---
title: "My desktop won't boot."
date: 2019-12-10
forum: General Help
---

### Post by joey1990 on 2019-12-10
My desktop has been crashing for a while now. Usually a restart fixes it. But now it won't boot. It's done this before and I've had to reinstall Ubuntu. But I'm wondering is there another fix. 
I've attached a photo of the errors.

---

### Post by ajgreeny on 2019-12-10
Seems you have a filesystem problem so as the screenshot says you should run fsck manually.
It would also be useful to see what hardware you're using so please tell us that.

Boot to a live system such as a DVD or USB that you used initially to install the system.
Open a terminal in the live system and run ***sudo blkid*** to figure out which is your root partition, probably /dev/sda1 if using an MBR system, or maybe /dev/sda2 if a UEFI system.
Once you know the root partition, still in the live booted system, run command ```
sudo e2fsck /dev/sda#
```using the root partition device, of course.

The output from running that command may tell you what is wrong and offer to correct it for you; come back again with the output if you're not sure.

Please use **Code-Tags** for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted.
See my signature below for a **How-to**

---

### Post by yancek on 2019-12-10
The image you posted shows the root fillesystem which needs checking is on /dev/sdb2 and needs a manual check.  The image you posted also indicates not to use the -a and -p options.  THe link below explains briefly, using fsck and what the various options are.

[https://www.linode.com/docs/quick-answers/linux/how-to-use-fsck-to-fix-disk-problems/](https://www.linode.com/docs/quick-answers/linux/how-to-use-fsck-to-fix-disk-problems/)

---

### Post by ajgreeny on 2019-12-10
Thanks for the extra info yancek; unfortunately I couldn't read the text on the image on my small screen at the time, but your clarification should be a help for [COLOR="#FF0000"]joey1990[/COLOR].

---

### Post by joey1990 on 2019-12-12
Thanks for the help guys. Going to tackle this this morning and try get it sorted.

---

### Post by joey1990 on 2019-12-12
Okay guys I've fixed it.  Cheers for your help. I've never had to use fsck before.

---

