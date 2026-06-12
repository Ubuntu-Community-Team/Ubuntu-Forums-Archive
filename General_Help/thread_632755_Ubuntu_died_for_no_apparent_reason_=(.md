---
title: "Ubuntu died for no apparent reason =("
date: 2007-12-05
forum: General Help
---

### Post by NNOP on 2007-12-05
Ok, so I'm a bit of a newbie when it comes to Linux. I tried out Red Hat 5 yrs ago or so but gave up and have just decided to give it another go with Ubuntu. So I loaded it up, seemed to be working fine for the last couple of weeks. But this morning it died, more or less. Rather than booting in 20 secs and running nicely it now takes about 5 mins to get from the login screen to the desktop. It also came up with an error about "OAFIID:GNOME_FastUserSwitchApplet" this morning aswell so I deleted the applet and it didnt help.

I tried to open the console and thought it would not open, but in fact it was taking about 5 mins to load and it popped up eventually. Firefox cant download web pages any more etc. Everything is running rediculously slowly, as in everything is taking literally about 100 times longer than yesterday. 

However I didnt change anything at all.. Heh all I did yesterday was use firefox and play that soduko game =) Is there some sort of system restore thing like on XP that I could try? I really dont know how to progress with fixing this.. I thought this sort of junk was only supposed to happen on windows =/.

---

### Post by NNOP on 2007-12-05
Gah, sorry to bother the friendly forum ppl here..

Fixed it, umm.. the network cable was unplugged.. /embarrased

Still its odd that unplugging it from the network causes everything to run extremely slowly..

---

### Post by gilf on 2008-01-16
Possible connection here:

[http://ubuntuforums.org/showthread.php?p=4147122#post4147122](http://ubuntuforums.org/showthread.php?p=4147122#post4147122)

---

### Post by gilf on 2008-01-24
After trying some of the workarounds -- deleting files in /tmp/orbit-user/ this problem is now mainifesting exactly as the first poster described. Computer is slowed to the point of being almost unusable.

HOWEVER, this is not due to a disconnected network cable. The computer is definitely connected, and in fact on the network. Shared folders work normally on this computer when read or written to across the network.

There are frequent error messages about failed configuration settings.

This computer is in a critical state, and I will be trying to purge and reinstall Gnome-applets -- per another user suggestion.

Edit-- additional problem -- computer is not accepting root password, therefore I can't purge and reinstall Gnome-applets.

---

### Post by gilf on 2008-01-24
Resolution:

1.) Booted into Recovery Mode
2 ) **apt-get remove gnome-applets **
3.) ** apt-get install gnome-applets**
4.) **apt-get install ubuntu-desktop**
5.) Restart computer

The computer booted up normally, with no error messages. Speed was normal. Root passwrod works again.

---

