---
title: "Startup problem, yes or no?"
date: 2017-03-23
forum: General Help
---

### Post by AbleTassie on 2017-03-23
Recently I did a clean install of Lubuntu 16.04.2 after checking that the MD5 and SHA256 Sums were correct. Now I get a screen on every boot that says about the following: 
 
 **/dev/sda1: clean, 184181/303334976 files, 4052381/121312000 blocks**

The numbers may vary slightly, but the message is essentially the same always.

From what I can gather by attempting to search this out, it appears that fsck is running on every boot. I checked the time to boot up and it appears to be about 45 seconds.

This did not occur with Lubuntu 14.04. 

Is the above a problem or not? 

Thanks,

Able

---

### Post by mörgæs on 2017-03-23
I see the same on all of my Lubuntu installs, both on new(ish) and old hardware. I take it as a benefit that the file system is checked, and except from the small delay I have not experienced any drawbacks.

---

### Post by Autodave on 2017-03-23
Same here on Xubuntu: 13 machines.

---

### Post by vasa1 on 2017-03-23
Same here. Just one laptop to talk of. It's running Lubuntu 16.04.

---

### Post by RobGoss on 2017-03-23
Same here on all my machines I just assumed it's part of the start up procedure. I don't think it anything to worry about

---

### Post by ajgreeny on 2017-03-23
As mentioned above it is a message saying that the filesystem is clean. This is always quickly checked at startup, and if needed a full fliesystem check (fsck) would be run in order to correct any problems, so don't worry about it.

If it really bothers you and you don't want to see it, you can edit the /etc/default/grub file as root and add fastboot to the GRUB_CMDLNE_LINUX_DEFAULT line so it reads
```
GRUB_CMDLINE_LINUX_DEFAULT="fastboot quiet splash"
```
The check will still be made but you just will not see that message; it's your choice.

---

### Post by AbleTassie on 2017-03-23
Thank you to everybody. I will mark this thread as solved.

A.

---

