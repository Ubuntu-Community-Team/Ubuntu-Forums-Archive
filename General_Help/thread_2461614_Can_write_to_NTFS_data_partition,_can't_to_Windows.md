---
title: "Can write to NTFS data partition, can't to Windows OS partition"
date: 2021-05-04
forum: General Help
---

### Post by spectatorx on 2021-05-04
I have an odd issue. I'm dualbooting windows 10 and ubuntu 20.04 (budgie flavor to be specific but i assume in this case it doesn't matter), using few hdds, both OSes installed on the same hdd. NTFS partitions mounting works fine, gives no errors. I'm able to read on all ntfs partitions but... write only on all DATA ntfs partitions and i'm unable to write into Windows OS ntfs partition. I've never faced that issue before and i'm dual booting for many years now. Obviously fast startup and hibernation are disabled in windows power settings also windows was closed properly, no power outage nor rebooting from pc case button.

In attachment i've added a screenshot from Disks tool.

[ATTACH=CONFIG]288423[/ATTACH]

There is no error messages, i just have no option to do any write operations on that one partition while on others can.

---

### Post by oldfred on 2021-05-04
Well, generally better not to write into the Windows system partition and use a shared NTFS partition for data.
Back when I used XP, I often fully corrupted it by doing something I should not. The Linux NTFS driver exposes all the hidden files & folders that Windows hides to try to prevent users from damaging system.

Double check Windows fast start up  which sets hibernation flag.
Windows will turn fast start up back on with updates, so whenever you cannot correctly see NTFS, recheck setting. And you may not always see that updates occurred.

---

### Post by Impavidus on 2021-05-05
Indeed, better not write to the Windows OS partition, unless you want to fix Windows and really know what you're doing.

If you want to understand the issue, how do you mount the Windows partition?

---

### Post by spectatorx on 2021-05-05
Not from terminal, with gui, from DE, just clicking on icon of the drive. Seems like the drive is for some reason being mounted in read-only mode and this partition only.

Ye, i know risks of mounting OS partitions and i am aware of what i am doing. That's kinda like with chmod 777: it is not recommended but everybody uses it if this is the quickest and good enough solution to problems which require quick and effective solving.

---

### Post by Impavidus on 2021-05-06
You can use the **findmnt** command to get the mount options of that partition.

BTW, I never use chmod 777. I may have used it once or twice when I was a complete beginner.

---

