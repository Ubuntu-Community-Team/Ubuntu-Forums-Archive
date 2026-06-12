---
title: "Gutsy freezing and fsck problems"
date: 2008-01-16
forum: General Help
---

### Post by Najmudin on 2008-01-16
Hi

I have gutsy installed in one of my hard disks since it was released and it was fine.
yesterday night the screen suddenly freeze and i couldn't do anything except hard restart
after restarting i get the automatic disk checking , the checking failed saying there is an error on sdc1 disk and asked me to do a manual "fsck" checking so I did the manual checking and log in to Ubuntu just for 15 minutes and the screen freeze again , i did the same operation again using a live CD but without benefit , i couldn't log in .:(
Today i decided to do a reinstall losing all my data , after finishing the reinstalling of Ubuntu every thing was seem to be fine about 25 minutes and the screen freeze again :mad: 
so i give up and I'm now writing to you from the xp partition , is this problem to do with gutsy update or the sdc1 hard disk  is damaged or a memory problem or what i 'm completely confused :confused:
I hope some one can help.

---

### Post by danwood76 on 2008-01-16
It sounds like a hard disk error.
It cant be an updates fault if you did a fresh install and you get the same symptoms.

Is your XP install on a different disk?

regards,
Danny

---

### Post by Najmudin on 2008-01-16
> **danwood76 said:**
> It sounds like a hard disk error.
It cant be an updates fault if you did a fresh install and you get the same symptoms.

Is your XP install on a different disk?

regards,
Danny

Yes

---

### Post by frodon on 2008-01-16
I would backup your datas from this disk in right now, this looks like the first sign of a dieing disk.
It can take some months but when you get disk errors on a regular basis on a system used to work without any problems it is most often hardware issue.

Consider changing your disk or use it in the spirit that it will soon die.

---

### Post by Najmudin on 2008-01-16
> **frodon said:**
> I would backup your datas from this disk in right now, this looks like the first sign of a dieing disk.
It can take some months but when you get disk errors on a regular basis on a system used to work without any problems it is most often hardware issue.

Consider changing your disk or use it in the spirit that it will soon die.

Bad news for me , it was the newest hard disk from my 3 hard disks and now its dieing :(
anyway thanks for you replay .

---

### Post by frodon on 2008-01-16
I had the problem 2 times with 2 maxtor disks which died after a years, to be exact right after the end of the warranty so now i don't buy maxtor disks anymore.
They are bad series from time to time so you may just be unlucky.

BTW, check your log in your system log viewer and check for errors in syslog, message and kern.log you may find errors from your disk here. This would confirm even more the harddrive issue.

---

### Post by SparcMan on 2008-02-14
> **Najmudin said:**
> Hi

I have gutsy installed in one of my hard disks since it was released and it was fine.
yesterday night the screen suddenly freeze and i couldn't do anything except hard restart
after restarting i get the automatic disk checking , the checking failed saying there is an error on sdc1 disk and asked me to do a manual "fsck" checking so I did the manual checking and log in to Ubuntu just for 15 minutes and the screen freeze again , i did the same operation again using a live CD but without benefit , i couldn't log in .:(
Today i decided to do a reinstall losing all my data , after finishing the reinstalling of Ubuntu every thing was seem to be fine about 25 minutes and the screen freeze again :mad: 
so i give up and I'm now writing to you from the xp partition , is this problem to do with gutsy update or the sdc1 hard disk  is damaged or a memory problem or what i 'm completely confused :confused:
I hope some one can help.

I've been suffering similar touture lately.
I have a dual boot with Vista (this is a laptop that was factory installed with Vista and I resized during initial install).
Twice now while installing software via Synaptic, the system froze and I had to power off cold.
The first time, I dumbly ran fsck on the partition from multiuser mode and it chewed up the partition beyond all repair and I had to reinstall.
The second time it happened, I booted straight to Single user mode and ran fsck from there, but the results were the same - trashed file system and reinstall.
If the system crashes during software installation again, I'm going to only run fsck from the boot CD, but I'm going to have to give up this release of Ubuntu if the kills the system again.

SparcMan

---

