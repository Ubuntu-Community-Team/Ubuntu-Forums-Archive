---
title: "[SOLVED] No hd anymore"
date: 2008-02-14
forum: General Help
---

### Post by alejo0823 on 2008-02-14
Hi
2 days ago I was doing some multitasking test to see how my pc does in ubuntu, it did pretty good but when I was closing the windows and finishing the test the systems locks up, nothing worked so I press the reset button. yesterday I couldn't see my hd its like ubuntu cant mount em I see the hard drives as empty files and have the same free space as the ubuntu partition. I don't know what to do, i tried to put auto in the fstab file to see if that was the problem but it did nothing. 
thanks for any help, I don't want to reinstall again I am really happy with my current configuration.

---

### Post by Borbus on 2008-02-14
What type of filesystem is it?

---

### Post by alejo0823 on 2008-02-14
3 NTFS and the Linux partition, there are 4 partitions and 3 hard drives

---

### Post by Borbus on 2008-02-14
Why are you using NTFS with Linux? You should get rid of those.

Sometimes NTFS partitions become "locked". Try mounting your partitions manually with mount. IF they are in your fstab it should be enough to type:

sudo mount /dev/sda1

Replacing sda1 with the name of the parition you need to mount. If it says something about it being locked, you have to add -o force to that command.

---

### Post by alejo0823 on 2008-02-14
I use NTFS cuz I'm dual booting vista and ubuntu, and I like to listen music while working in both OS.
I don't know why but the hd are now working I didn't do anything I guess it comes and goes if it does it again I'm gona try mounting like you said
thanks for the help.

---

