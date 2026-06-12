---
title: "NTFS partition not mounting if Windows is shut down; fine if it reboots?!"
date: 2016-03-17
forum: General Help
---

### Post by Cleaver on 2016-03-17
Hi,

I have a NTFS partition separate from my Windows 10 and several Linux partitions, which holds all of my media/documents. It has no problem mounting/automounting on startup on Ubuntu if I previously *rebooted* windows to exit it, but every time I shut Windows down entirely, it fails to do so, and I have go to into Windows and reboot it to fix this. This only started happening since I upgraded to 15.10 in the last 7-10 days from 15.04.

Any idea why it'd only work OK when I reboot? Thanks!

---

### Post by mastablasta on 2016-03-17
you are porbably hibernating windows or have fast boot or whatever it is called, turned on in windows.

---

### Post by Cleaver on 2016-03-19
You were absolutely right. I think I heard of this concept before, but forgot it. Thanks!

---

### Post by oldfred on 2016-03-19
And Windows updates may keep turning it on, as you would not want Windows to be slower booting.

 Fast Startup off (always on hibernation)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold)
More explanation of NTFS driver & Windows hibernation
[http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation](http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation)
[http://mjg59.dreamwidth.org/24869.html](http://mjg59.dreamwidth.org/24869.html)

---

