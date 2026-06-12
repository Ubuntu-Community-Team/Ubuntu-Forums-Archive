---
title: "Live/Install CD Won't Boot"
date: 2006-11-05
forum: General Help
---

### Post by subxero on 2006-11-05
I recently downloaded the Edgy live/install CD, for i386, and successfully tried it under VMware 5.5 with no problem. However, it refuses to boot on my real machine. The Ubuntu screen comes up and asks me what I'd like to do -- start/install Ubuntu, et cetera. So, I choose the first option, and the loading screen appears. Then the main loading screen (with the large "Ubuntu" text) appears, and the progress indicator bounces to and fro for a good 5-10 minutes before the screen goes blank and I get an error message that flashes very quickly, and then am dropped to a /bin/sh prompt titled "(initramfs)" where I can't do a whole lot. /bin/sh also gives a message: "/bin/sh: can't access tty; job control turned off."

I'm stumped. ](*,) 

Oh, I tried doing a "check CD for defects" and the same thing happened. So I booted it under VMware again (I still have Windows on my PC at the moment) and tried it there, and it passed with flying colors.

If you need any more info, let me know, I apologize for any lack of detail. I would greatly appreciate help with this, I'm looking forward to Edgy.

Thanks.

---

### Post by subxero on 2006-11-05
I'm really looking forward to trying the new version of Ubuntu -- is there anyone that can help me with this problem?

---

### Post by ckonrad on 2006-11-05
> **subxero said:**
> I'm really looking forward to trying the new version of Ubuntu -- is there anyone that can help me with this problem?

that error is from a boot loader not being able to find a root device i dont know why it would do that just form a live cd though i will look around, if i cant help someone has the answer around here i am sure. If you look here [http://ubuntuforums.org/showthread.php?t=94250&highlight=job+control+turned](http://ubuntuforums.org/showthread.php?t=94250&highlight=job+control+turned) you will see that someone else had the same issue with windows on a secondary drive. Not sure but maybe some of that info would be helpful.

---

### Post by subxero on 2006-11-05
I fixed it!

I've never had to do this with a Ubuntu installation before (I have with RedHat, and Mandrake -- something must be really different with Ubunut 6.10)

All I did was go into the BIOS, go to Advanced BIOS Options, and turn APIC off -- seeing as how I have only one processor anyway, APIC isn't a serious benefit nor a requirement. I don't think I see any downside to turning APIC off, since Ubuntu boots now :D

I've updated the tags for this forum post so it's easier to find.

---

### Post by Devboy on 2006-11-16
I have tried booting the live cd and came up with the same old job control turned off problem, I have tried what was mentioned about turning of APIC and this did not solve the problem.

Anyone got a clue? I am clueless.

---

### Post by happysmileman on 2006-11-16
You've fixed it so this isn't any help for you... But since I had a similar problem I'd like to point out that you should burn the ISO to a CD on a lower speed than you would burn music or stuff as the slightest error could render the CD unusable or slow it down alot

---

