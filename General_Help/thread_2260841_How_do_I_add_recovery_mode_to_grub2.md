---
title: "How do I add recovery mode to grub2?"
date: 2015-01-14
forum: General Help
---

### Post by George_Hostler on 2015-01-14
I have an earlier ASUS 701 netbook with 7 inch screen at 1024x600 pixels, 4gb SSD and 512mb RAM. Due to growth changes in a previous Ubuntu based fork I was using, it no longer support my limited system resources.

Thus, I came across Xubuntu 14.04.1 LTS alternate ISO. It installed fine and I have excellent functionality with my limited assets machine. (This earlier netbook has a motherboard hardware bug where I can't use SD cards or USB thumb drives for basic Linux partitions for increased OS storage. Even USB and SD Card ISO's don't work, must use a USB DVD.) I am very happy with it, now I have an up-to-date operating system.

There is one exception, Xubuntu 14.04 grub2 boot menu does not offer recovery mode. Advance menu only shows Linux images for boot. (Yes, I know about the hit shift key to display, and have changed /etc/default/grub to enable menu display, updating grub.)

How do I add recovery mode to Xubuntu?

---

### Post by deadflowr on 2015-01-14
So what does /etc/default/grub show?
Is the line for
```
#GRUB_DISABLE_RECOVERY="true"
```
have an# or does it look like
```
GRUB_DISABLE_RECOVERY="true"
```

---

### Post by George_Hostler on 2015-01-14
The grub disable recovery line is commented out. To be sure to force it, I uncommented and set it to "false". After update-grub either way, there still is no recovery menu item.

---

### Post by George_Hostler on 2015-01-14
This is not solved, but I mistakenly identified this problem with Xubuntu, when it is Lubuntu that I installed. Therefore, I am reposting it identified as Lubuntu.

---

### Post by George_Hostler on 2015-01-14
In thread [http://ubuntuforums.org/showthread.php?t=2260841](http://ubuntuforums.org/showthread.php?t=2260841) I mentioned about this problem, but I was incorrect. It is not Xubuntu but in Lubuntu.

I would like to know how to add recovery mode. Apparently the designers left this out. Even uncommenting the line in /etc/default/grub, ***#GRUB_DISABLE_RECOVERY="true"***, changing ***"true"*** to ***"false" ***and then ***update-grub*** does not insert a recovery entry in the grub boot menu or submenu.

I'm thinking that there may have been a reason related to keeping this distribution light.

Reason for this is I find recovery mode very useful for elemental tasks and fixing things outside the GUI. Over time I'd probably figure this out, but figure there must be some guru's out there who have already tackled this problem and give me a head jump on things.

Thanks in advance, George

---

### Post by efflandt on 2015-01-14
If all else fails and you want to boot without X running, hit **e** during grub menu, replace **quiet splash** and whatever follows in that line with **text** instead, then boot. That will display boot messages and boot into a text console. That is only temporary for that boot, it does not change anything in the stored grub menu.

---

### Post by grahammechanical on 2015-01-14
There was no need to open a new thread. Certain parts of Ubuntu and its flavours are the same. Background colours may be different. That is about all. So, you installed this Lubuntu from the alternate CD. Correct? Did you install Friendly Recovery? It is a special set of scripts.

Search for friendly recovery in the software centre or whatever it is called in Lubuntu and see if Friendly Recovery is installed. The scripts should be found at /lib/recovery-mode/

Regards.

---

### Post by Bucky Ball on 2015-01-14
*Thread moved to **General Help**.*

*Threads merged. *

Same issue, same grub, same fix. ;)

If you would like to remove the 'solved', please 'unsolve' the thread from Thread Tools. Good luck.

---

### Post by George_Hostler on 2015-01-15
> **grahammechanical said:**
> There was no need to open a new thread.  Certain parts of Ubuntu and its flavours are the same. Background  colours may be different. That is about all. So, you installed this  Lubuntu from the alternate CD. Correct? Did you install Friendly  Recovery? It is a special set of scripts. Search for friendly recovery in the software centre or whatever it is  called in Lubuntu and see if Friendly Recovery is installed. The scripts  should be found at /lib/recovery-mode/ Regards.

grahammechanical, I am new to your forums and unfamiliar with how you folks operate. Regarding this problem, I reinstalled, it is now gone. I don't know what happened. One thing that went wrong is that my two 8mb bios partitions somehow got overwritten during the previous install. Anyway, problem is solved, sorry for troubling you all.

---

