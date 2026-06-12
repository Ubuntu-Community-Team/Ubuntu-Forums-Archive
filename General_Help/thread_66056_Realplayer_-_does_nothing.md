---
title: "Realplayer - does nothing"
date: 2005-09-15
forum: General Help
---

### Post by Steve Smith on 2005-09-15
I've installed realplayer, through Synaptic.  When I click on the icon in the Applications menu, nothing appears to happen, although realplay.bin is running.  Has anyone else had this problem?  Thanks :)

---

### Post by numberexhaust on 2005-09-15
[QUOTE=happysteve]I've installed realplayer, through Synaptic.  When I click on the icon in the Applications menu, nothing appears to happen, although realplay.bin is running.  Has anyone else had this problem?  Thanks :)[/QUOTE]
 yeah, but i gave up on it and moved to xine.  seriously, get that.  it's amazing.

---

### Post by shyguy on 2005-09-15
After following this I was able to get Real Player to start. Did not follow steps 11 & 12 though.  :)  HTH

[http://ubuntuguide.org/#configuresoundproperly](http://ubuntuguide.org/#configuresoundproperly)

---

### Post by Steve Smith on 2005-09-21
[QUOTE=shyguy]After following this I was able to get Real Player to start. Did not follow steps 11 & 12 though.  :)  HTH

[http://ubuntuguide.org/#configuresoundproperly](http://ubuntuguide.org/#configuresoundproperly)[/QUOTE]
 Thanks, will give it a go!

---

### Post by peterthewolf on 2005-09-22
Edit /etc/esound/esd.conf and change auto-spawn=0 to auto-spawn=1
If real player still does not work re-install real player and reboot ubuntu

---

### Post by cbudden on 2005-09-22
[QUOTE=peterthewolf]Edit /etc/esound/esd.conf and change auto-spawn=0 to auto-spawn=1
If real player still does not work re-install real player and reboot ubuntu[/QUOTE]
 I found that to get realplayer to work, i had to turn of the option to start sound server at startup.  Click system -> preferences -> sound and untick the Start sound server option.

---

### Post by peterthewolf on 2005-09-22
Yes that will do it BUT if you load an audio disc cdplayer will not make any sound. If you want cdplayer then set enable sound back on and alter auto-spawn as I said above.

---

### Post by antariksh on 2005-09-25
I am a bit disappointed that the Real Player in the Ubuntu repositories is an obsolete RP8 version, whereas the latest version is 10. My previous distro came with 10 pre-installed.

Moreover, when I try to install RP10 on Ubuntu directly from the RP website, it just hangs after installation and does nothing.

I have similar complaints about skype and adobe acrobat on ubuntu as well, but those are for another thread.

---

### Post by raven on 2005-09-26
[QUOTE=shyguy]After following this I was able to get Real Player to start. Did not follow steps 11 & 12 though.  :)  HTH

[http://ubuntuguide.org/#configuresoundproperly](http://ubuntuguide.org/#configuresoundproperly)[/QUOTE]


In this link above does it apply to Kubuntu, KDE 3.4.2
cause I did all the steps and still can not have
2 sound apps in the same time
thanx for the help

---

