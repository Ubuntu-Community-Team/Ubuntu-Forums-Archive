---
title: "File Permissions Issue"
date: 2015-03-18
forum: General Help
---

### Post by lethu-net on 2015-03-18
Hello,
Following an issue with my kubuntu installation (graphics driver libraries problem), I decided to restore a backup of my system that I had made several weeks earlier, but since I didn't want to lose all the settings and other customizations, I copied my home folder but with root permissions because I couldn't mount my backup disk as simple user. So when I copied back the home folder overwriting the backup files I had restored, I got into permission issues (everything was under user: root and group: root and read only, so I have changed the user and group to my username, then changed the permissions of all the files and folders in home to "can read/write, can read, can read" I believe its 644 if I recall correctly. It has been a long time since I used a linux system the hard way, I was running a gentoo installation and knew all these informations but that was many years ago, so now I am not sure anymore if I am doing things correctly or not. Please can you tell me if setting the file permissions this way can pose a security issue ? And if yes, what do you recommend ? Thank you !

Cheers,

---

### Post by nerdtron on 2015-03-18
If after the copy, the files ownership is changed to root, you don't have to change the mode (644) of the files when you restore. You just have to change the owner back to your account.
Something like "sudo chown -R myuser:myuser /home/myuser" should be enough to you control back to your files.

And for premission like the "chmod" command that you did, 644 is the default for files and 755 is the default for directories. These are fine for normal users.

---

### Post by lethu-net on 2015-03-18
> **nerdtron said:**
> If after the copy, the files ownership is changed to root, you don't have to change the mode (644) of the files when you restore. You just have to change the owner back to your account.
Something like "sudo chown -R myuser:myuser /home/myuser" should be enough to you control back to your files.

And for premission like the "chmod" command that you did, 644 is the default for files and 755 is the default for directories. These are fine for normal users.

Thanks for your help, that's all I wanted to know. Thanks again!

Cheers,

---

