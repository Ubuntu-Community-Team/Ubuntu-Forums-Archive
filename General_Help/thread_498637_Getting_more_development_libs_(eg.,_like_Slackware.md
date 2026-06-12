---
title: "Getting more development libs (eg., like Slackware)?"
date: 2007-07-11
forum: General Help
---

### Post by djtopper on 2007-07-11
I've been maintaining a Slackware shop for about 10 years.  I'm considering Ubuntu and have it now installed on my laptop.  It's nice to have so many things working out of the box.  But when I go to compile some of my projects and code, I'm finding SO MANY libraries not installed (eg., perl, python, audio libs, etc...).  I'm finding it very difficult to get work done and the time I'm spending downloading all these libs I could have just spend using Slackware.

So my questions are:

1.  Is there a "dev" snapshot of packages I can install, rather than poking around the Synaptic downloader?

2.  Once I finally manage to install the dozens of libraries I need, how can I find out which ones I've added, so I can automate this task on the other machines in my lab?

Thanks,

DT

---

### Post by Joseph1337 on 2007-07-11
Did you try sudo apt-get install build-essential and sudo apt-get install sbuild?

---

### Post by southernman on 2007-07-11
> **Joseph1337 said:**
> Did you try sudo apt-get install build-essential and sudo apt-get install sbuild?

These are fine, but you still need the dependent libs to do a task at hand.

---

### Post by djtopper on 2007-07-12
Thanks ... but I can't seem to do:

sudo apt-get install sbuild
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sbuild

Thanks,

DT

---

