---
title: "'You do not have the permissions necessary to view the contents of &quot;cdrom0&quot;.'"
date: 2007-01-19
forum: General Help
---

### Post by Dave54 on 2007-01-19
I have a specific CD that when I put it into my computer, Ubuntu (edgy) opens nautilus at "/media/cdrom0" and pops up with an error saying: "The folder contents could not be displayed.", "You do not have the permissions necessary to view the contents of "cdrom0".". 

Since when do I not have permission to browse my own CD? All other CD's work fine, just this one causes this error.

Additional Info:
The CD is UBCD4win (Ultimate Boot CD for Windows)
What I would like to do: put in the CD, right-click the icon that should appear on the desktop, and copy it to another CD.
From the "/media" folder if I double click on "cdrom0", I get the same error.
The permissions of "cdrom0" seem to be Owner: 400, Group: 401.

Tell me if you need more info.
Any help is appreciated.
-Dave

---

### Post by squrl on 2007-01-19
Check your /etc/fstab and see if you have more than one listing for cdrom. I had the same problem and found out cdrom0 was a mistake. When I removed it everything worked good.

---

### Post by Dave54 on 2007-01-19
Not sure what I'm looking for here in the file, but I don't think I see CD-rom more than once. Tell me if anything looks wrong in the file.
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                    0  0  
# /dev/hda1
UUID=9f335c9c-fc49-43ac-b591-3f4e81599e11  /               ext3         defaults,errors=remount-ro  0  1  
# /dev/hda5
UUID=57bfaea6-c4c7-4132-bfb8-013b0a1aa09a  none            swap         sw                          0  0  
/dev/hdc                                   /media/cdrom0   udf,iso9660  user,noauto                 0  0  
/dev/                                      /media/floppy0  auto         rw,user,noauto              0  0  
/dev/hdb1                                  /media/hdb1     ext3         defaults                    0  0  
/dev/hdb5                                  /media/hdb5     swap         defaults                    0  0 
``` 
Thanks for the help.

---

### Post by Kateikyoushi on 2007-01-19
Is your user in the cdrom group ? If not that could cause this.

---

### Post by Dave54 on 2007-01-19
If I go to System > Administration > Users and Groups, I see that there are two users: "root" and "Dave".  If I click on "Manage Groups", I cannot find a group called cdrom or the like. Which group is the cdrom group?

If I select my user and click properties, on the User Privilages tab, "Use CD-Rom Drives" is checked.

Keep in mind all other CD's work fine. Just this one causes the error.

Thanks so far
-Dave

---

### Post by Kateikyoushi on 2007-01-19
Oh I see then what I wrote is irrelevant to this problem, the cdrom is at fault probably file or folder permissions.

---

### Post by Dave54 on 2007-01-19
How do you change the file/folder permissions of the CD-rom drive or CD? Is it possible?

When I right click on cdrom0, properties,  permissions, it says "you are not the owner so you can't change these permissions." I'll have it know i DO in fact own the CD-rom drive, thankyouverymuch. :wink: 

-Dave

---

### Post by Kateikyoushi on 2007-01-19
It never happened to me but I read about that some discs if made with wrong permissions could result in coasters. Probably could ask the source of the disc.

---

### Post by Dave54 on 2007-01-19
I burnt the CD myself. It's UBCD4win (Ultimate Boot CD for Windows). I downloaded it here: [http://www.ubcd4win.com/]("http://www.ubcd4win.com/")

In order to make the CD, you need the program, Windows, and a Windows CD. I have tested the CD and it works fine. It's a bootable CD that basically runs Windows live. Very helpful if you have a windows problem that prevents it from booting.

Since it's bootable, i don't know if it's readable as normal files, that may be the problem. However, I should still be able to make a copy of it. Is there a way to copy it without the icon on the desktop?

Thanks
-Dave

---

### Post by Dave54 on 2007-01-21
Well, I figured out a work-around.
EDIT: Please read next post, work-around did not work.

I'm not too good with terminal, but I looked up some mounting/unmounting commands and tried them out. Here's what I did:```
dmesg |more
```This told me that my CD-rom drive is hdc```
umount /media/cdrom0
```This unmounted my cd-rom drive at cdrom0, which I couldn't access because of permissions restrictions.```
pmount hdc
```This mounted the CD again. Apparently it mounted to /media/hdc, however I can now fully access and read the CD. Also, the icon appeared on my desktop, so I can run the "copy disc" thing.

The reason I thought unmounting and remounting the cd would work is that I figured I could sudo mount to bypass any permissions. However, it seems sudo wasn't needed. I still have no Idea why this worked, but I'll write down the lines of code in case I ever need it again.

Thanks for the help guys.
-Dave

---

### Post by Dave54 on 2007-01-21
Well, I spoke too soon.

I right-click on the icon, and select "copy disc". On the window that pops up, I select write. Another window pops up with a progress bar, and says "creating image".  After about 10 seconds, it freezes, then closes.

Any Ideas, anyone?
Thanks,
-Dave

---

### Post by Dave54 on 2007-01-21
**THE CD IS STUCK IN MY CD-ROM DRIVE.**

If I right-click the icon and select "eject", I get an error message saying:
"Unable to eject media"
"umount: /dev/hdc mount disagrees with the fstab"
"eject: unmount of `/media/hdc' failed"

If I hit the button to open my CD-rom drive, it won't open.

How do I get it out?

---

### Post by Dave54 on 2007-01-21
I was able to get it out by restarting and ejecting while the bios was printing boot messages.

Annoyed by all these problems with ubuntu seeing a simple CD, I put it in windows (which saw it perfectly) and copied it with nero (again, worked perfectly).

I guess I can't switch completely to linux and get rid of my windows box. If anyone has any suggestions on why ubuntu had so much trouble, I'm listening.

-Dave

---

