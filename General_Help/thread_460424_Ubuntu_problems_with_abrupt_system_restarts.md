---
title: "Ubuntu problems with abrupt system restarts"
date: 2007-05-31
forum: General Help
---

### Post by Sushubh on 2007-05-31
I have tried installing Ubuntu using Wubi two times and it works fine for me. Except for when the system restarts due to massive power fluctuations in my region.

I have a decent power backup solution but it still manages to fail sometimes restarting the system. 

As a result I have crashed my Ubuntu installation two times. The latest one happened today and here is the result:

[[IMG]http://farm1.static.flickr.com/196/523825551_8d8b26d9aa.jpg[/IMG]]("http://flickr.com/photo_zoom.gne?id=523825551&size=o")

My question is… I am ready to have a real installation of Ubuntu on my system. Dual boot of course for the time being. Would a regular installation suffer similar problems in case of abrupt system restarts? How do I fix a situation like this?

In case of Wubi, nothing happens to my regular OS. But if I have a regular install of Ubuntu, I might end up having a broken boot manager! 

Please help.

---

### Post by Sushubh on 2007-05-31
Wubi should seriously give an option to repair an existing installation!

---

### Post by ago on 2007-05-31
Wubi is more vulnerable to a hard reboot than a real installation for various reasons (we have not 1 but 2 nested file systems). Hard reboots are never recommended but in my own experienced I never had a problem with a real installation under ext3. Linux can recover ext3 problems often but  in the case of wubi you may also have to fix ntfs and that has to be done with windows tools.

---

### Post by Sushubh on 2007-05-31
so you suggest i should go ahead with a proper installation rather than a third time wubi based installation?

is my current installation recoverable? coz that would save me a lot of effort!

and of course i dont do hard reboots on purpose :)

---

### Post by ago on 2007-05-31
If power is an issue, you should consider a normal installation. Also if you keep the image file around, you can mount/recover that from within linux.

---

### Post by steve.horsley on 2007-05-31
Sorry, but I doubt if your current installation is easily recoverable. The problem is likely corruption of the NTFS file that holds the disk image. This could easily include corruption of the journal that Ubuntu thought it had written to the disk to protect against sudden resets.

I agree with ago that a real installation is less likely to get corrupted like that, but it is still possible of course, so regular backups should be part of your way of life.

---

