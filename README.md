# Winecraft's Nginx Server
In order to host my multiple websites, I have this basic docker compose environment with
a service running for each of my websites. These services are reverse proxied using nginx
which takes care of SSL termination.

## Setup
We have to setup the certs first. Make sure the only file sitting in `./nginx-conf` is `ssl_setup.conf`.
Let's use the following commands:

    docker compose run --rm certbot certonly --webroot --webroot-path /var/www/certbot -d jellothompson.com
    docker compose run --rm certbot certonly --webroot --webroot-path /var/www/certbot -d winecraft.dev

Once these two steps pass, we can swap `ssl_setup.conf` with `working.conf`.
