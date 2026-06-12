---
title: "Computer locked with a virus"
date: 2022-06-22
forum: General Help
---

### Post by mountainman70 on 2022-06-22
I am running Ubuntu 22.04. Just now I signed in on one of my computers and opened Facebook. As I was checking a site that I thought was good(don't remember what it was now) I got a screen saying MS Windows Defender Security Center had locked my computer and to call this number(833-798-2936) for a technician to help solve the problem. I can't do anything on that computer. 

How do I remove this? Can I just wipe the HD and reinstall from a cloned drive? 

Thanks for any advice.

---

### Post by Autodave on 2022-06-22
Usually, I do a hard reboot.....press and hold the power button until the machine stops running.  Turn PC back on.  At that point, 99% of the time, all is back to normal.  On very rare occasions, you might have to go into the settings of your browser and change the start page.

---

### Post by mountainman70 on 2022-06-22
> **Autodave said:**
> Usually, I do a hard reboot.....press and hold the power button until the machine stops running.  Turn PC back on.  At that point, 99% of the time, all is back to normal.  On very rare occasions, you might have to go into the settings of your browser and change the start page.

Thanks Autodave for replying. 

Before whenever I got the FBI warning I would do a hard reboot and it was gone. This time I tried twice and it was still there. Then I tried crtl+alt+delete and restart. Since I dual boot both W10 and Ubuntu 22.04 on that computer I decided to open W10 first. It opened without any problems. I then restarted and opened Ubuntu and it opened normally.
I have read that the so called Trojan App: Ads.fiancetrack (2).dll is not real. Don't Know if true or not. 

I can now open Ubuntu like I always do.

I am running all scans in W10 since it has been awhile.

Thanks Autodave.

---

### Post by yancek on 2022-06-22
Don't call the number.  So you are not able to boot the computer at all?  Do you have another OS installed?  Unfortunate that you don't know which site as you may end up there again.

Did your OS just lock up?  What exactly happened?  Are you unable to do anything?  Have you rebooted?  What happened?

---

### Post by Holger_Gehrke on 2022-06-22
Before doing a hard shutdown, I'd first try switching to a virtual Terminal (Ctrl-Alt and a function key, F1 to F6 should work depending on display manager, display server and GUI used). At that point you should get a text mode login and can then do a controlled shutdown. If that doesn't work, the ['Magic Sysrequest']("https://en.wikipedia.org/wiki/Magic_SysRq_key") key combinations should. Hold the keys Alt and SysRequest and hit 'r'; keep holding Alt and s-l-o-w-l-y type "e","i","s","u", and "b". This, too, should lead to a reboot - the difference to a hard shutdown is that all processes get killed (in two stages, SIGTERM on 'e', SIGKILL on 'i'; this allows programs to shut down in a controlled manner), then storage is synced ('s') and unmounted ('u') before boot ('b'). Only if both of these fail would I hold the power button.

Holger

---

### Post by #&amp;thj^% on 2022-06-22
> **mountainman70 said:**
> 
I** have read that the so called Trojan App: Ads.fiancetrack (2).dll is not real. Don't Know if true or not. **

I can now open Ubuntu like I always do.

I am running all scans in W10 since it has been awhile.

Thanks Autodave.
It's real in the sense, The “App Ads.fiancetrack(2).dll” page is a browser-based scam that displays fake error messages to trick you into calling a Tech Support Scam phone number.
Source: [https://malwaretips.com/blogs/remove-ads-fiancetrack2-dll-virus/](https://malwaretips.com/blogs/remove-ads-fiancetrack2-dll-virus/)
You are seeing the “App Ads.fiancetrack(2).dll” tech support scam because your computer is infected with a malicious program or a site that you have visited has redirected you to this page.

Less than reputable sites can display malicious ads that redirect your browser to the “App Ads.fiancetrack(2).dll” tech support scam to generate advertising revenue. If this happens, you can close the page and install an ad blocker like AdGuard to block the malicious ads. However, if you are continuously seeing pop-ups like the “App Ads.fiancetrack(2).dll” tech support scam, then your computer might be infected with a malicious program and you need to scan your device for adware and remove it.
It also shows how to get rid of it.

---

### Post by mIk3_08 on 2022-06-23
> **mountainman70 said:**
> I am running Ubuntu 22.04. Just now I signed in on one of my computers and opened Facebook. As I was checking a site that I thought was good(don't remember what it was now) I got a screen saying MS Windows Defender Security Center had locked my computer and to call this number(833-798-2936) for a technician to help solve the problem. I can't do anything on that computer.
How do I remove this? Can I just wipe the HD and reinstall from a cloned drive?
Thanks for any advice.
Usually in this kind of issue I just completely eliminate the Windows Operating System to save my hardware. This kind of issue can break your hard drive storage.Regards and cheers.

---

### Post by cyberkingdom on 2022-06-27
I would take a look at this link [https://www.lifewire.com/free-bootable-antivirus-tools-2625785](https://www.lifewire.com/free-bootable-antivirus-tools-2625785) . I should allow you to scan the computer with out turning it on. Just make sure that the bitlocker is not enabled or it will not be able to scan.

---

