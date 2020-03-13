# MaintenancePage

###Simple to install and use

1. `cd /var/www`
2. `git clone https://github.com/pashcovich/maintenance_page`

I use this simple configuration for `nginx` on my servers:
```bash
# Default server configuration
#
server {
        listen 80 default_server;
        listen [::]:80 default_server;

        # listen 443 ssl default_server;
        # listen [::]:443 ssl default_server;

        root /var/www/maintenance_page;

        error_page 403 = /403.html;
        error_page 404 = /404.html;

        error_page 500 502 503 504 /50x.html;

        index index.html;

        server_name _;

        location / {
                # First attempt to serve request as file, then
                # as directory, then fall back to displaying a 404.
                try_files $uri $uri/ =404;
        }
}
```
