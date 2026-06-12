---
title: "HDD problem"
date: 2006-12-10
forum: General Help
---

### Post by xopher on 2006-12-10
I have this small problem with my computer at the moment. Yesterday everything was working just fine - and I left the computer on for the night, like I always do. This morning - 6 hrs later, the system was unresponsive -- it didn't wake up properly, and I couldn't access a TTY. CTRL+ALT+DEL worked to restart the system though.

Now to the problem - at boot, /dev/sda isn't found by fsck. I login at the promt, and my $HOME is missin (it was on /dev/sda).

This sounds like a hardware failure to me, are there any other possibilities? (Im hoping yes -- since didn't have recent backups of my $HOME)

Im not home at the moment, and won't be for a week or so -- because of work. But any ideas are appreciated.

:rolleyes:

---

### Post by JohnBoy55 on 2006-12-10
It really does sound as if your hard drive bit the big one. One possible solution you might try before you call it quits is a program called SpinRite. It's a drive recovery program from 'www.grc.com' that costs about $89 US dollars. Depending on how 'mission critical' the lost files are, it may be worth the attempt. We use the program at work, and I will tell you, it is amazing what you can recover with it. BTW, if you do use it and it works, I'd make a drive image, pitch the current hard drive, and get a new one. Once they start to fail, they usually go downhill fast.

---

### Post by xopher on 2006-12-10
> **JohnBoy55 said:**
> It really does sound as if your hard drive bit the big one. One possible solution you might try before you call it quits is a program called SpinRite. It's a drive recovery program from 'www.grc.com' that costs about $89 US dollars. Depending on how 'mission critical' the lost files are, it may be worth the attempt. We use the program at work, and I will tell you, it is amazing what you can recover with it. BTW, if you do use it and it works, I'd make a drive image, pitch the current hard drive, and get a new one. Once they start to fail, they usually go downhill fast.

Thanks. I'll look into this when I get back home. :)

Really hope it just magically works again though. But yeah, I doubt it. Haven't had that kind of luck with anything in a long.. well, never. ](*,)

---

### Post by xopher on 2006-12-14
Wow - I booted today (I know I've been away for a long time ;)), and it worked again. Don't know what caused this, probably the HDD nearing total failure..

And yes, I am backuping everything as we speak, let's see how long this hdd holds up.. :rolleyes:

---

### Post by JohnBoy55 on 2006-12-16
I'm glad it worked for you! IMHO I still think you should look at replacing your hard drive. If nothing else, running SpinRite periodically may keep you running. Good luck!

---

