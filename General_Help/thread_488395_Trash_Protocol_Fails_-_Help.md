---
title: "Trash Protocol Fails - Help?"
date: 2007-06-30
forum: General Help
---

### Post by Gary.M on 2007-06-30
Under Kubuntu...

I have twice this week struck this problem. Logout / shutdown.  Start up the next day and login to be told the trash protocol has failed... The system is then unstable.

When this happened a few days ago I thought I'd fixed it, as it seemed to be reported as a Kde error, by adding the gnome desktop and messing around with the delete function in there. It seemed to bypass the trash bin without being upset, and offered only "delete" while things weren't right. It was still unstable though.

Can anyone please background what the trash protocol depends on. I have tried deleting the .trash folder, but that is recreated, empty, and the problem still persists.

Thanks in advance...

---

### Post by Gary.M on 2007-06-30
Further to this, on a hunch I've commented out all lines in Fstab except those that mount root and home. Now it starts OK. So on one of the other volumes exists something that is causing the trash protocol to die. Yet the .trash folder is in my home folder... which is still mounted.

Ideas?

---

### Post by tgbrowning on 2007-06-30
If commenting out lines in fstab fixed, couldn't you just go back, add one line at a time and see what works and what causes the problem. Pin it down to one particular mounting? 

Trouble is, I only have a vague idea what the trash protocol is or does. 

Browning>>>

---

### Post by Gary.M on 2007-06-30
Yeah, thats my next move today when I get a few minutes free... but when I find which volume it is I need to know what to look for on that to clear the problem...

---

### Post by Gary.M on 2007-07-01
Ok, so problem solved...

I found one volume was the cause of the trash protocol dying at login. When I uncommented that line in fstab the problem returned. So with it unmounted I did fsck -f on it, errors were found and corrected, and then all worked. It was an Ext3 volume that mounts to a folder in my home folder.

It seems if there are unremoved items in the trash bin and the drive they're on gets some sort of corruption, this problem will arise.

How come Ext3 is this fragile? This has happened twice in a week. I think the first time it was actually corrected because at boot the offending volume was checked and corrected because its number had come up. I didn't reallise at the time that was what had cured it.

I am using Dolphin in Kubuntu. Any possibility it might be the culprit?

By the way, how do you unmount from the console? My system says there is no such command as unmount, yet the online manual for mount refers to the unmount command...???

---

### Post by tgbrowning on 2007-07-01
The command you want is umount, NOT unmount. 

No, I have NO idea why the "n" is missing.

Try man umount in terminal mode to see exactly what and how the command works.

Browning>>>

---

### Post by Gary.M on 2007-07-09
Ok. It appears the problem may have arisen because of the IFS driver installed in my WinXP partition to allow access to the Ext3 shared volumes. The trash protocol failure each time was associated with an Ext3 volume problem that was fixed subsequently by fsck. Each time this was after accessing the Ext3 volume from Windows.

---

