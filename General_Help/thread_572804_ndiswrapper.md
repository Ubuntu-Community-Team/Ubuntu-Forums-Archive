---
title: "ndiswrapper"
date: 2007-10-10
forum: General Help
---

### Post by todd_freeride on 2007-10-10
hello, I'm having a ton of trouble with ndis wrapper, I cannot figure out why it doesnt load anymore. I used it all the time trying to install things. I've spent around 40 hours trying to get ubuntu working with 4 different cards, none of them work at all. ubuntu wireless is something that doesnt exist.

But upon trying to install a different .inf file I jacked from the airlink CD, I try to go and load ndis wrapper, but it then only loads, then shuts down. I cant even browse for a file. it just loads, then turns off and dissapears. does anyone know whats wrong? I went in and re installed the program, but it still just loads up a little bit, then crashes. thanks.

---

### Post by HermanAB on 2007-10-10
Go to the ndiswrapper web site and start reading:
[http://ndiswrapper.sourceforge.net/joomla/](http://ndiswrapper.sourceforge.net/joomla/)

If a program refuses to run, run 'ps -e' and make sure that the program isn't running already - if so kill it.

If you can't get it to install at all, change to Mandriva, since it has wizards for everything, including ndiswrapper.

Cheers,

Herman

---

### Post by texasjim on 2007-10-13
> **todd_freeride said:**
> hello, I'm having a ton of trouble with ndis wrapper, I cannot figure out why it doesnt load anymore. I used it all the time trying to install things. I've spent around 40 hours trying to get ubuntu working with 4 different cards, none of them work at all. ubuntu wireless is something that doesnt exist.

But upon trying to install a different .inf file I jacked from the airlink CD, I try to go and load ndis wrapper, but it then only loads, then shuts down. I cant even browse for a file. it just loads, then turns off and dissapears. does anyone know whats wrong? I went in and re installed the program, but it still just loads up a little bit, then crashes. thanks.

I had a similar problem loading a driver that I installed using WINE, then NDISWRAPPER.  Turns out the wine c:disk file "Program Files" apparently is not a valid Linux filename (the blank).  I copied the entire AWLH6045 folder (for the Airlink101 AWLH6045 I am using)  from "Program Files" to a folder on my /home.. then used the ndiswrapper GUI to point at the .inf file in my new folder. Plugged in the card, rebooted just for fun, modprobe'd ndiswrapper and bingo.  By the way, for this Marvell Top-Dog driver you gotta configure wine as winxp or later.  Xp worked for me.  Good luck.

---

### Post by cssutto on 2007-10-13
If read you correctly, your troubles started while trying to get your wireless working.

Get wicd.  I worried with wireless for about three weeks. Got wicd and had my wireless router up and running in 15 minutes, WPA and all.

---

