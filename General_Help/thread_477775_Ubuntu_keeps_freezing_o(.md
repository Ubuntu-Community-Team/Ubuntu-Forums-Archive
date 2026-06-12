---
title: "Ubuntu keeps freezing :o("
date: 2007-06-18
forum: General Help
---

### Post by Opti on 2007-06-18
My Ubuntu just freezes every so often. The freezes happen either 1 hour after a reboot or it could take up to 2 days before it hangs up. When it freezes up both mouse and keyboard is diabled.
I have checked in syslog, butI can't find any errors in there.
I'm using the latest version of Ubuntu.

---

### Post by phr0ze on 2007-06-18
Does ctrl-alt-f2 work? or ctrl-alt-backspace?

---

### Post by avik on 2007-06-18
Also, when it does freeze, do the graphics get garbled?  That happened to me too; turns out it was a hard drive failure (even though detaching that hard drive didn't fix the problem until I reinstalled the OS...).

---

### Post by Opti on 2007-06-19
I can't use the keyboard since everything stops working.

And the graphic stays the same, no change at all. It's like u've taken a screenshot.

I believe all this started after an update ubunutu had some 5-6 days ago I think.

---

### Post by Perrorist on 2007-06-19
I had the same thing happen while installing a backlog of updates. It was installing an update to Open Office and froze.

---

### Post by Opti on 2007-06-19
It just randomly freezing every so often... getting pretty enoying :(
No errors while updating no freezing during an update. It started a day or so after.

---

### Post by phr0ze on 2007-06-19
Try unplugging the mouse and keyboard and plug it back in. This is only if they are USB. Let us know.

---

### Post by MrShmoo on 2007-06-19
This seems to be having a problem that a lot of us are having. Check [http://ubuntuforums.org/showthread.php?t=412125](http://ubuntuforums.org/showthread.php?t=412125) for possible solutions...unfortunately none of them worked for me. Let us know if you find a workaround!

---

### Post by Opti on 2007-06-19
I have read the whole thread, found some things there that I'm trying out now. Like the one where firefox is the reason for the freezing :P I'm only running eggdrop on my ubuntu comp, not touching FF at all. Comp has been OK for little over 1 day now.. I'll post more here later :) Need to monitor he comp the next days.

---

### Post by MichaelLerch on 2007-06-19
I've had a similar problem on Ubuntu 7.04 [Feisty].  I've been trying to get Cedega and/or WinE working with STEAM (Counter-Strike Source, Half-Life 2 Deathmatch, and Day of Defeat Source).  Apparently when I was transfering some file (FireFox was open at the time) from an NTFS drive to my ubuntu-based drive (under /home/michael/.cedega/STEAM/c_drive/Program Files/Steam/steamapps/) I opened a audio file and during the process the whole system locked up.

---

### Post by Opti on 2007-06-21
My Ubuntu where running 2 days and then froze up :( again.

---

### Post by MidnightOwner on 2007-06-21
I have Ubuntu Feisty installed on a desktop after upgrading from Edgy.  Had no problems with Dapper Drake or Edgy Eft on this computer.  Upgraded to Feisty Fawn and used the 2.6.17 kernel with no problem.  The problems with freezing up started with the 2.6.20 kernels.  And I have tried everything, including making the suggested modifications to grub.

Here's what I am doing now.  When my computer boots up and I start pressing the ESC key and there you will see the previous kernels your computer has used.  I select the 2.6.17 kernel and I have no problems.  When I select any of the two 2.6.20 kernels, I can go for a little while but my computer will freeze up when I run Firefox in combination with Thunderbird OR when I play a movie (using Xine).  Again, the freeze ups do NOT occur with the 2.6.17 kernel.  This is why I believe the 2.6.20 kernel is faulty, especially -- like me -- if you are employing an ATI graphics card (I have an ATI 8500 Radeon).  

I do wish I could find someone who could tell me where to find an AGP 2x/4x graphics card that works GREAT with Ubuntu distributions.

Hope this helps.

---

### Post by Opti on 2007-06-22
the only kernels I can choose from is the following:
2.6.20.17 and 2.6.20.16

I'm trying this one now 2.6.20.16 in hopes it helps. But I'm not sure it will :(

---

### Post by Lord Paladin on 2007-07-03
You did a fresh install rather than an upgrade???
I'd say that is why you don't have the same kernel as listed above as I would assume it is a kernel from an older release??

I have the same problem. I'm pretty sure something is wrong with the Kernel in Feisty as I haven't got this issue before upgrading (actually never had ANY issues before upgrading)

There are heaps of people in the same boat and scores of solutions but none have worked for me. If I find one ill keep you posted in the meantime if anyone can shed some light on how we can fix this please let us know.....

Thanks

---

### Post by xxhaloownerxx on 2007-09-22
im having the same problem! mines with GAIM apperantly, first it was a var cup error, fixed that, and now no errors or anything, this happend when i completely unplugged my computer to clean the dust out of the case :( ill try that ESC thing too, i noticed that it acted up when i installed the recent update.

---

### Post by ZxEfR on 2007-09-27
Same here.....random freezing.....I'm using 2.6.20-16-generic.

At first I thought it was FF whilst viewing digg....but it has happened while not viewing digg......although it seems to occur most often while viewing digg.

Still may be FF on my computer.....I've installed Opera and it hasn't happened while using Opera......at least not that I remember right now :(

Sure seems to occur 99% of the time while using FF. I've installed NoScript but that doesn't help either.

It sure is getting old too :(  the mouse still moves and Amarok will continue to play but that's it. I've got to hard shutdown (ouch) and reboot.


Small update: Now the mouse doesn't move when it freezes.

---

### Post by donmor on 2007-09-27
At boot up. I was getting a clock error.
Put "noapic nolapic"  into my kernel line at boot-up, and since then, the computer hasn't frozen.

root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=caae8c05-dc12-43d2-81e1-8805a409e1d6 ro quiet splash** noapic nolapic**
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

Hope this helps someone else.

Don

---

### Post by euthyfro on 2007-09-29
This seems 2b a major problem for a lot of people, it started for me w/the latest kernel update.  I found myself some bad RAM directing memtest, thought i fixed it but then it started again, guess i'll try the menu.lst edit now & see if that works for me.

Keep ya'chins up comrades.

---

### Post by euthyfro on 2007-09-29
& speaking of clock error, that had been my only problem before the update.  Even set to synchronize automatically with Colombia U., my clock would end up 2 or 3 minutes fast every couple weeks & require a synchronization from the terminal.  i dunno if we're talking about the same "clock" here, but yeah it had never really bothered me enough to do anything about...who knows if this is related to the freezing?

---

### Post by ZxEfR on 2007-10-23
Well I have been using Gutsy Gibbon for about a week now and not one freeze..... :) I think the freezing problem for me is over with....I sure hope so....it was getting bad.

---

