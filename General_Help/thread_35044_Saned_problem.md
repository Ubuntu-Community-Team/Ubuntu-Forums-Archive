---
title: "Saned problem"
date: 2005-05-17
forum: General Help
---

### Post by Snocrash on 2005-05-17
Hi all,

I seem to have some sort of a problem with saned. I have a umax scsi scanner attached to my server and I usually share it out over the network with saned. This worked fine with Redhat, Fedora and Slackware.

I changed my server over to Ubuntu this weekend because I was already running it on my Desktop and laptop. Everything worked fine except saned. XSane works fine on the server and I can scan on that box. I modified inetd.conf and services as suggested in the saned man page. Set up the saned.conf and dll.conf as needed. But saned does not seem to be starting so I can't reach the scanner from my desktop. If I manually start saned with the -d option, it will start and let me access the scanner from my desktop, but it complains about sane-port being unknown and port 6566 already being in use.

Any clues????

Thanks,

-Sno

---

### Post by Snocrash on 2005-05-18
Just moving it up the list  :)

---

### Post by Lupine on 2005-09-16
Hmmm, just tried this on my scanner and I'm seeing the same thing.  Every find a solution?

---

### Post by zalun on 2005-10-05
I rode somewhere about changing port name other than sane-port
Otherways: Does the sane port have the same name in /etc/services?

---

### Post by dare2dreamer on 2005-12-22
I ran into a similar problem here, and found a solution.

It seems that the default ownership of the scanner (/dev/sg0 in my case) was root:scanner as opposed to being in the saned group. I simply changed my /etc/inetd.conf to read as follows:

sane stream tcp nowait saned.scanner /usr/sbin/saned saned

Note that all the documentation recommends you set user.group to saned.saned instead.

Anyway, the change gave saned access to the scanner device and everything "just worked".

You could probably mess with devfs to change the permissions on /dev/sg0, or possibly just add saned to the scanner group, but this seemed the most elegant solution to me.

Hope it helps.

---

