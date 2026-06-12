---
title: "Installing fluxbuntu"
date: 2007-03-20
forum: General Help
---

### Post by ThaDoctor99 on 2007-03-20
Hi I were not sure whether to post this question here or somewhere else.

But I would like some help with a command to install fluxbuntu on a old laptop, a standart computer from 2001 Toshiba Satellite, well it is none of the new Satellite boxes it is really old. 


But I just need the command to install fluxbuntu to the harddisk, the computer wasn't quite big enough to have a bigger version of ubuntu like kubuntu or one of the bigger distros into it, so I will try to install the smaller distro.
Just really need the command

---

### Post by IcemanV9 on 2007-03-20
There is no command to install fluxubuntu from {U,K,X}buntu LiveCD or repo (if that's what you are asking).

It may be a good idea to go over @ [[COLOR="Orange"]**fluxubuntu**[/COLOR]]("http://fluxbuntu.org/") website and download their ISO.

---

### Post by Ramses de Norre on 2007-03-20
Install from alternate disc and select server install, then install ubuntu-minimal and fluxbox. You'll then have an as small as possible ubuntu system with fluxbox and without gnome.

---

### Post by ThaDoctor99 on 2007-03-21
I have the iso from fluxbuntu, but I would just like to know if I can install it from the disc or not...
As I have got this really old computer which can't run Kubuntu and not at all Ubuntu.

---

### Post by hikaricore on 2007-03-21
If you can burn it to a cd, and that computer can boot from the cd, it should be possible.

Note you will need atleast 256mb of ram (may be different with fluxubuntu, but that's the spec for normal live cds) to boot the cd.  If this is not possible, there are other ways to do this.  Personally I've written an iso to an external usb drive and booted to install *buntu on several machines which were not capable of booting from the cd, this may still not be possible if the computer does not have enough ram.  If the ram is an issue I believe you can also create a swap partition on an external drive, linux should recongnize this and use that space instead of memory.  Alot of what I'm mentioning here is just speculation + trial and error.  Hopefully you have enough memory and don't need to go through all these hoops.  :)

---

### Post by bodhi.zazen on 2007-03-21
To install Fluxbuntu :

Boot to the Fluxbuntu CD

Open a terminal.

Type : ```
sudo ubiquity
```

Ubiquity is the graphical installer for Ubuntu so installation is otherwise similar to Ubuntu.

FYI, you are welcome on the Fluxbuntu Forums as well ...

[Fluxbutu forums](http://community.fluxbuntu.org/)

You will find how-to's there as well.

---

### Post by ThaDoctor99 on 2007-03-22
well that commando didn't work with Kubuntu and Ubuntu didn't even load but fluxbuntu just is installing which is really nice....
Thanks for the help

---

### Post by caveman56 on 2007-03-29
Hey anyone know the user id and password to use with the live fluxubuntu cd, their site is down and i'm trying to test out an install of it to see what the speed differance is over gnome in our schools computer lab.

thanks,

Dave

---

### Post by bodhi.zazen on 2007-03-29
Username : fluxbuntu
PW : livecd

---

### Post by zandoval on 2007-08-01
Hey - Heres a trick that works for alot of systems when in a pinch - Just remember to leave a note for the next guy who comes along of what you did...

Ctrl-Alt-Backspace a few times to get to a command prompt

then

sudo passwd root

enter your new root pass word twice

then

startx

then

Enter your pass word

That should get you in - I have had to use this method after "zeros" have trashed the log in entry scripts...

Good Luck - Have Fun...

---

### Post by bns on 2007-08-06
Speaking of fluxbuntu, anybody know what's going on with it?  The community forum has been down for a while, and I'm anxious to see how development is coming.

---

### Post by bodhi.zazen on 2007-08-06
I do not know why the forums are down ...

They (we) are planning a release with 7.10. Feisty was skipped so that Fluxbuntu relsease schedule would coincide with Ubuntu.

If you irc, come on over to #fluxbuntu (on freenode)

The forums are back up now, some upgrades for the forums are planned so it may be a little spotty (hope not)

---

### Post by bns on 2007-08-07
Thanks, bodhi.  I tried out fluxbuntu several months ago, and I've been anxiously awaiting a more mature version of it.  I have been checking in on the web page every few days just to keep tabs on it.  I'll go check now.:)

---

### Post by bodhi.zazen on 2007-08-07
You are most welcome. Fluxbuntu is looking very nice and we are planning a text installer (alternate CD) for low RAM machines. 

SLiM will likely be the log in screen :  [http://slim.berlios.de/](http://slim.berlios.de/)

---

### Post by merlinus on 2007-08-07
Will fluxbuntu be similar to fluxbox?  Differences?  Upgrade path?

Thanks!

-merlin

---

### Post by bodhi.zazen on 2007-08-08
Well, fluxbox is a window manager. There are a few tweaks to Fluxbox, mainly with start scripts.

Think of Fluxbuntu as an Ubuntu server install + fluxbox + ROX (fox file manager) + light weight apps. We tend to shy away from applications that will pull in extensive KDE/Gnome/XFCE llibs.

From there you have all the Ubuntu repos at your finger tips and you can install / upgrade additional apps as needed.

The goal is to again be in sync with Ubuntu in terms of compatibility and upgrades (ie the intention is NOT to fork Fluxbuntu).

---

