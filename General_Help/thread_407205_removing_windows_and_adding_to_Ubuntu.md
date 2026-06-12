---
title: "removing windows and adding to Ubuntu"
date: 2007-04-11
forum: General Help
---

### Post by mikawber on 2007-04-11
I want to remove my existing Windows partition and turn it into a /home directory. How do I go about doing this? Can I do it by being booted in Ubuntu or should I run a live cd? A tutorial would also be very helpful. Thanks!

---

### Post by arya6000 on 2007-04-11
I'm not sure if I fully understand your question.

Are you asking how to install Ubuntu over your windows, and change from your windows filesystem to Linux's filesystem system?

If thats the case, just back up your files that you would need from your computer like important documents, images, etc

than just put in the Ubuntu disk, and once you click install, the process is only requires a couple of clicks

---

### Post by mikawber on 2007-04-11
sorry if I wasn't clear...I already have Edgy installed. I also have Vista installed but I hardly use it so I was going to delete the Vista partition and make it into a /home. I just don't know how to go about doing it. Do I need a live cd?

---

### Post by dreadlord_chris on 2007-04-11
> **mikawber said:**
> I want to remove my existing Windows partition and turn it into a /home directory. How do I go about doing this? Can I do it by being booted in Ubuntu or should I run a live cd? A tutorial would also be very helpful. Thanks!

Just got rid of Windows myself :o 

Use GParted to delete your NTFS partition and create a new ext3 partition for /home.
The follow the guide [here]("http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/") to move your /home to it's new partition....

---

### Post by mikawber on 2007-04-11
thanks I'll take a look at it this weekend. I was wondering if anybody knew of any good replacements for AnyDVD and CloneDVD. This is the only thing holding me back from leaving Windows 100%. I can live with AmaroK instead of iTunes but I need a replacement for AnyDVD and CloneDVD that will do just as good of a job. Is that possible?

---

