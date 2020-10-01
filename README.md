# BARTOC.org

> Relaunch of BARTOC.org web interface

This repository contains the new web interface of BARTOC.org, run at [VZG](https://www.gbv.de/).

*See <https://info.gbv.de/display/DiB/BARTOC-Import> for additional information (internally only)*

## Functional Requirements

* Keep all BARTOC URIs and most URLs
* Provide a nice web interface, possibly multilingual
* Use JSKOS API (in particular DANTE) as backend
* Serve HTML, JSKOS, and RDF

## Install

## Requirements

Requires at least Node.js 10 and an instance of [jskos-server](https://github.com/gbv/jskos-server) to connect to. Additional dependencies are listed in `package.json`.

## Install from sources

~~~sh
git clone https://github.com/gbv/bartoc.org.git
cd bartoc.org
npm install
~~~

Optionally transform the Drupal export to JSKOS format (requires Perl >= 5.14 without additional modules):

~~~
npm run cache
~~~

Then import the resulting file `cache/vocabularies.ndjson` into your jskos-server instance.

## Configuration

Basic configuration is located in `config/config.default.json`. Selected fields can be overridden in a local `config/config.json`. The latter should at least include a link to a JSKOS server instance, e.g.:

~~~json
{
  "backend": {
    "provider": "ConceptApi",
    "api": "http://localhost:3000/"
  }
}
~~~

## Run for testing

~~~sh
npm run start
~~~

The application is made available at <http://localhost:8338/>.

## Deployment

The application is temporarily deployed at <http://bartoc.gbv.de/> and will be made available at <http://bartoc.org/> with the relaunch.

Update an existing installation:

~~~sh
git pull
npm install
pm2 restart bartoc.org
~~~
