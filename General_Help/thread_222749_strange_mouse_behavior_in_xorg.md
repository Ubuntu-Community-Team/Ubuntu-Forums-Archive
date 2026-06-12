---
title: "strange mouse behavior in xorg"
date: 2006-07-25
forum: General Help
---

### Post by tsumi on 2006-07-25
Running 2.6.15-26-386 on a dell optiplex 170L.

The mouse is a stock mouse for the system which is a USB ball mouse (dell branded as well)

I use Terminal Server Client a lot where I work to connect to remote windows server machines to admin them. I also use a client on the windows servers called DameWare which allows you to remote controll other windows machines inside the network providing you can produce a domain administrator login.

The problem I am having is that when a screen saver kicks off (i.e when coming back from a screen saver state) from a remote session, the mouse clicks stop responding. The mouse still moves around the screen but I do not get a response from either the remote session or the local x session..

Any help / suggestions / ideas / ... well anything at all would be greatly appreciated.

---

### Post by tsumi on 2006-07-25
no ideas? this is a pretty annoying issue for me... ](*,)

---

### Post by frobroj on 2006-09-20
Me and my coworker are also experiencing this problem. It is extremely annoying!!!! I have a logitech trackball and my cohort has a microsoft optical mouse.

---

### Post by frobroj on 2006-09-20
Think we got it. The xscreensaver was not installed for some reason. The xscreensaver-data was(which you would think would have a dependency on xscreensaver.). Anywho, we did a reinstall of xscreensaver-data and xscreensaver-gl and an install of xscreensaver & the two *-extra packages. Everything seems to work great now. Hope this helps...

Jeff M

---

