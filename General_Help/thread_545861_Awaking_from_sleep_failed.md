---
title: "Awaking from sleep failed"
date: 2007-09-08
forum: General Help
---

### Post by Robbyx on 2007-09-08
Because my room does not need heating by my desktop I decided to switch on the sleep mode after 30mins inactivity. I was very pleased with this yesterday. It worked a number of times  well and quickly (in fiesty).

Over night it went to sleep again, but his time would not wake up properly.I pushed the space bar. The machine work up but did not load the system. I gave up when loading cups printer daemon stayed on the screen for a very long time. I did a hard rebote and am back into Ubuntu. As I have nvidia drivers I suspect that I should install suspend2, but it looks daunting and I do not want to mess up my system or my head. So for the moment I have disabled sleep mode. Is this an issue that has been resolved without recompiling the kernel with siuspend2?  

Robin

---

### Post by kev000 on 2007-09-08
setting up suspend2 is easy.  You can get a feisty one from trevino's repo that works really well.  All you need to do after installation is add a line to your grub/menu.lst.

[http://3v1n0.tuxfamily.org/dists/feisty/suspend2/](http://3v1n0.tuxfamily.org/dists/feisty/suspend2/)

Alternatively you can just install the hibernate scripts and hack around with those since they seem to help suspend2ram also.

good luck.

---

### Post by Arwen on 2007-09-08
Thanx a lot kev000,I really thought I screwed everything when I used suspended and my pc wouldn't wake up unless I rebooted,I have nvidia card too, so that's the explanation!

---

### Post by Robbyx on 2007-09-08
After adding the following to the software sources:

 deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty suspend2
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty suspend2

the following error message appeared 

W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D6CFB44DD800CD9

The error is part of the results of a sudo apt-get update

This surprises me because I ran the following line in terminal:

wget [http://download.tuxfamily.org/3v1deb/DD800CD9.gpg](http://download.tuxfamily.org/3v1deb/DD800CD9.gpg) -O- | sudo apt-key add -

Do you know why the error message arose? Do I need to worry about it?

is there a way for me to  I tell if the patch installed? I presume the application installed somewhere but I do not know where it is.

---

