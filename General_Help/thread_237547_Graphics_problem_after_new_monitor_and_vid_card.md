---
title: "Graphics problem after new monitor and vid card"
date: 2006-08-16
forum: General Help
---

### Post by johnk93 on 2006-08-16
Hi everyone,
I recently installed Ubuntu, dual booting with XP.  It took me a while, but I finally got GRUB loading right.  This required a fresh install of Windows, but that's OK.  Dual booting was going good.  Then I stopped using Ubuntu for a few weeks while I got windows back to how it originally was.  I also installed a new monitor (20.1" wide from my old 17"CRT) and graphics card (different brand of 7800GT). 

Now when I try to load into Ubuntu, I have graphics problems.  It loads through the first loading list, but at the splash screen everything is "messed up", meaning the graphics and text are not even legible.  It just looks like artifacts and tearing.  It stops there, and doesn't actually load into my Ubuntu desktop.  I assume this is because when I installed Ubuntu, I didn't select the widescreen resolution options, but I'm brand new to Linux and don't really know what the problem is.  (BTW, windows still loads fine)

Is there any way to correct the problem without re-installing Ubuntu?  I'm hesitant to do this, because I'm afraid I'll make another mistake and have to re-install windows again.  (I have XP and Ubuntu on differnt partitions of the same hd)

Thanks!

John

---

### Post by foolsh on 2006-08-16
i personally dont know how to fix the screen problem but i do know that you can install ubuntu as many times as you like, and it *should* not mess up your xp install. Aslong as you do the partitioning correctly taking note which partitions ubuntu wants to use. i've reinstalled ubuntu three times last month, only because im really really paraniod, but still ontop of all that i can boot xp with no problems

---

### Post by orb9220 on 2006-08-16
Try

sudo dpkg-reconfigure xserver-xorg

in a term

---

### Post by johnk93 on 2006-08-16
Orb,
I'm frightened by your avatar:) 

Since I can't get into ubuntu to the terminal, do I load in recovery mode, then type the command? 

I'll try when I get home...thanks.

John

---

### Post by greg m on 2006-08-16
i had to fix mine in recovery mode.

---

### Post by tommcd on 2006-08-16
Yes recovery mode will work for that. At the end, when it gets to the part about configuring your monitor, choose "medium" and select the resolutions you want with the space bar. You will then have to reinstall the nvidia driver. Good luck.

---

