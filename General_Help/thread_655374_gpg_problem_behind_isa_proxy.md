---
title: "gpg problem behind isa proxy"
date: 2008-01-01
forum: General Help
---

### Post by spinnekoppeke on 2008-01-01
Hi,

I try to acesss gpg-hkp-server --keyserver hkp://subkeys.pgp.net through a isa proxy server. somewhere else i have another ubuntu host, with same configuration, but not behind proxy server, where gpg works perfect. I use ntlmaps which points to the isa proxy-server : surfing, apt-get, wget , ... works. The proxy ([http://localhost:5865](http://localhost:5865) points to the real proxy server)

sudo gpg gpg --keyserver hkp://subkeys.pgp.net --recv 371A69E3AE3BE9AA
sudo gpg --keyserver-options http_proxy --keyserver hkp://subkeys.pgp.net --recv 371A69E3AE3BE9AA
sudo gpg --keyserver-options http_proxy,honor-http-proxy,broken-http-proxy --keyserver hkp://subkeys.pgp.net --recv 371A69E3AE3BE9AA

I always get this error  :

gpg: requesting key AE3BE9AA from hkp server subkeys.pgp.net
gpgkeys: key 371A69E3AE3BE9AA not found on keyserver
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

Anybody has an idea ?

Greetz,
Johan

---

