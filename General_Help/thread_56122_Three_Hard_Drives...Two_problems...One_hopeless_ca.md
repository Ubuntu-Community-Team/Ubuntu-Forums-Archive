---
title: "Three Hard Drives...Two problems...One hopeless case."
date: 2005-08-11
forum: General Help
---

### Post by Fwyxx on 2005-08-11
I have two problems.  One is immense, and the other is trivial.  However, as I have nowhere else to ask for help, here I am.   ](*,)   

First of all, the immense problem: I have three Hard Drives, am currently running Windows XP Media Center off of one of them, and am using the other two for extra storage.  Why would I need two 250 GB Hard Drives to supplement another one?  The Hard Drive with Windows on it has mere megabytes of space left on it.  I have made the decision to give Ubuntu Linux a shot.  If I like it in LiveCD form, I might even consider trying to install it permanently.  However, I also require Windows to be running on my machine for games and other apps that I consider vital.  How would I go about installing Ubuntu on one of my 250 GB Hard Drives without losing Windows?

Next, the smaller problem: Debian has an immense software library.  Since Ubuntu is Debian based, can I download programs from that Library and install tem in Ubuntu?

While I'm at it, I thought of another problem: My house has several computers on a Wireless network.  My computer (the one I want Ubuntu on) is not the one running the network.  is Ubuntu compatible with my Linksys wireless card?  Is Ubuntu compatible with my Linksys wireless connection?  How would I go about setting that up?

Confused, Disoriented, and Signing off,

Fwyxx

---

### Post by mo_x on 2005-08-11
More questions than problems I suppose.

The installer will let you choose where to install Ubuntu. Use a different drive from the one you installed Windows on. The installer will most likely detect Windows and you will be able to boot into both.

You can install Debian packages. There are also a lot of packages available for Ubuntu.

---

### Post by jasmuz on 2005-08-11
For you to install in one of those 250 gb drives you will have to resize its partition table in order to make space for the Ext3 Filesystem Ubuntu uses, and for a swap partition also. When doing the installation it will prompt you (expert mode) where to place your Ubuntu install, you must specify the disk to wich you made the space in. Grub will do the rest of adding the windows system to its table so you can boot up.

Yes, debian does have a great software database, you could try to use some software, but i would recommend our software wich is growing exponentially. 

[https://wiki.ubuntu.com/WindowsDualBootHowTo](https://wiki.ubuntu.com/WindowsDualBootHowTo)

---

### Post by Fwyxx on 2005-08-11
Thanks.  I'll give it a shot.  And I suppose there *were*  more questions than problems.  However, thanks to the available support, I have a felling that the install should go smoothly.  There is still the matter of the wireless, though.  Well, with any luck at all, no problems should occur.


Thanks again,

Fwyxx

---

### Post by wrtrdood on 2005-08-11
[QUOTE=Fwyxx]There is still the matter of the wireless, though.[/QUOTE]


Have a look at [http://linux-wless.passys.nl](http://linux-wless.passys.nl)

Linksys has had a fairly decent Linux record in the wireless arena so you'll probably be Ok.

---

