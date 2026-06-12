---
title: "How to write commands when using tcplay? Tcplay a truecrypt alternative."
date: 2014-06-09
forum: General Help
---

### Post by ubto66 on 2014-06-09
Ubuntu 14.04 64bit


tcplay 1.1 installed using software center


I do not know how to use tcplay. I recon it is a command lineprogram.


If I write tcplay in terminal I get a list of commands. But what do I precisely write to


Search for truecrypt devices and files?


Mount and unmount truecrypt devices and files?


Also I would like to get detailed instructions on how to make a tc container and full hdd using
tcplay?


Tc containers and full hdds made using tcplay can be mounted using truecrypt 7.1a?


Thanks.

---

### Post by bapoumba on 2014-06-09
May be this will be of some help ?
[https://wiki.archlinux.org/index.php/Tcplay](https://wiki.archlinux.org/index.php/Tcplay)
There are links at the bottom of the page.

---

### Post by ubto66 on 2014-06-11
Thank you for answering.

I have read the links, and tried some of the commands. I am making it wrong and get error messages.

---

### Post by bapoumba on 2014-06-11
It will help others help you if you posted the commands you used and the error messages you got :)

---

### Post by ubto66 on 2014-06-12
I have truecrypt7.1a installed. I made a truecrypt test container named 'truetest' 2mb. I put files into it. The container is located in the home folder.

I used the link you stated. The instructions are for arch. Maybe that makes it no surprise, that they do not work.
Arch mount instructions are
# losetup /dev/loop0 foo.tc
 # tcplay -m foo.tc -d /dev/loop0
 # mount -o nosuid,uid=1000,gid=100 /dev/mapper/foo.tc /home/you/truecrypt/

If I write
losetup /dev/loop0 foo.tc
in terminal, I get
No such file or directory
If I write
tcplay losetup /dev/loop0 foo.tc
the tcplay commands
get listed.

---

### Post by bapoumba on 2014-06-12
I'm not quite sure why they would not work.
Here is the man page for ubuntu that looks quite similar to the one linked on the Arch wiki
[http://manpages.ubuntu.com/manpages/raring/man8/tcplay.8.html](http://manpages.ubuntu.com/manpages/raring/man8/tcplay.8.html)
[http://leaf.dragonflybsd.org/cgi/web-man?command=tcplay&section=8](http://leaf.dragonflybsd.org/cgi/web-man?command=tcplay&section=8)

---

### Post by sudodus on 2014-06-12
Do you run with superuser privileges (sudo before the commands)?

---

### Post by ubto66 on 2014-06-12
Thank you.
The link
[http://manpages.ubuntu.com/manpages/.../tcplay.8.html]("http://manpages.ubuntu.com/manpages/raring/man8/tcplay.8.html")
showing the examples and 'sudo' made a difference.

The name of the truecrypt container is truetest
I wrote
sudo losetup /dev/loop1 truetest
then
sudo tcplay --map=truetest --device=/dev/loop1
got
Passphrase:
I entered the passphrase
got
All ok!
Truetest container is mounted and files are available.

To unmount write
umount /dev/mapper/truetest

I write
sudo dmsetup remove truetest
to unmap.

If I want to mount truetest again and I write 
sudo losetup /dev/loop1 truetest
I get this error message
losetup: /dev/loop1: device is busy
Why does it say that?

If I instead write
sudo tcplay --map=truetest --device=/dev/loop1
I can mount again.
And then unmount, unmap.

---

### Post by sudodus on 2014-06-12
I have never used truecrypt. I'm glad I could help at the basic level, but now I think you need help from someone who knows truecrypt. Also, if you backup your system, you need not be afraid of trial and error.

Let us hope someone who knows will chip in and continue helping.

Good luck :-)

---

