---
title: "Awful unreadable notification on Lubuntu 15.04"
date: 2015-05-24
forum: General Help
---

### Post by minecraft2048 on 2015-05-24
[img]http://i.imgur.com/QysH7r4.png[/img]

That whiteish background makes the text unreadable, and yes, it happens to all of the notifications. Compare this with this:

[img]http://i.imgur.com/FCLU1Gw.png[/img]

Its on Lubuntu 14.04 LTS, and the notification background is solid grey making the text highly readable. This small thing kinda holds me back from upgrading my laptop to 15.04, although there is that NetworkManager upgrade and pcmanfm can now browse the network, so how do I revert or change the background of the notification?

---

### Post by vasa1 on 2015-05-24
That's unfortunately a known bug. See [https://bugs.launchpad.net/ubuntu/+source/lubuntu-artwork/+bug/1362555](https://bugs.launchpad.net/ubuntu/+source/lubuntu-artwork/+bug/1362555) for a workaround.

Sidenote:
I don't understand [comment #17]("https://bugs.launchpad.net/ubuntu/+source/lubuntu-artwork/+bug/1362555/comments/17") which seems to imply there's something wrong with the notifier itself:> We should get ridd off this notifier. It's giving problems to XFCE itself. ...I don't see anything wrong with xfce4-notifyd at all.

---

### Post by Dennis N on 2015-05-24
In Lubuntu 15.04, you can find and use an unaffected theme, or you can do what I ultimately did, inspired by comments in the bug report, and fix Lubuntu-default as well:

Create a solid grey panel-bg.png image 60x240 px with Inkscape, and copy it to /usr/share/Lubuntu-default/gtk-2.0/ and to /usr/share/Lubuntu-dark-panel/gtk-2.0/ (This will replace any existing panel-bg.png in those folders.)

That's it.

Appearance of notifications varies with the theme: Illustrated are Lubuntu-default and Greybird, both after this fix.

[ATTACH=CONFIG]262180[/ATTACH][ATTACH=CONFIG]262181[/ATTACH]

---

