---
title: "How to Remove"
date: 2006-08-28
forum: General Help
---

### Post by markcausa on 2006-08-28
Hello - I installed Ubuntu on my laptop a bit back and I love it so much I've installed it on my desktops!

Now I must remove Ubuntu from my laptop, because I need the space back.

I have Windows XP and Ubuntu currently.

How can I remove Ubuntu and get that old partition back for Windows to use? ](*,)

---

### Post by divague on 2006-08-28
First to have to fix the mbr, you can use you windows XP cd to do this. Boot from your windows xp cd and select the restoration console, select your windows XP installation, and put:

fixmbr

when it's done, reboot your machine and with a program like partition magic you can add the space from your ubuntu partition to the windows pertition

---

### Post by markcausa on 2006-08-29
Done and Done.

I actually used the Live CD of Ubuntu I had to run the install manager for the partition area.

It worked like a charm! Thank you very much. :)

---

### Post by football-fan on 2007-05-26
I cannot boot through a Windows CD, and I can't use the six floppy discs because my laptop does not support Floppy boot... what should I do?

---

### Post by mikewhatever on 2007-05-26
> **football-fan said:**
> I cannot boot through a Windows CD, and I can't use the six floppy discs because my laptop does not support Floppy boot... what should I do?
Use the [Uninstall Page]("http://www.users.bigpond.net.au/hermanzone/p18.htm")

---

### Post by mirridon on 2007-06-22
Easy step by step:

1. You need Ultimate Boot CD, the kind user has provided a link above so use that.

2. Burn the UBC to a CD and reboot your computer

3. Now press F12 to boot from CD, now click filesystem tools->partition tools-> And it should be the first avaliable freeware software that appears on the list, Im pretty sure its like Ravish or someting similar to that.

4. Once all has loaded it will come up with your partitions and master boot record, press enter and down the bottom it will have option in which you have to press space to cycle through them. The default installation of windows XP shpuld be on HD1/Partition 1 so you need to select that.

5. Exit saving changes. Once exited and evetrything is save and the screen isnt doing anything, as in loading or unpacking files press Cntrl + Alt and press delete. Now when it loads it will load windows rather than ubuntu.

6. You need a tool like partition magic to rejoin the two partitions togther. You can play around with the UBC but after checking all of the freeware its unable to rejoin partitions. It is able to however to delete them, but the partition seems to stay there.

---

### Post by arturk on 2007-10-22
Hi,

I installed Ubuntu on my comptuer (IBM T60). So, now I want to go back to Windows XP since a lot of my external devices don't work with linux. I used the Live CD to remove everything from the hard drive and then booted the computer with the windows CD it said that the hard drive cannot be found. I've been reading many forums and I couldn't find anything that would work. So, does anyone have any idea what I can do so that my hard drive gets recognized?

Thanks

Art

---

### Post by TheK3vin on 2008-07-09
Heh, I know this is a raheely old thread, but I figured it's better than starting my own of the same purpose...

Anyway.  I was reading through the uninstall page, and found out it'd be much easier to just prevent the grub menu from coming up.  Well, the problem is I don't know how to edit the menu.lst file.  Whenever I try to save, it tells me I don't have the necessary permission.  Is there some kind of sudo-save or something?

---

### Post by jerome1232 on 2008-07-09
```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by TheK3vin on 2008-07-09
That worked great, thanks!

EDIT:
Now, something else is showing on startup called the Windows Boot Manager, which is for some reason asking if I want to Run "Acer eRecovery" or Vista (it's my mom's laptop, I hate Vista just as much as everyone else).  Can I get rid of this?  It's kinda annoying...

---

