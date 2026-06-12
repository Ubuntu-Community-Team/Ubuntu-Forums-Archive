---
title: "is capath for certificates for curl and wget broken"
date: 2019-04-25
forum: General Help
---

### Post by patle2 on 2019-04-25
It seems certificates are in part broken in 19.04, or am I doing something wrong?

Sitting behind a proxy with a self signed certificate, I have done the usual efforts to install the local certificate into /etc/ssl/certs/ca-certificates.crt

Testing this with **curl --cacert /etc/ssl/certs/ca-certificates.crt https://www.ubuntu.com** works as expected,

However **curl https://www.ubuntu.com** and **curl --capath /etc/ssl/certs/ https://www.ubuntu.com** gets me "curl: (60) SSL certificate problem: unable to get local issuer certificate" response. I've also attempted --proxy-capath.

Since --cacert is working, this seems to confirm that the certificates is correct, and that there is a bug.

wget shows similar behavior. firefox with certificates installed works. I'm running kubuntu, and I've also installed certificates using System Settings.

Is this a bug, or am I missing something?

---

