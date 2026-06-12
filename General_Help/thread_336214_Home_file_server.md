---
title: "Home file server"
date: 2007-01-11
forum: General Help
---

### Post by m.rollman on 2007-01-11
First, let me say that I'm coming from the very closed world of OS X (and XP, through this past June), so I'm not accustomed to Linux just yet. Well, I'm not accustomed to Linux or Ubuntu at all, for that matter.

So, I just recently purchased [this]("http://www.hcditrading.com/Shop/Control/Product/fp/vpid/2683419/vpcsid/0/SFV/29664") Dell Optiplex GX150 with the intention of setting it up as a file server. I figured for $70, $150 or so for a larger HDD, I could add quite a bit of storage space that would be accessible anywhere, on my LAN or over the 'net, for less than an external HDD.

I've been doing my homework on what I need, how to set it up, etc., but I am a Linux n00b and would like a little guidance just so I don't screw anything up. Just so you know exactly what I'm trying to do: set up a headless file server that I can access on my WLAN (server would be wired to my router/switch, not wireless) and across the net; put on a remotely accessible BitTorrent client; and have, on the rare occasion I do decide to use it as a desktop, basic browsing/mail capabilities.

From what I understand so far, I'll want to install and setup Edgy Eft as a LAMP server ([these directions]("http://www.debianadmin.com/ubuntu610-edgy-lamp-server-installation-with-screenshots.html") seem to explain that), and then pop on SSH server. After that, I'll want to put on Samba, and after that Torrentflux. As you can see from the link, I have a nice guide to help me with the LAMP/SSH installation, but I'm kind of lost after that. If anyone could help me with that, or direct me towards a good setup guide, I'd really appreciate it.

The other thing I think I'll be needing help with is upgrading the HDD. I've read conflicting things, but from what I understand, because of it's age my Optiplex wouldn't support a partition any HDD larger than 137GB. That's a problem for me, because I'm looking to drop in a drive with at least 400GB. Obviously there's ways around this, but could someone tell me what they are? Is it a matter of putting on a new BIOS, will it not matter with Ubuntu on there, or what? If it helps any, [here's the GX150 page from Dell]("http://support.dell.com/support/edocs/systems/opgx150/en/ug/specs.htm").

Well, let me shut up for now. Thanks in advance for helping me!

Mike

---

### Post by LotsOfPhil on 2007-01-11
I have never done a server-only setup, but I am concerned about the "decide to use it as a desktop, basic browsing/mail capabilities" part. I am afraid you might only have a command line.

---

### Post by Modernity on 2007-01-11
Yes, if you install the server edition, you will not get a GUI. You can install GUI later, if you need to, but since you are learning Linux, it might be helpful to install the desktop version first, then install the individual packages, ie. Apache, Php, Samba and whatever else you may want.

---

### Post by m.rollman on 2007-01-11
OK, well the web browsing/mail isn't all that terribly important to me. So long as I can access the thing over my LAN and the 'net, and solong as it runs BitTorrent (TorrentFlux, I guess), I'm fine. As I said, I'm thinking of this primarily as a headless file server, and expect to manage most things through a web GUI over LAN/Internet. So again, if anyone could point me in the right direction with Samba, the hard drive, etc., I'd really appreciate it.

---

