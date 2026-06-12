---
title: "help me..again"
date: 2008-04-03
forum: General Help
---

### Post by uselessname on 2008-04-03
ei guys...another linux newbie here...

im going straight forward to my problem..

i know ...windows discussion is NOT welcome here..

but anyway...

i can't access my windows xp bacause it was infected by a spyware and it keeps on restarting and restarting...

can i possibly re-format or re install windows xp without doing the same thing as to my ubuntu os..

pls help me..because i have already store a lot of file in my ubuntu os..and i kinda feeling bad if i re-install again my ubuntu os...

but then ..it's ok if it's that the case..im ready to accept the fate of my pc...

arigATO gozaimasu

---

### Post by NToasteD on 2008-04-03
You could do a repair install of Windows. This can be done by booting the Windows XP CD you have. Boot to main Windows setup. Press enter, f8 to agree to terms, then you should be prompted to press R to repair or ESC for a fresh copy. Press R, this will begin the repair install which will rewrite the Windows XP files without formatting the drive.

---

### Post by sekinto on 2008-04-03
If you have a virus or something on your Windows partition you could always try scanning your computer with an anti-virus utility from Ubuntu (Avast!, ClamAV, et cetera). You would need to make sure to mount the Windows partition first though, then you can scan the directory you mounted it to.

Anyway, if you really want to reinstall XP without ruining Ubuntu you can do this:
Insert the XP CD.
When it gets to the part about formating only delete your NTFS partition, don't delete your Ubuntu one (which will probably show up as something like "unknown").
Then choose the empty space to format and install XP on.
Note: XP will write its bootloader to the MBR so you will have to re-add grub, to do this stick in your live CD and fallow this guide:
[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

---

### Post by zvacet on 2008-04-04
Can you boot Windows in safe mode and then just restore it (back to the pervious restore point)?

---

### Post by uselessname on 2008-04-04
thanx guyz..

i'll try those suggestions...

---

### Post by lemonlaw95 on 2008-04-04
you could uninstall windows.  no, you could FORMAT your windows partition/drive.  :)

---

### Post by uselessname on 2008-04-04
another problem here...

i can't boot on my ubuntu now...

i selected ubuntu then an error told me that....error mounting partition(something like this..)

any suggestions??

linux newbie

---

### Post by zvacet on 2008-04-04
Try to reinstall grub.[Here](http://ubuntuforums.org/showthread.php?t=224351&highlight=grub)

---

### Post by uselessname on 2008-04-04
@zvacet

thnx for ur reply 

ive tried your suggestions...

here's what i did:

find /boot/grub/stage1
 .....the result is (hd0,1)

root (hd0,1)

setup (hd0)

quit

...then right after that i quited the terminal and I've restarted my computer

then it boot-up, i've selected ubuntu on the boot menu then voila!

error 17: cannot mount selected partition
press any key to continue

have i done something wrong or its just me...

arrrgh...any suggestions???!!!

---

### Post by Comrade Mike on 2008-04-04
GRUB is probably trying to mount the wrong partition for Ubuntu. Boot up with a Live CD, run gparted and check what your Ubuntu partition is called (presumably something like /dev/hda2). Then open /boot/grub/menu.lst on your Ubuntu partition and make sure the Ubuntu entries point to the correct partition. If they don't, change them, save the file and reboot. It should work then.

**Edit:** Actually, scrap all that gparted stuff, that's wrong. I was thinking of something completely different. How many partitions did you have before and how many do you have now?

---

### Post by zvacet on 2008-04-05
[Here](http://users.bigpond.net.au/hermanzone/p15.htm#When_trying_to_boot_Linux)

---

