---
title: "Top panel has disappeared"
date: 2008-02-07
forum: General Help
---

### Post by tc101 on 2008-02-07
I have ubuntu installed on a backup hard drive that I use to play
around with so I don't really mess up anything on this main one that I
use all the time.   

I replaced the regular hard drive with the backup just now to test the
changes that we have been talking about.  I have not used the backup
hard drive in months, but it does have ubuntu 7.10 installed on it.

ubuntu loaded.  It did the force check disk thing because it had not
been done in 280 days.

Then the background picture loaded just fine, but the top panel, with
"Applications  Places  System"  did not load.  

The only thing I was able to do was right click the desktop background
where I could make changes to background, create launcher and so on. 
I used the browse function of create launcher to verify that the file
system was still there.

I could not do anything and had to put this regular hard drive back in
the computer.  

Any idea what might have caused the top panel to disappear and how I
can get it back?

---

### Post by Don Gatto on 2008-02-07
Hello,

Can you run the gnome-panel (or something with a similar name) in a terminal?

---

### Post by drs305 on 2008-02-07
Just a tip if you create a lot of shortcuts on the panel once you get it back:
Your custom panel shortcuts are located in:
/home/<username>/.gnome2/panel2.d/default/launchers

I backup this folder from time to time and it makes it easy to restore should I lose or mess up the panel. ;-)

---

