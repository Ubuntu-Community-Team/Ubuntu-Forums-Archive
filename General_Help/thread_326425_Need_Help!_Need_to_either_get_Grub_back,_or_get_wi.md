---
title: "Need Help! Need to either get Grub back, or get windows bootloader back..."
date: 2006-12-27
forum: General Help
---

### Post by user1397 on 2006-12-27
I am messing around with the partitions on my PC, and I deleted my ubuntu partition (on purpose) using gparted on my ubuntu live dvd, so that now the partitions are setup like this:

partition 1 (hda1 or hd0,0) : windows recovery fat32 (4.2 GB)

partition 2 (hda2 or hd0,1) : primary windows installation (145 GB)

and that's it.  if i boot my computer, grub returns "error 22"

I do have another computer here (which I am using to type this right now), but I do want to get my computer up and running again.

I do not want to put ubuntu back on this PC, I wan to leave it only with windows.


So I want to know exactly how to do the 2 choices I have left: Put grub back on the MBR, or put the windows bootloader back on the MBR.

I prefer getting rid of grub all together, since only windows will be installed on that computer, but if that is too complicated, I guess I could install grub, even though nothing on _[this]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")_ page has worked for me.

---

### Post by bulldog on 2006-12-27
Pop in the windows install disk and let it boot.
Run it till you get three options.
1:Install windows
2:Repair a windows 
3:Exit

Choose 2 [R] and you're getting to a console,choose your windows install and provide the administrator password.

Type fixmbr and after a warning [proceed] you'll have your windows bootloader back.

---

### Post by user1397 on 2006-12-27
> **bulldog said:**
> Pop in the windows install disk and let it boot.
Run it till you get three options.
1:Install windows
2:Repair a windows 
3:Exit

Choose 2 [R] and you're getting to a console,choose your windows install and provide the administrator password.

Type fixmbr and after a warning [proceed] you'll have your windows bootloader back.thanks for replying.

I don't have a system install disk, but I do have a recovery disc.  So I inserted my recovery disc, tried to go to the recovery options screen, but it would not let me because it said it could not read devices or something close to that.

But when I pressed 'Q' for quit, it actually booted me to my windows partition, and every thing's fine with my windows.  

The only dilemma still, is the grub error 22; it still appears when I reboot the computer.

Can I simply type 'fixmbr' in a command prompt from within windows?  or is that not the same as doing it from an install disc?

---

### Post by kelbizzle on 2006-12-27
If you have an ubuntu cd. You can try this [http://www.daniweb.com/blogs/entry708.html](http://www.daniweb.com/blogs/entry708.html)
It's hepled me before.

---

### Post by user1397 on 2006-12-27
wait...when I boot into windows, there is a screen right before the actual booting of windows, which gives me 2 options: windows xp, or windows recovery console


I chose the recovery console, and it asked me to choose which windows installation to log onto;  I chose the only one there is, and then it asked me
 for an administrator password, and I just pressed enter (without tping in a password) and it logged me in.

So now can I type fixmbr in this recovery console?

---

### Post by bulldog on 2006-12-27
Nope that won't work,try the rescue cd it seems it can restore a windows MBR.
Never used it though so you should read up a little :D 

[http://sysresccd.org/Main_Page](http://sysresccd.org/Main_Page)

---

### Post by bulldog on 2006-12-27
> **erik1397 said:**
> wait...when I boot into windows, there is a screen right before the actual booting of windows, which gives me 2 options: windows xp, or windows recovery console


I chose the recovery console, and it asked me to choose which windows installation to log onto;  I chose the only one there is, and then it asked me
 for an administrator password, and I just pressed enter (without tping in a password) and it logged me in.

So now can I type fixmbr in this recovery console?

Give it a try and you'll know:D 
Other wise see my previous post.

---

### Post by user1397 on 2006-12-27
yep, typing fixmbr in the recovery console worked.  thanks bulldog for your help.

it was kinda scary though, it was like "this command could potentially destroy all of your partitions, are you sure you want to continue?"

and I was like "yea"

and it worked.

---

