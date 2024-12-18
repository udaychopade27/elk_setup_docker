FROM docker.elastic.co/beats/auditbeat:8.13.0

# Install GLIBC 2.34
RUN apt-get update && apt-get install -y wget \
    && wget http://ftp.gnu.org/gnu/libc/glibc-2.34.tar.gz \
    && tar -xvzf glibc-2.34.tar.gz && cd glibc-2.34 \
    && mkdir build && cd build \
    && ../configure --prefix=/opt/glibc-2.34 && make -j$(nproc) && make install \
    && rm -rf /glibc-2.34*

# Set GLIBC path
ENV LD_LIBRARY_PATH=/opt/glibc-2.34/lib:$LD_LIBRARY_PATH
CMD ["auditbeat", "-e"]
