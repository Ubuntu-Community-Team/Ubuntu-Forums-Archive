---
title: "Mounting usb cdrom"
date: 2005-10-29
forum: General Help
---

### Post by _kresten on 2005-10-29
Hi!
I'm having problems mounting my usb cdrom. It worked like a charm under Horay, and I've installed Breezy from that same drive. It shows up under "Places" => "Machine" next to "Filesystem" as "Cd-rom 1". But when I clik it it shows this error message:
[INDENT]mount: special device /dev/scd0 does not exist[/INDENT]
I'm not sure what else to post (because I'm not an experienced Linux user). So please tell me and I will...

The drive is an LG "external super multi dvd rewriter" model "GSA-5163D" and the computer is an IBM T40.

I'd greatly appreciate any help!

---

### Post by darknuala on 2005-11-16
Look at your etc/fstab, and it should tell you what it is called there.

---

### Post by taurus on 2005-11-16
Or look at your kernel message to see what device it is on,

dmesg | more 
(hit space key for next screen...)

---

### Post by _kresten on 2005-11-16
Well I tried getting help at ubuntu's IRC channel. And they asked me the same (that is to show them my dmesg and fstab). It didn't make any sense to anyone in there!?! 
But all of a sudden it just seems to work.:o  Why, I don't know... The last couple of times I've booted it worked fine.

Well, guess thats just how these machines works. 

Thanks for your reply anyway, though!

---

### Post by kruz on 2005-11-16
its because ubuntu reconized it, and now automounts it

---

### Post by _kresten on 2005-11-16
Just strange that it took 30 reboots before it reconized the drive, right?:???:

---

