---
title: "Linux network"
date: 2005-10-14
forum: General Help
---

### Post by Cybercool on 2005-10-14
Hello guys,

I have to ask a question. Because I can't find the answer on the internet.
I have a 2 linux installation and soon it will be 3.
One I use as a server.
Two I use as desktop pc's.

How do I make a system so everytime I log in i get my own home directory and account setting (wich are in the home).

I already had on the server a samba installation wich was a domain. In combination with my windows pc's. Do I need to use samba domain server and samba domain client to make this. Or are there other solutions??

Also i have another question.
Does anybody know how to get the Canon mp110 work on linux??
Only the printing function is enough.

I hope i'll get an answer soon.

Greetingz, Ivo Keizers

P.s. Ubuntu breezy really rocks.
I got everything working.
My grafical card
My spdif (optical) sound card
My firewire (ieee1394) video camera with kino
my burner
Everything works very good :D

---

### Post by AndersAA on 2005-10-14
[http://freshmeat.net/projects/pam-mount/](http://freshmeat.net/projects/pam-mount/)

no longer maintained, but it might work anyway ;), or you could probably make pam_run do it, that I wrote, but that's also no longer maintained ;)

[http://hollowtube.mine.nu/wiki/index.php?n=Projects.PamRun](http://hollowtube.mine.nu/wiki/index.php?n=Projects.PamRun)

---

### Post by Brad wilkinson on 2005-10-14
If you are going to run multiple desktops and have a server, you might want to look into apt-proxy to save you  bandwidth in downloading packages multiple times.

search apt proxy on the forums, or look through the howto's.

[http://www.ubuntuforums.org/showthread.php?t=59151]("http://www.ubuntuforums.org/showthread.php?t=59151")

---

### Post by rplantz on 2005-10-14
[QUOTE=Cybercool]
Also i have another question.
Does anybody know how to get the Canon mp110 work on linux??
Only the printing function is enough.
[/QUOTE]

If you go to my post
[http://www.ubuntuforums.org/showthread.php?p=408818#post408818](http://www.ubuntuforums.org/showthread.php?p=408818#post408818)
I describe how I got both my usb printers working. One is an Epson CX-6400 (all-in-one) and I got the scanning to work on that, too.

Bob

---

### Post by Cybercool on 2005-10-15
[QUOTE=rplantz]If you go to my post
[http://www.ubuntuforums.org/showthread.php?p=408818#post408818](http://www.ubuntuforums.org/showthread.php?p=408818#post408818)
I describe how I got both my usb printers working. One is an Epson CX-6400 (all-in-one) and I got the scanning to work on that, too.

Bob[/QUOTE]

Thanks, with this i got it detected, but now I have trouble with the drivers.
The driver of the Canon mp110 is not there. 
Does anybody know if there is a driver that i can use??

edit:
I got the printer working with turboprint.

---

### Post by Craftybytes on 2005-11-21
Hi Cybercool,

I don't actually run Ubuntu as my OS (mine is Debian MEPIS 3.3.1) but I have an Canon MP110 unit and have successfully got the "printer" side working under Linux.  I used the [COLOR="Magenta"]*Canon PIXMA iP1500*[/COLOR] linux driver - downloaded from the web (just do a Google for it).  You'll need to edit the relevant '.ppd' file in the driver folder and change the [COLOR="Orange"]"Resolution"[/COLOR] from 600dpi to 1200dpi (or even 2400dpi - if you want to go that high) to get higher print resolution than the default (much better for photos etc).

Just install the printer using the iP1500 driver and you'll get the 'printer' side up and working OK.

I still have not yet got the "scanner" side working - but hope to get it up within the next week or so.

The printer works very well at the higher resolution - an excellent unit for the price  (AUS$100).

Regards.

---

### Post by nubbe on 2006-03-09
Hi

I can print a test-page but nothing else with the iP1500 driver.
Did you edit the .ppd for something else than resolution?

---

