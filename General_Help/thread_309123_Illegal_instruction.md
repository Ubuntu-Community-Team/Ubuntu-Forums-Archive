---
title: "Illegal instruction"
date: 2006-11-29
forum: General Help
---

### Post by Ramses de Norre on 2006-11-29
Does anyone know when exactly you get an illegal instruction error?
Yesterday my machine suddenly gave me such an error on almost every command.. I had to use SysRq to reboot it because I wasn't able to run init neither..
The logs look clean so I have no idea what happened..

---

### Post by az on 2006-11-29
> **Ramses de Norre said:**
> Does anyone know when exactly you get an illegal instruction error?
Yesterday my machine suddenly gave me such an error on almost every command.. I had to use SysRq to reboot it because I wasn't able to run init neither..
The logs look clean so I have no idea what happened..

Is you box overheating?  Maybe run a memtest and a badblocks, too?

Do you remember what was running when you stared to get the error?  Can you reproduce it?

---

### Post by Ramses de Norre on 2006-11-29
I did "**sudo vi /etc/fstab**" when I first got it, I then tried to find out what was causing it and ran just vi, which worked, then sudo -K which worked too and then sudo -v and that gave me an illegal instruction again. So I thought I'll restart X, maybe there went something wrong causing segfaults or something.. So I tried to log off but the button didn't respond.. I went to a tty and did **sudo /etc/init.d/gdm restart** and I got the illegal instruction error again.. I then went back to X but nothing responded.. Although amarok kept on playing. And every command in a tty gave me the same error.

My last resort was SysRq to sync-remount-reboot..
Heat isn't really a possibility I think, I'm on a desktop, never had heat problems before, wasn't doing anything cpu intensive, the temperature here was rather low and my machine is now up for 6h already so it most likely should have happened again then.

And I'll run a memtest the next time I reboot, I hope my sticks are ok..

How do I check for badblocks? That's with fsck no? I'll read the man pages and do a check.

Thanks for your thoughts!;)

EDIT: at the moment only firefox amarok and amsn were running I think, and I wouldn't know how to reproduce it because I don't know what it exactly is or why it appeared...

---

### Post by taurus on 2006-11-29
So the last thing you ran before all this trouble began was editing your /etc/fstab!!!  If that's the case, what does your /etc/fstab look like now?

---

### Post by Ramses de Norre on 2006-11-29
No, I tried to edit it but that gave me the error, so I just typed in "sudo vi /etc/fstab" but instead of opening vi I got one line printed "Illegal instruction" and then the prompt again. I never got to open my fstab.

And if fstab was the problem the errors shouldn't have appeared until I remounted my drives..

---

### Post by az on 2006-11-29
> **Ramses de Norre said:**
> My last resort was SysRq to sync-remount-reboot..
Heat isn't really a possibility I think, I'm on a desktop, never had heat problems before, wasn't doing anything cpu intensive, the temperature here was rather low and my machine is now up for 6h already so it most likely should have happened again then.

It does seem to be more likely a hardware problem than something on the OS-level.

And you certainly can have overheating problem with desktop PCs.  Most of the time, the cpu fan gets slowed down by an accumulation of dust.  The symptom is usually random errors such as you describe.



> **Ramses de Norre said:**
> 


How do I check for badblocks? That's with fsck no? I'll read the man pages and do a check.

...

sudo badblocks /dev/hda1

There are switches for doing a read/write test, but you don't want to do that on your root partition....   By default, it is only a nondestructive test.  

Fsck checks the filesystem.  Badblocks checks the disk medium.

---

### Post by Ramses de Norre on 2006-11-29
> **azz said:**
> And you certainly can have overheating problem with desktop PCs.  Most of the time, the cpu fan gets slowed down by an accumulation of dust.  The symptom is usually random errors such as you describe.

Yes, but much less change than with a notebook, no? And the problem is that lm-sensors doesn't detect my cpu sensor (it's an athlon 64 3700+), maybe I'll need to boot windows sometimes and look at my temperatures for a while..

> **azz said:**
> 
sudo badblocks /dev/hda1

There are switches for doing a read/write test, but you don't want to do that on your root partition....   By default, it is only a nondestructive test.  

Fsck checks the filesystem.  Badblocks checks the disk medium.

I'll run the badblocks too (and isn't e2fsck -c safer?).

---

### Post by az on 2006-11-29
> **Ramses de Norre said:**
> Yes, but much less change than with a notebook, no? And the problem is that lm-sensors doesn't detect my cpu sensor (it's an athlon 64 3700+), maybe I'll need to boot windows sometimes and look at my temperatures for a while..

I have fixed a number of "broken" desktop computers where the problem was overheating.

> **Ramses de Norre said:**
> 

I'll run the badblocks too (and isn't e2fsck -c safer?).

Well, badblocks is very safe.  The thing is that if the filesystem is not using a bad block at the time, you won't catch the problem using fsck.  And vice versa, not every corrupted filesystem is due to a disk failure.

---

### Post by Ramses de Norre on 2006-12-01
I just ran memtest the whole afternoon and it went through 15 passes without a single error so I guess my RAM is ok. I do get segfaults sometimes though, with programs like aptitude and such..

I still need to run badblocks. And maybe I'll go through the case with the vacuum cleaner one of these days to get the dust out of the fans and heatsinks.

---

### Post by az on 2006-12-01
> **Ramses de Norre said:**
> I just ran memtest the whole afternoon and it went through 15 passes without a single error so I guess my RAM is ok. I do get segfaults sometimes though, with programs like aptitude and such..

I still need to run badblocks. And maybe I'll go through the case with the vacuum cleaner one of these days to get the dust out of the fans and heatsinks.

Can you try running from the live cd for a while ( a few hours) to see if this is a software problem or a hardware problem?  (running from the live cd will be like running with a different copy of the software on your HD).

---

