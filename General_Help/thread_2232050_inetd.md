---
title: "inetd"
date: 2014-06-29
forum: General Help
---

### Post by prc320 on 2014-06-29
Hi

Where is inetd.conf?

prc320

---

### Post by gordintoronto on 2014-06-29
My system has no such file. What package is it part of?

It never hurts to mention what version of Ubuntu you are using, and it might be very relevant is this case.

For a file which has been around for a while, you can use the command: locate inetd.conf

---

### Post by HermanAB on 2014-06-30
Deprecated

---

### Post by SeijiSensei on 2014-06-30
Install [xinetd]("http://bose.utmb.edu/Compu_Center/xinetd_faq.html") instead with "sudo apt-get install xinetd".  Inetd has been deprecated on nearly every distribution for many years now.

---

### Post by prc320 on 2014-07-29
Thanks guys, reading an old book.

---

### Post by ian-weisser on 2014-07-29
Indeed, xinetd is superfluous these days.
The functionality of xinetd has been taken on by Upstart and systemd.

In other words, let's say you want to run an application (or just a script) upon connection to port 9999.

The *really old* way was to install inetd and create an inetd.conf entry.

The *old* way was to install xinted and create an xinted conf file for the service. xinetd is still in the Ubuntu repositories.

The *current* way is to install nothing (Upstart is already part of Ubuntu), and create an Upstart job that uses the socket bridge. See [http://upstart.ubuntu.com/cookbook/](http://upstart.ubuntu.com/cookbook/) for detailed instructions.

The *future* way is to install nothing (systemd will replace Upstart in a future release of Ubuntu) and create a systemd job that uses the socket bridge.

---