### Post by LotsOfPhil on 2007-01-11
[http://librenix.com/?inode=1075](http://librenix.com/?inode=1075)

Try this for a samba tutorial. I have always heard setting up Samba described as a pain. I don't think it is that bad. By the time you are done setting this all up, I think you will be plenty accustomed to Linux.

I don't know about your hard drive. I think you'll be okay, but that is just a hunch. If the HD doesn't work for you, you can probably return it.

---

### Post by cmost on 2007-01-11
If you want to easily setup a pretty nice home server, consider using PCLinuxOS 0.93 (a.k.a 'Big Daddy'.)  This is a live-CD that you can try out and then install to hard disk if you like it, just like Ubuntu.  The difference, however, is that it's derived from Mandriva but still utilizes Synaptic (Apt for RPM) for package management (just like Ubuntu.)  PCLinuxOS relies upon a fully up-to-date and extremely user friendly KDE desktop that is setup by default to ease former Windows users' transition to Linux.  There are over 5000 high quality packages included in the PCLinuxOS repositories, including the complete SAMBA server suite of tools.  PCLinuxOS includes a very easy to use (and very Windows-like) control panel where you can easily setup server shares, etc.  Please consider it.  I don't think you'll be sorry.

---

### Post by bodhi.zazen on 2007-01-11
Almost any version of Linux will do.

If you do a server install you will have no GUI ... (GUI's are over rated)

Access the box with ssh or [webmin](http://www.webmin.com/)

here is a server guide:

[http://doc.gwos.org/index.php/ServerGuide](http://doc.gwos.org/index.php/ServerGuide)

HTH

---

### Post by esaym on 2007-01-11
Some info here: [http://www.rage3d.com/board/showthread.php?t=33866415](http://www.rage3d.com/board/showthread.php?t=33866415)

I started to do a similar project but I bought a laptop instead:mrgreen:

---

### Post by cmost on 2007-01-11
"f you do a server install you will have no GUI ... (GUI's are over rated)"

I strongly disagree, and, your statement implies that a Linux server necessitates foregoing the GUI.  This isn't true at all.  It's Linux, you can have it any way you want.

It sounds as though he's going to want a GUI.  There's nothing wrong with having a GUI on a server (this is a home server after all, it's not as if he's going to be worried about the slight increase in overhead since there will likely only be a few users.)  The GUI will make managing users and shares much MUCH easier.  I say go with a GUI and enjoy!

---

### Post by Iowan on 2007-01-12
> **bodhi.zazen said:**
> 
If you do a server install you will have no GUI ... (GUI's are over rated)


Not to be contrary... but I'd have to agree.  An out-of-the-box (off-the-CD?)  _SERVER_ install will have no GUI - but that doesn't suggest you can't add one later. :)

---

### Post by cmost on 2007-01-13
"Not to be contrary... but I'd have to agree. An out-of-the-box (off-the-CD?) SERVER install will have no GUI - but that doesn't suggest you can't add one later."

I'm aware of this.  What I strongly disagree with is the former posters assertion that GUI's are over rated (presumably for servers.)  For a lay person managing a home server with minimal users, it's ridiculous to expect him or her to manage the thing from the command line.  Especially when it's extremely easy to do so from the Gnome or KDE environment.

---

### Post by Azakus on 2007-01-13
I've done this with an old computer of mine to do backups and I must say the easiest way to install Samba is to follow the Ubuntu Wiki: [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
As for managing it, if you use the ssh command with the arguement -X, it will allow you to use the GUI of programs on your server
Example:
```
ssh -l admin -X 192.168.XXX.XXX
gedit
```
This will forward the GUI display to your computer so you can use the GUI program gedit.

---

### Post by dannyboy79 on 2007-01-16
> **Azakus said:**
> I've done this with an old computer of mine to do backups and I must say the easiest way to install Samba is to follow the Ubuntu Wiki: [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
As for managing it, if you use the ssh command with the arguement -X, it will allow you to use the GUI of programs on your server
Example:
```
ssh -l admin -X 192.168.XXX.XXX
gedit
```
This will forward the GUI display to your computer so you can use the GUI program gedit.

if all you need is to edit stuff with a text editor I wouldn't go thru with that but just use ssh and nano. Nano is really easy to use if you just need to do text edits. there is a search function also.

---

### Post by msimon1960 on 2007-01-16
I agree -- start with a desktop setup and add the rest.  The gui overhead is microscopic and the convenience is invaluable.

Matt.

---

### Post by nix4me on 2007-01-16
Install the server install and select the lamp install from the menu.  Then follow the wiki instruction for samba install.  Its easy.

Then later, if you want a gui, just apt-get gnome.  This is all documented very well on the wiki.

As far as the harddrive size, make sure you are running the newest bios possible...it should support large harddrives although i have not verified this.

Here is a link to the wiki:
[https://help.ubuntu.com/6.10/ubuntu/serverguide/C/index.html](https://help.ubuntu.com/6.10/ubuntu/serverguide/C/index.html)

nix4me

---

### Post by jd4x4 on 2007-01-17
GUI's are _underrated_ i.m.o.
I haven't used it much yet, but I've just set up a home server on Xubuntu that I want to use to learn & develop php on.. it was reasonably simple (after I removed the text-based Ubuntu server!).

I used plain-vanilla Xubuntu install, then got XAMPP, and after it was up & running I got Webmin. I figure a web interface beats text/command-line even if it isn't a "conventional" GUI.

Links are:
[http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html)
and
[http://www.webmin.com/download.html](http://www.webmin.com/download.html)

---

