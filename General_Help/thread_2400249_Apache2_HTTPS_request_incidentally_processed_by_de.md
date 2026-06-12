---
title: "Apache2 HTTPS request incidentally processed by default HTTP site. 400 Bad Request"
date: 2018-09-04
forum: General Help
---

### Post by jakusb on 2018-09-04
I am facing inconsistent behaviour when trying to make the same request https.
Most of requests are handled properly by the related Virtual Host definition.
Some are handled by my default HTTP Virtual Host definition... I cannot figure out why?


The log from apache clearly shows the request on port 443 is handled by the default site configured for port 80.
tshark confirmes this

See attached logs

---

### Post by sporksrule on 2018-09-04
I'm sorry to ask, but did you have both non-ssl and ssl apache2 config files set up and enabled? Along with a valid ssl certificate? If not the default page will be served.

---

