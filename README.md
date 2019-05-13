9 May 2019, Yeong Zhi Wei

After managing to get Docker up and running on Azure VM yesterday, I gained such a huge confidence that now I tried to get a real-world open source app up and running. The app is Wallabag and is similar in nature to Pocket where I can save the articles and read it later. Being open source has its plus, first I could host it on my server. Awesome. Second, it comes full featured with full text search whereas had I used Pocket, I would have to pay monthly subscriptions to unlock the full features. Woohoo.

## Change logs
| Date | Description |
| --- | --- |
| 9 May 2019 | https using **Traefik** as reverse proxy and **Let's Encrypt** for free TLS certificate |
| 7 May 2019 | First version |

Reference
- https://www.wallabag.org/en
- https://hub.docker.com/r/wallabag/wallabag
- https://hub.docker.com/_/postgres
- https://docs.microsoft.com/en-us/azure/virtual-machines/windows/portal-create-fqdn
- https://github.com/wallabag/docker/issues/77
- https://docs.traefik.io/user-guide/docker-and-lets-encrypt/

---

## Create configuration files

Create a [docker-compose.yml](docker-compose.yml) file.
> Replace `<postgres-user>`, `<postgres-password>`, `<database-password>` and `my.domain.com`

    $ touch docker-compose.yml
    $ vi docker-compose.yml # copy over

Create a [traefik.toml](traefik.toml) file to configure traefik.
> Replace `<email-address>`

    $ touch traefik.toml
    $ vi traefik.toml # copy over

Create an empty acme.json file for storing SSH credentials.

    $ touch acme.json
    $ chmod 600 acme.json

## Set up Docker & Docker Compose

Create a `web` network.

    $ docker network create web

Run the containers.

    $ sudo docker-compose up -d

## Check it out

Go to `https://my.domain.com` and login
- user: wallabag
- password: wallabag

Change the password.