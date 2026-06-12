---
title: "GRUB goes haywire"
date: 2008-04-22
forum: General Help
---

### Post by ferrelas on 2008-04-22
When I installed the rc of 8.04 something broke in GRUB. When I try to boot ubuntu it says: "Error:22 No such partition". While this is annoying, the true disaster becomes apparant when I choose Win XP. It says "Error:12 Invalid device requested" and doesn't boot anything thus turning my computer into a 50 pound paiperwieght. As this is not a favourable situation I would be happy if someone could help me sort this out or at least get rid of GRUB.

---

### Post by smoker on 2008-04-22
whenever i have grub problems, i always use this, simple to use app, 'supergrubdisk'
[http://supergrub.forjamari.linex.org/?section=download](http://supergrub.forjamari.linex.org/?section=download)

you can also use a live-cd, read this thread:
[http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

best of luck

---

### Post by ferrelas on 2008-04-22
I can't boot from cd:s for some reason so I have to solve this from the commandline you can get in GRUB or by puting the hdd in another computer.

---

### Post by louieb on 2008-04-22
> **ferrelas said:**
> I have to solve this from the commandline 
Which command line? Grubs which looks like[B] grub>
[/B]or the recovery shell looks like **root@comuter#**

---

### Post by ferrelas on 2008-04-22
The GRUB one, you get to it after pressing c in the menu.

---

### Post by louieb on 2008-04-23
Probably the root statement in the Ubuntu entry. Does it have a mix of ide  and sata drives?  
Anyway check the root statement.
```
find /boot/grub/stage2
```

Then  go back to the menu and press e to edit the Ubuntu entry. and edit the root statement with what was found. 

Hope that works. If not its going to be a pain to fix without a working CD drive.  Rather that pull the drive.  it would be easier to put a working CD drive in the broke computer and use super grub.

---

### Post by ferrelas on 2008-04-23
Yes, it is a mix of sata and ide drives. I managed to figure most of it out by myself, however grub won't let me edit the menu options so I had to boot into linux mannualy with the right commands from the command line, is there a way (or rather how) to change GRUB's configuration from Linux?

---

### Post by louieb on 2008-04-23
To make your changes stick edit /boot/grub/menu.lst as the super user
So you got to the desktop?
Press Alt+F2 and enter
```
gksudo gedit /boot/grub/menu.lst
```
or from the command line
```
sudo nano /boot/grub/menu.lst
```

Nice to see you got it going. :)

---

### Post by louieb on 2008-04-23
Almost forgot. find the line that has the **groot ** option. and make the same change there. Or it will break agin next time there is a kernal update. Gota go to work now - good luck.

---

### Post by ferrelas on 2008-04-23
I think it should work now, but I've been to lazy to test it yet. Thanks alot for all your help. :) If it doesn't work I'll be back to haunt you. :P

---

