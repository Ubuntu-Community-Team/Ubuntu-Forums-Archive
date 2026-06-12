---
title: "Detecting Revoked SSL Certificate"
date: 2008-06-13
forum: General Help
---

### Post by dslehman on 2008-06-13
I am presently using the application ssl-cert-check ([http://prefetch.net/articles/checkcertificate.html](http://prefetch.net/articles/checkcertificate.html)) to detect if any of my Apache SSL certificates are expired. I have it set up as a cron job to check the SSL certificates on a list of web sites.

This script will only let me know if if my certificate is expired. I am now looking for a script that will take in a list of web sites and inform me if any of their SSL certificates have been revoked. Newer browsers (Firefox 3.x and IE 7.x) check web site SSL certificates to see whether or not they have been revoked before it starts to load the site. 

I work in a large organization where someone else manages the SSL certificates that I use. They have accidentally revoked some of my certificates in the past and have caused issues with users who have newer browsers. Hence, proactively checking my SSL certificates to see if they have been revoked is important to me. 

Please let me know if you know of a way to do this.

Thanks very much!

---

### Post by dslehman on 2009-03-12
Anyone? Pleases :(

---

### Post by Neo_The_User on 2009-03-12
I don't know the answer. I don't use SSL AFAIK.

---

