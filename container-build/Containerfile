# Use the httpd-parent image as base
#FROM quay.io/redhattraining/httpd-parent

FROM registry.access.redhat.com/ubi8/ubi:8.0

LABEL value="1.0" description="Application for container optimize" maintainer="Red Hat Training <training@redhat.com>"

# DocumentRoot for Apache

#ENV DOCROOT=/var/www/html 

RUN   yum install -y --disableplugin=subscription-manager httpd && \
      yum clean all --disableplugin=subscription-manager -y && \
      echo "Hello from the httpd-parent container!" > /var/www/html/index.html
      #echo "Hello from the httpd-parent container!" > ${DOCROOT}/index.html

# Allows child images
EXPOSE 80

ONBUILD COPY ./src/ /var/www/html
# This stuff is needed to ensure a clean start
RUN rm -rf /run/httpd && \
    mkdir /run/httpd
# Run as the rroot user
 USER root 
# Launch httpd
 CMD /usr/sbin/httpd -DFOREGROUND
