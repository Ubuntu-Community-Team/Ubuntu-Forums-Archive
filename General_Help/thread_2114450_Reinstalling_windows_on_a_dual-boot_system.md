---
title: "Reinstalling windows on a dual-boot system"
date: 2013-02-10
forum: General Help
---

### Post by Werne on 2013-02-10
Ok, I've got a problem I could use help with. I've spent 4 hours googling for a solution and found absolutely nothing. And I'm not sure if this was asked before so sorry if I'm posting something that already exists. Anyway, here it goes...

I've got a XP/Ubuntu 12.10 dual-boot, last week I got a Win7 disc so I decided to replace my old XP with Win7 x64. I use Ubuntu for more-or-less everything except 3D modeling for which I need Windows.

And here's the problem, XP is on an active partition and as far as I understand, if I remove XP and install Win7 I won't be able to boot into Ubuntu anymore because installing Win7 will change the Master Boot Record.

I want to keep Ubuntu intact and only replace XP with Win7, I know it should be possible but I don't know how to achieve that. All I've found so far is that I should make a backup of the MBR, restore it after I install Win7, boot into Ubuntu and set GRUB to boot Windows but I can't find any details or instructions about how to do that anywhere.

So I'd really appreciate some help with this.

---

### Post by kc1di on 2013-02-10
No problem go ahead and install win 7 and replace xp.
then follow these steps to re-install grub2 to the MBR then all will be back to normal as long as you don't allow win 7 to format the ubuntu partitions you will be fine. 

Just follow the instruction on this [page]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") and all should be well. 

you may want to go [here]("https://help.ubuntu.com/community/Boot-Repair") and download a copy of boot-repair first.

Good luck :)

---

### Post by Werne on 2013-02-10
Thanks, the instructions are pretty simple, though now I wonder why I haven't found them myself.

In any way, problem solved, thanks again. :D

---

### Post by kc1di on 2013-02-10
> **Werne said:**
> Thanks, the instructions are pretty simple, though now I wonder why I haven't found them myself.

In any way, problem solved, thanks again. :D

Your Welcome enjoy :p

---

