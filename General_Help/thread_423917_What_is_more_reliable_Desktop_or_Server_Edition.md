---
title: "What is more reliable Desktop or Server Edition"
date: 2007-04-26
forum: General Help
---

### Post by nami on 2007-04-26
Hi

I am planning on setting up a computer which will be used for nothing but cctv recording.  i have the appropriate hardware and software i.e.

[http://www.zoneminder.com/](http://www.zoneminder.com/)

So I was wondering, would it be better for me to install ubuntu desktop or ubuntu server on this computer?

---

### Post by Zuph on 2007-04-26
There aren't many differences between server and desktop.  There are slight differences in some parts of the OS, but for your needs you wouldn't notice them.  The big difference is that the default Ubuntu server install is a lot more lean.  The server doesn't include much, except for Ubuntu's well known hardware support.  You'll be dumped to a lean command-line interface to do whatever you need.  You can install a desktop environment on top if you need a GUI (metapackage ubuntu-desktop), and whatever else you need.

If you want a leaner install, go for server edition, if you want an easy to use desktop, install desktop.

---

### Post by joft on 2007-04-26
AFAIK and IMO that does not matter. Desktop and Server editions are based on the same packages and have the same package repository. They differ in the pre-installed/automatically installed set of packages, e.g. the Server edition does not setup a graphical interface (Xorg) by default.
So this is not a question of reliability.

---

### Post by nami on 2007-04-26
Thanks for the replies.  I'll go for the desktop edition then, easier to use. :)

---

