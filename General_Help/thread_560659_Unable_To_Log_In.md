---
title: "Unable To Log In"
date: 2007-09-26
forum: General Help
---

### Post by D4ggity on 2007-09-26
Hello everyone! I just started using Ubuntu again, but as soon as I've begun I've already had an error. For some reason, I can not log in. I try using my name and password, and it turns to a console-ish screen, then black and a lighted black a couple of times, and then goes back to the log in screen. I tried searching the forum, but was unable to come up with any solutions that worked.

Before the error occured, I had: installed Ubuntu 7.04 with Wubi. I had updated everything. I then searched for a line of code that would fix my resolution problem, (It wasn't giving me a widescreen resolution for my widescreen monitor.) and I had used this code: 'sudo apt-get install xserver-xorg-video-intel'. I restarted from this, and this is when the problem showed up.

I tried: 'df -H', but the size was fine. I can log into the terminal, but I'm not sure where to go from from there. 'rm /var/backup/ df -h' and 'rm -ri /var/backups/*' 'rm~/.gnome* && rm ~/.gconf*' 'sudo apt-get install xserver-xorg-core=1:103-0ubuntu10' 'sudo apt-get update' 'sudo apt-get install xserver-xorg-core' 'sudo apt-get install --reinstall xserver-xorg-core'


I had posted this in General Help, but was pointed here because I was told it was a problem that occurs with Wubi.

---

### Post by Skerit on 2007-09-26
I'm afraid I can't offer any help on this matter, don't have an intell graphics card and don't know what a wubi is ...

Definately looks like a driver problem, though. However, when my nvidia drivers have a problem with my resolutions and stuff I usually get a nice error message telling me what's wrong (Yes, the blue kind :P)

I'm sure someone else in here could help you out.. anyone?

---

### Post by ago on 2007-09-26
try 

sudo dpkg-reconfigure xserver-xorg

---

### Post by D4ggity on 2007-09-26
Nope, that didn't work. I got up to the screen asking me if I wanted my graphics as 15, 16, or 24 bit, and it went back to the console and gave me the error, "xserver-xorg postinst warning: overwriting possibly-custimised configuration file; backup in /etc/X11/xorg.conf.20070926183423"

---

### Post by ago on 2007-09-27
> **D4ggity said:**
> Nope, that didn't work. I got up to the screen asking me if I wanted my graphics as 15, 16, or 24 bit, and it went back to the console and gave me the error, "xserver-xorg postinst warning: overwriting possibly-custimised configuration file; backup in /etc/X11/xorg.conf.20070926183423"

Hmm that's not an error check /etc/X11/xorg.conf, should be a new one. If you still have issue try to use Vesa with a low resolution first.

---

