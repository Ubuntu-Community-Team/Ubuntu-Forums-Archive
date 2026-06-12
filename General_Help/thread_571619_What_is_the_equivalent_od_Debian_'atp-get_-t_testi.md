---
title: "What is the equivalent od Debian 'atp-get -t testing'"
date: 2007-10-09
forum: General Help
---

### Post by kkruecke on 2007-10-09
I want to get the latest version of the web server lighttpd. On Debian, I could do this by issuing **apt-get -t testing <package name>**
I just first had to add   ```
deb http://ftp.us.debian.org/debian testing  main contrib non-free 
``` to **/etc/apt/sources.list**, and put ```
APT::Default-Release "stable";
``` in **/etc/apt/apt.conf**. Then after **apt-get update**, do **apt-get -t testing <package name>**

What is the equivalent way of doing this on Ubuntu? I need to do this from a command line SSH session.

---

### Post by kzutter on 2007-10-09
Ubuntu has a different development cycle and philosophy from Debian.

Read
[https://wiki.ubuntu.com/UbuntuDevelopment]("https://wiki.ubuntu.com/UbuntuDevelopment")

and
[http://people.debian.org/~mbanck/texts/ubuntu_development_model.html]("http://people.debian.org/~mbanck/texts/ubuntu_development_model.html")

neither of which will solve your problem, but will answer why you have to think about these things differently. 

-Ken

[BTW- Gutsy has lighttpd 1.4.18]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=lighttpd&searchon=names&subword=1&version=all&release=all")

---

### Post by kkruecke on 2007-10-09
Thanks. I'll check out those links pronto.

---

