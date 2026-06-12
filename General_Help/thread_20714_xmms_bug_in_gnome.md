---
title: "xmms bug in gnome ?"
date: 2005-03-18
forum: General Help
---

### Post by dusu on 2005-03-18
Hi,

I'm running Hoary and I have the following problem with xmms :
I can listen to web radios with it when I use xfce4, and blackbox for example, but I can't when I'm running gnome  ](*,) 
Under gnome, when I select a radio, and press on the xmms play button, xmms goes to the right radio address but plays nothing.
Then, *any* action I do (like press play again, or try to quit xmms) freezes xmms !

Does any one know why things do not work only when using gnome ?
Thanks for any help !

---

### Post by subjectdenied on 2005-03-18
try to use the ESD (Enlightenment Sound Daemon) plugin in the output-options of XMMS. your problem looks identically to mine i had with the Beep Media Player, when the soundcard was blocked by another application (in your case gnome desktop sounds i think)

you might have to apt-get the plugin

---

### Post by dusu on 2005-03-18
[QUOTE=subjectdenied]try to use the ESD (Enlightenment Sound Daemon) plugin in the output-options of XMMS. your problem looks identically to mine i had with the Beep Media Player, when the soundcard was blocked by another application (in your case gnome desktop sounds i think)

you might have to apt-get the plugin[/QUOTE]

That worked ! Thanks a LOT :D

---

