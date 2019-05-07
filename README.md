$ sudo systemctl unmask docker.service
$ sudo systemctl unmask docker.socket
$ sudo systemctl start docker.service
$ sudo systemctl enable docker
$ docker --version

$ touch index.html
$ nano index.html

<!DOCTYPE html>
<html>
        <body>
                <h1> HelloWorld..! I am running inside a Docker Container  </h1>

        </body>
</html>

$ touch Dockerfile
$ nano Dockerfile

FROM ubuntu:19.04
RUN apt update -y
RUN apt upgrade -y
RUN apt dist-upgrade -y
RUN apt autoclean -y
RUN apt autoremove -y
RUN apt install -y apache2
RUN chown -R www-data:www-data /var/www
ENV APACHE_RUN_USER www-data
ENV APACHE_RUN_GROUP www-data
ENV APACHE_LOG_DIR /var/log/apache2
ENV APACHE_LOCK_DIR /var/lock/apache2
ENV APACHE_PID_FILE /var/run/apache2.pid
ADD index.html /var/www/html
EXPOSE 80
ENTRYPOINT ["/usr/sbin/apache2ctl"]
CMD ["-D","FOREGROUND"]

$ docker images
