---
title: "will ubuntu run on this hardware?"
date: 2005-11-01
forum: General Help
---

### Post by krikke on 2005-11-01
Hello,

I have a pentium 1 133mhz, 32MB memory with 2Gigabyte Harddisk next to me, and I want to make it a printserver, is it possible to run ubuntu linux on this old machine?

---

### Post by Kyral on 2005-11-01
Very, very, _***very***_ slimmed down. I'd just throw the minimal "server" install on it

---

### Post by majikstreet on 2005-11-01
Yes, no X.org/Gnome is needed for a printserver :)

---

### Post by Kyral on 2005-11-01
He might be able to get Fluxbox running on it if he really needed a GUI for something ;P

---

### Post by felix_stegerman on 2005-11-01
For servers I'd recommend Debian.

Especially in this case, since Debian's CUPS can be configured w/ the
web interface, unlike Ubuntu's. So you won't need X / Gnome.


Felix

---

### Post by Kyral on 2005-11-01
Yah I'd actually go with Debian on this one. You *can* use Ubuntu as a server, but if its going to be like a high end professional application, use something like RHEL, SuSE Enterprise, or CentOS

---

### Post by jonzep on 2005-11-01
amazingly ubuntu will run on your setup... i guess there really is a good argument for the i386 kernel being defaut after all...

---

### Post by az on 2005-11-01
[QUOTE=krikke]Hello,

I have a pentium 1 133mhz, 32MB memory with 2Gigabyte Harddisk next to me, and I want to make it a printserver, is it possible to run ubuntu linux on this old machine?[/QUOTE]
Hoary may fail the installation because of the low memory.  Although it will probably work.  Breezy says it needs 128 megs of ram for the installer on the boot page.

---

### Post by Kyral on 2005-11-01
Actually.....Damn Small Linux anyone?

---

### Post by SickTwist on 2005-11-01
If you do decide to try Ubuntu, there is a special server edition that comes with more server-oriented packages on the CD:

I grabbed the following info from [this]("http://lwn.net/Articles/156309/") article:
[INDENT][I]To Get Ubuntu 5.10 Server
-------------------------

Download Ubuntu 5.10 here (choose the mirror closest to you):

  Europe:
    [http://se.releases.ubuntu.com/ubuntu-server/5.10/](http://se.releases.ubuntu.com/ubuntu-server/5.10/)

  United Kingdom:
    [http://releases.ubuntu.com/releases/ubuntu-server/5.10/](http://releases.ubuntu.com/releases/ubuntu-server/5.10/)

  Rest of the World:
    [http://releases.ubuntu.com/releases/ubuntu-server/5.10/](http://releases.ubuntu.com/releases/ubuntu-server/5.10/)

Please download using Bittorrent if possible.[/I][/INDENT]

---

### Post by Irysche on 2008-03-09
I have an old Toshiba laptop with an AMD 333 MHz processor and 128 MB of RAM and a 4 GB HDD.

In reading the minimum suggested requirements I found that ubuntu will run, but it might not run well.  I just need this for my son to use to surf the net.  Not going to be anything big run on it, just a simple desktop machine.

It's running windows 98 right now and I can't get alot of the new flash stuff to run on it because most of it is not compatible with IE 5.5 or 6.0.  I can get some if it to work in Firefox 2, but I'd just as soon get a more advanced and stable OS on the hardware if I can.  Oh, I also have an old 10BaseT PCMCIA card that last time I was looking for drivers I had to get them from Russia.

I'm okay with purchasing a bigger HDD and a different NIC, but don't want to put the effort in if I don't have to.

Last thing, hopefully not a tall order, it needs to be easy to install.  I've only done a RedHat install and that was like 4 years ago.

Any suggestions would be appriciated.

---

### Post by Oldsoldier2003 on 2008-03-09
> **Irysche said:**
> I have an old Toshiba laptop with an AMD 333 MHz processor and 128 MB of RAM and a 4 GB HDD.

In reading the minimum suggested requirements I found that ubuntu will run, but it might not run well.  I just need this for my son to use to surf the net.  Not going to be anything big run on it, just a simple desktop machine.

It's running windows 98 right now and I can't get alot of the new flash stuff to run on it because most of it is not compatible with IE 5.5 or 6.0.  I can get some if it to work in Firefox 2, but I'd just as soon get a more advanced and stable OS on the hardware if I can.  Oh, I also have an old 10BaseT PCMCIA card that last time I was looking for drivers I had to get them from Russia.

I'm okay with purchasing a bigger HDD and a different NIC, but don't want to put the effort in if I don't have to.

Last thing, hopefully not a tall order, it needs to be easy to install.  I've only done a RedHat install and that was like 4 years ago.

Any suggestions would be appriciated.

maybe run Xubuntu, Icebuntu or Fluxbox....

---

### Post by eriqjaffe on 2008-03-10
FWIW, I run Ubuntu (not the full Gnome desktop, mind you, but Fluxbox on top of a command-line install) on a similar system, and Flash stuff runs like an absolute ***dog*** - to the point where I've actually disabled it.  If your son tries to go to a Flash-heavy site (like, say, Nick.com), forget about it.

That being said, I've found that Opera 9.5b is the snappiest browser on my laptop, and it's far more full-featured than something like Kazehakase.

---

