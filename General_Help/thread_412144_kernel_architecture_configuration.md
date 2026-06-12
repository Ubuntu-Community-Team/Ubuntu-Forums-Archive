---
title: "kernel architecture configuration"
date: 2007-04-17
forum: General Help
---

### Post by Bobtheknight on 2007-04-17
My betters,

I think my computer is using a generic kernel image.  "linux-headers-2.6.20-14-generic"

I wish to use my architecture, p4.  Is there a way to do it without compiling a kernel myself?

Thanks a lot!

---

### Post by HiSPEC on 2007-04-17
Hey,
try running:
apt-cache search kernel | grep -i kernel | grep 686

and search for an appropriate kernel.

---

### Post by Bobtheknight on 2007-04-17
I did the command, nothing happened.

Is something supposed to output afterwards?

Seeing it's a grep command I'm assuming nothing means not found.

---

### Post by igknighted on 2007-04-17
You could just try looking at all the kernel packages in synaptic to try to find the one you want.  Otherwise, download the kernel source and have at it :).  It sounds rather scary, but as long as you have the time to let your computer hammer away, it is really easy.  Somewhere there is a guide on these forums to configuring and installing a 2.6.20 kernel from source, I would recommend you check that out.  There really isn't much risk, if it doesn't work you boot your old kernel and the worst thing that happened is you lost some time out of your life.  And when you succeed it is a great feeling, and you will definitely notice the difference when using your system.

Here's the how-to:
[http://ubuntuforums.org/showthread.php?t=311158&highlight=master+kernel+compile](http://ubuntuforums.org/showthread.php?t=311158&highlight=master+kernel+compile)

---

### Post by Bobtheknight on 2007-04-18
Okay, I understand.  So there is no way to "convert" a generic compilation to a "i386" one.  I either have to download an i380 from repository or compile my own i386.  I can still get updates and everything even tho I use a customized kernel right?

---

