# Svelte PWA with Traefik

This is an extension to the Svelte-PWA template at https://github.com/tretapey/svelte-pwa.
It features a simple setup with [Traefik](https://traefik.io/) using docker-compose that allows easy self-hosting webpages using [DuckDNS](https://www.duckdns.org/). It features redirection from HTTP to HTTPS, and ACME DNS challenge using [LetsEncrypt](https://letsencrypt.org/).

To create a new project base on this template using [degit](https://github.com/Rich-Harris/degit):

```bash
npx degit pedroallenrevez/svelte-pwa-traefik my-svelte-pwa-traefik
cd my-svelte-pwa-traefik
```

*Note that you will need to have [Node.js](https://nodejs.org) installed.*

## Get started

Install the dependencies...

```bash
cd my-svelte-pwa-traefik/app
npm install
```

...then start [Rollup](https://rollupjs.org):

```bash
npm run dev
```

Navigate to [localhost:5000](http://localhost:5000). You should see your app running. Edit a component file in `src`, save it, and reload the page to see your changes.

By default, the server will only respond to requests from localhost. To allow connections from other computers, edit the `sirv` commands in package.json to include the option `--host 0.0.0.0`.

## Building and running in production mode

Replace your credentials in following places:
1. `DUCKDNS_TOKEN` - `docker-compose.yml` - replace with the token provided by DuckDNS
2. Email - `config/traefik.yml` - the email provided to DuckDNS.
3. Webpage names - in `config/traefik.yml` and `config/dynamic_conf.yml`

Refer to https://doc.traefik.io/traefik documentation for more information on the configuration.


To create a containerized version of the app:

```bash
docker-compose build
docker-compose up
```

*Note that you will need to port-forward ports 80 and 443 to the machine that is hosting the webpage.*
