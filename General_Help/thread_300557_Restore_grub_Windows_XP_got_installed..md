---
title: "Restore grub? Windows XP got installed."
date: 2006-11-15
forum: General Help
---

### Post by UltraSonicSite on 2006-11-15
And it killed my beautiful GRUB menu! Oh how I wubbed that menu! And now it's gone.

A quick google search required me to have a floppy disk. My floppy drive does not work ._.

Any other solutions?

Thank you very much in advance; Cannot wait to upgrade Ubuntu!

---

### Post by UltraSonicSite on 2006-11-15
Crap, the forum only gives complicated ways to restore it ._.

---

### Post by pissedoffdude on 2006-11-15
you should see this thread [http://www.ubuntuforums.org/showthread.php?t=24113&highlight=grub]("http://www.ubuntuforums.org/showthread.php?t=24113&highlight=grub")

---

### Post by scrooge_74 on 2006-11-15
Try using your Live CD and then you can reconfigure your GRUB

---

### Post by noynac on 2006-11-15
Have you looked at this Ubuntu documentation:

[http://tinyurl.com/y53law](http://tinyurl.com/y53law)

or

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?highlight=(grub-install)#head-bf3232f10ddf1b078de064622ccbb25225cdb3c0](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?highlight=(grub-install)#head-bf3232f10ddf1b078de064622ccbb25225cdb3c0)

---

### Post by UltraSonicSite on 2006-11-15
[IMG]http://img.photobucket.com/albums/v64/ultrasonicsite/Screenshot-2.jpg[/IMG]

Are my options set correctly?
[IMG]http://img.photobucket.com/albums/v64/ultrasonicsite/Screenshot2.jpg[/IMG]

---

### Post by UltraSonicSite on 2006-11-15
Yes no? I believe it's wrong but don't know exactely how to set it up correctly.

---

### Post by UltraSonicSite on 2006-11-15
1. Pop in the Live CD, boot from it until you reach the desktop.[img]http://aitdomains.com/images/check.gif[/img]

2. Open a terminal window or switch to a tty (Ctrl + Alt + F1).[img]http://aitdomains.com/images/check.gif[/img]

3. Type "sudo grub"[img]http://aitdomains.com/images/check.gif[/img]

4. Type "root (hd0,6)", or whatever your harddisk + boot partition numbers are (my /boot is at /dev/sda7, which translates to hd0,6 for grub).[img]http://www.dshs.state.tx.us/kids/ems/redx.gif[/img]

Which root is the one I should put? I assume it is not hd1 for me because thats NTSF, which I believe is Windows only. 

5. Type "setup (hd0)", ot whatever your harddisk nr is.[img]http://www.dshs.state.tx.us/kids/ems/redx.gif[/img]

6. Quit grub by typing "quit".[img]http://www.dshs.state.tx.us/kids/ems/redx.gif[/img]

7. Reboot. [img]http://www.dshs.state.tx.us/kids/ems/redx.gif[/img]

---

### Post by UltraSonicSite on 2006-11-15
1. Boot your computer up with Ubunto CD **-Got it**
2. Go through all the process until you reech "[!!!] Disk Partition" **-Got it**
3. Select Manual Partition **-Got it**
4. Mount your appropriate linux partions **-Wtf?**

/
/boot
swap
..... 

5. DO NOT FORMAT THEM. **-Get it**
6. Finish the manual partition **-Get it**
7. Say "Yes" when it asks you to save the changes **-Get it**
8. It will give you errors saying that "the system couldn't install ....." after that **-Get it**
9. Ignore them, keep select "continue" until you get back to the Ubuntu installation menu **-Get it**
10. Jump to "Install Grub ...." **-Why not just go straight to this menu instead of doing the above?**
11. Once it is finished, just restart your computer **-Get it**

Good luck!. **-Need it**

---

### Post by organica on 2006-11-15
> **UltraSonicSite said:**
> 1. Pop in the Live CD, boot from it until you reach the desktop.[img]http://aitdomains.com/images/check.gif[/img]

2. Open a terminal window or switch to a tty (Ctrl + Alt + F1).[img]http://aitdomains.com/images/check.gif[/img]

3. Type "sudo grub"[img]http://aitdomains.com/images/check.gif[/img]

4. Type "root (hd0,6)", or whatever your harddisk + boot partition numbers are (my /boot is at /dev/sda7, which translates to hd0,6 for grub).[img]http://www.dshs.state.tx.us/kids/ems/redx.gif[/img]

Which root is the one I should put? I assume it is not hd1 for me because thats NTSF, which I believe is Windows only. 

5. Type "setup (hd0)", ot whatever your harddisk nr is.[img]http://www.dshs.state.tx.us/kids/ems/redx.gif[/img]

6. Quit grub by typing "quit".[img]http://www.dshs.state.tx.us/kids/ems/redx.gif[/img]

7. Reboot. [img]http://www.dshs.state.tx.us/kids/ems/redx.gif[/img]

4. your root should be at hda3 which is root (hd0,2)
5. setup (hd0)
6. quit
7. reboot

---

### Post by confused57 on 2006-11-16
Here's a how to restore grub, using the live cd:

[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

---

### Post by UltraSonicSite on 2006-11-16
Thank you, that worked flawlessly.

---

