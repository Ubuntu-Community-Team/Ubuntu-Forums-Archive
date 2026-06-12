---
title: "Firefox slow (62sec) to start."
date: 2007-07-03
forum: General Help
---

### Post by schuelaw on 2007-07-03
I'm installing Feisty on one of my lab machines in the hopes of migrating the whole lot from Centos 4.5.  So far, so good.  However, firefox takes about 60 seconds to start.  

The machine is a Dell GX280.  The feisty install is pretty typical and fully updated.  I've read about slow startup for gnome apps, but those seem to be starting just fine.  It's quite repeatable and the fact that it reliably takes about a minute suggests some kind of time out.  I have flash, java, and adobe's pdf plugins among other things.  They all seem to work once the browser appears.  All activity after the slow start appears to be normal and responsive.  Any tips or advice on places to look?

Albert

---

### Post by Cool Surfer on 2007-07-03
Try to toggle the choice from in the address bar - 

about:config

then

ipv

set bollean to truth true.

---

### Post by schuelaw on 2007-07-03
If you mean the ipv6 option in about:config, I tried that to no effect.  I also disabled ipv6 in /etc/modprobe.d/aliases, but thanks for the try.

---

### Post by schuelaw on 2007-07-03
My next step is to work my way through the firefox start up shell script and see where the hang up is, but I'm at home right now and can't work on it.  The really puzzling thing is that I run feisty in my office with no problems.  I also run it at home on 4 laptops and another desktop, no problem.  It makes me think that there's something unusual about the lab set up.  The major differences between the lab computer and my own is that it uses kerberos for user authentication and automount to mount user home directories from our file server.  That said, both of those services are working on the machine in question.

---

### Post by hikaricore on 2007-07-03
I bet you anything some of your Firefox addons are causing the slow launch.
I know on my home desktop, flashblock causes FF to take nearly 15 seconds longer to start.

Have you tried launching from a terminal?  Check for message output there.

---

### Post by schuelaw on 2007-07-03
Nice thought, but I tried /usr/bin/firefox from the terminal.  There are no messages.  The three add-ons are "Adblock plus", "Bookmark Sync and Sort", and "Download status bar".  I use these everywhere and this is the only machine I have problems with.

---

### Post by stchman on 2007-07-03
> **schuelaw said:**
> I'm installing Feisty on one of my lab machines in the hopes of migrating the whole lot from Centos 4.5.  So far, so good.  However, firefox takes about 60 seconds to start.  

The machine is a Dell GX280.  The feisty install is pretty typical and fully updated.  I've read about slow startup for gnome apps, but those seem to be starting just fine.  It's quite repeatable and the fact that it reliably takes about a minute suggests some kind of time out.  I have flash, java, and adobe's pdf plugins among other things.  They all seem to work once the browser appears.  All activity after the slow start appears to be normal and responsive.  Any tips or advice on places to look?

Albert

A while back I was having problems with slow load and slow internet.  This worked for me:

[http://www.stchman.com/conf_host.html](http://www.stchman.com/conf_host.html)

Hope it helps.

---

### Post by schuelaw on 2007-07-03
Thanks.  I tried that with no luck.

---

