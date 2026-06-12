---
title: "Internet setup"
date: 2004-10-30
forum: General Help
---

### Post by robert3061 on 2004-10-30
Hello,
I installed Ubanta and my Internet does not work. Any ideas? I have a cable modem with Charter.
Robert

---

### Post by Rancoras on 2004-10-30
Should be moved to the General Support forum, oh ubuntu-geek?

And Robert, you're going to have to be a little more specific.  Dialup or dsl?  Modem not recognized?  There are many possibilites.

---

### Post by Rancoras on 2004-10-30
Let's keep the discussion here.  So are you connected to your modem via a network card?  If so is your network card detected?  What kind of network card?  Are there any errors that you are getting?  Please give more information about the problem.

---

### Post by beeldings on 2004-10-30
Is your connection set up for use with a router? When I first purchased my router, I experienced connection problems simply because I thought a router was a plug-and-play device (which it is not). From my experiences with Windows and Linux, you have to configure your computer to use the router's gateway  in order to establish an Internet connection. While I am not a networking guru, I might be able to offer some assistance if you are using a Linksys router.

---

### Post by robert3061 on 2004-10-31
[QUOTE=beeldings]Is your connection set up for use with a router? When I first purchased my router, I experienced connection problems simply because I thought a router was a plug-and-play device (which it is not). From my experiences with Windows and Linux, you have to configure your computer to use the router's gateway  in order to establish an Internet connection. While I am not a networking guru, I might be able to offer some assistance if you are using a Linksys router.[/QUOTE]
 I have xp installed on the master drive and my internet connection is fine, I do not have a router. I installed Ubuntu on my slave drive with the duel boot feature. When I boot ubuntu from the slave drive my internet connection does not work. The error messages are page can not be displayed. Come on experts!
Robert

---

### Post by robert3061 on 2004-10-31
[QUOTE=Rancoras]Let's keep the discussion here.  So are you connected to your modem via a network card?  If so is your network card detected?  What kind of network card?  Are there any errors that you are getting?  Please give more information about the problem.[/QUOTE]
 I have xp installed on my master drive and my internet connection is fine, I do not have a router. I installed Ubuntu on my slave drive with  the duel boot feature. When I boot ubuntu from the slave drive my internet connection does nor work. The error messages are page can not be displayed. Come on experts!
Robert

---

### Post by btb on 2004-10-31
Is your network card properly detected? You can check this in the (GNOME) menu computer -> System configuration -> Networking

If so, configure the device and active it. 

If not, look for it in the device manager. If it's not there give a precise description what card you have.

---

### Post by robert3061 on 2004-10-31
[QUOTE=btb]Is your network card properly detected? You can check this in the (GNOME) menu computer -> System configuration -> Networking

If so, configure the device and active it. 

If not, look for it in the device manager. If it's not there give a precise description what card you have.[/QUOTE]
 Thanks,
All that I needed to do was to setup my card in the config mgr
Robert

---

