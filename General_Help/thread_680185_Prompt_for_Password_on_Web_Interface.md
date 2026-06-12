---
title: "Prompt for Password on Web Interface?"
date: 2008-01-27
forum: General Help
---

### Post by i.wanna.corndog on 2008-01-27
Hey everyone,

I'm attempting to set up a web interface for my network scanner. One question: how do I go about prompting to have the user login as root (or another user) over the web interface to run a scan without permissions problems? For instance, I use SWAT, and when I go to that page, it prompts me to login via a popup password dialog. I keep having permissions problems, and this is only for use on a private network, so security isn't a big issue.

EDIT: Something else that I just thought of that might work is simply letting any user run the scan binaries as root. Would I do this through visudo (a.k.a. sudoers)?

Thanks!
Dan

EDIT: Solved my problem by setting user "www-data" to require no password in sudoers.

---

### Post by gvartser on 2008-01-28
To setup web authentication on a web server pages take a look at ".htpasswd"

[http://httpd.apache.org/docs/2.0/programs/htpasswd.html](http://httpd.apache.org/docs/2.0/programs/htpasswd.html)

/g

---

