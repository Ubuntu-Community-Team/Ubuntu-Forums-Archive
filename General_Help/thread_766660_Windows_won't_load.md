---
title: "Windows won't load"
date: 2008-04-25
forum: General Help
---

### Post by ontocabaret on 2008-04-25
Hi.

I installed Ubuntu using the Wubi loader a couple of days ago. I've been working in Ubuntu for the last few days, not having booted into Windows. Just now, however, I wanted to check something in Windows and whenever I try to boot it, my computer just restarts and takes me to the 'Which OS'-screen again. I've tried Safe Mode, I've tried 'Last known working configuration' but nothing seems to work. I just can't get Windows running.
Ubuntu stalled a couple of hours back and I couldn't do anything. I tried to reboot it but it wouldn't do. My only solution was a hard reboot (pressed the power button on my pc for a few seconds.) I'm guessing this is the reason why my Windows XP won't load anymore. (I don't get any errors, just a black screen and back to the 'Intel' logo I get when I start my pc)
I can still access my 'windows files' (my hdd) by going to /host and nothing is lost, I just can't get in there with windows anymore.

I know I shouldn't have hard rebooted but I didn't have another option at the time, as far as I know.
I'm just hoping that someone can help me get back on Windows XP one way or another, because I don't think I'm ready to live with Ubuntu alone yet.

I need some help ASAP.

Thanks in advance,

J.

---

### Post by ago on 2008-04-25
chkdsk /r 

If you cannot boot into windows, you need to run it from a Windows CD (from the recovery console). There are also some rescue CD on the web but I cannot provide the link...

[https://wiki.ubuntu.com/WubiGuide#head-ba8242d659938a2a8293e4b77c8733eae7334a0a](https://wiki.ubuntu.com/WubiGuide#head-ba8242d659938a2a8293e4b77c8733eae7334a0a)

---

### Post by ontocabaret on 2008-04-25
> **ago said:**
> chkdsk /r 

If you cannot boot into windows, you need to run it from a Windows CD (from the recovery console). There are also some rescue CD on the web but I cannot provide the link...

[https://wiki.ubuntu.com/WubiGuide#head-ba8242d659938a2a8293e4b77c8733eae7334a0a](https://wiki.ubuntu.com/WubiGuide#head-ba8242d659938a2a8293e4b77c8733eae7334a0a)


I've tried doing 'chkdsk /r' from the recovery console and it says something like (it's in dutch so i have to translate) 'the system has errors' and then it just goes back to c:\> without executing chkdsk.

I have no idea what to do. I can't access the hdd itself from the recovery console, yet i can see it and access everything from Ubuntu.


EDIT: Do you think it would be a safe option to just back up the things I really need through Ubuntu, then format everything? Or might there be another, easier solution?

---

### Post by ontocabaret on 2008-04-25
Bump.

Ago, I've managed to get chkdsk running. It's taking a long long time though, 61% atm after almost an hour. Is this normal?

I hope that'll do the trick to make me happy again :)

---

### Post by ago on 2008-04-25
should be ok

---

