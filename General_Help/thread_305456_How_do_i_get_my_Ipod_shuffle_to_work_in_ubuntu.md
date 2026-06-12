---
title: "How do i get my Ipod shuffle to work in ubuntu?"
date: 2006-11-23
forum: General Help
---

### Post by implor on 2006-11-23
do any one know how to get a ipod shuffle (2nd gen) to work (add/remove music) in ubuntu?

---

### Post by Phalangees on 2006-11-23
I know there's a program called ipodslave for linux that works quite nicely.

try

sudo apt-get install ipodslave

it may not work because that's what I think I did, but it's off the top of my head.

---

### Post by ChrisC on 2006-12-30
I installed gtkpod and it all Just Worked.

When I plug the iPod in, rhythmbox launches automatically, which I don't want.  So the only tweak was that I had to go into "Preferences" -> "Removable Drives and Media" and tell it to launch gtkpod instead.

I did not have to mess with any of the HFS/OSX/diskutil stuff that searching in this forum led my to believe that I'd need to do.  I just installed gtkpod, plugged it in and it worked.  On Dapper.

---

