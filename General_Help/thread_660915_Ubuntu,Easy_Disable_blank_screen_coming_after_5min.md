---
title: "Ubuntu,Easy: Disable blank screen coming after 5mins of no use.."
date: 2008-01-07
forum: General Help
---

### Post by Peter Sommer-Larsen on 2008-01-07
Hey I just installed a fresh installation of Ubuntu - and it has been many years
since I did that.. this is why Linux is so nice.

I have one question though..

I forgot how to disable the blank screen which pop up when I
have not been using the computer for 5mins. Pretty annoying when watching movies.
It doesn't help to disable the screen saver - I remember that I out-commented something
in a file.. but which.?

Help please..

Thx.
Sommer

---

### Post by SOULRiDER on 2008-01-07
What version of Ubuntu are you using? Its probably a good idea to upgrade since youre probably not getting any security upgrades or anything.

---

### Post by Peter Sommer-Larsen on 2008-01-07
Oh thx - but my system is allready 100% up to date..

---

### Post by Peter Sommer-Larsen on 2008-01-07
And by the way I use xubuntu (xfce4) with openbox..

---

### Post by xc3RnbFO8P on 2008-01-07
You could uninstal screensaver, do you realy need screensaver?

---

### Post by djrobthaman on 2008-01-07
One way to do it is to edit the xorg.conf file.  That's located in your /etc/X11/ folder.

To edit it just do the following:

Open the terminal

type:
sudo gedit /etc/X11/xorg.conf

Scroll to the bottom of the file and cut and paste the following:

Section "ServerFlags"
	Option      "blank time" "0"
	Option      "standby time" "0"
	Option      "suspend time" "0"
	Option      "off time" "0"
EndSection

Save it and restart your system.

You should be all set after that.

---

### Post by oldsmobile_mike on 2008-01-07
Have you tried VLC Media Player?  I've used the PC version for years (and just installed the Ubuntu version yesterday on my new Ubuntu PC).  While I can't speak on the Linux version of it yet, I know for a fact that VLC disables the screensaver during playback on a Windows PC.

---

### Post by Peter Sommer-Larsen on 2008-01-07
> **djrobthaman said:**
> One way to do it is to edit the xorg.conf file.  That's located in your /etc/X11/ folder.

To edit it just do the following:

Open the terminal

type:
sudo gedit /etc/X11/xorg.conf

Scroll to the bottom of the file and cut and paste the following:

Section "ServerFlags"
	Option      "blank time" "0"
	Option      "standby time" "0"
	Option      "suspend time" "0"
	Option      "off time" "0"
EndSection

Save it and restart your system.

You should be all set after that.

Hehe thx I found this after a long search. Lets see if it works ;)

---

### Post by bgat on 2008-02-13
According to the xorg.conf manpage, those options have no spaces in them.  E.g. "BlankTime", etc.

b.g.
--
Bill Gatliff
[email]bgat@billgatliff.com[/email]

---

