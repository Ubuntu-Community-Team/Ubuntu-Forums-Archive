---
title: "System beeps on return from suspend"
date: 2008-05-05
forum: General Help
---

### Post by AaronMT on 2008-05-05
I dont know what is causing this, I get a few system beeps every time I return from suspend, I also disabled system sound but it still occurs.

How can I diagnose this?

---

### Post by ryanhaigh on 2008-05-05
No idea what could be causing this as I have never used suspend on any of my machines but you could try blacklisting the pc speaker module which is probably what is making the noise. To do so add ```
blacklist pcspkr
``` to /etc/modprobe.d/blacklist. This won't take effect till you reboot and you will need to open the file with sudo to make the change (Alt-F2 then enter gksudo gedit /etc/modprobe.d/blacklist)

---

### Post by Z47isthenew42 on 2008-05-08
I don't know.  I get beeps after I try to suspend and then come back from suspend, but I also get an error message saying that my computer has failed to suspend.

---

### Post by retrow on 2008-05-08
Or if you don't want to disable the speaker, you can disable system beeps from sound settings.

---

### Post by sdennie on 2008-05-08
If suspend/resume is working but beeping at you, try System->Preferences->Power Management->General and uncheck, "Use sound to notify of an error".

---

### Post by Whiffle on 2008-05-08
What kind of computer?  I know thinkpads do this by default and its a bios setting.  I turned it off in bios and havn't heard it since.

---

### Post by gcastell on 2008-05-09
I have the same problem, but mine is not consistent. In many ocassions my computer resumes without problem but sometimes it beeps and I get the message that my computer failed to suspend. Is there any log where I could check why I got that message?

---

### Post by HumidBean on 2008-05-13
I get very similar behavior on an XPS M1210.  Sometimes after resuming, there's a series of loud, shrill beeps that do not appear to be BIOS error beeps.  Sometimes, this is all that happens, and the laptop resumes just fine.  Other times (with or without beeps) it will resume without the keyboard and mouse working.  When that happens, closing the lid to suspend it, then re-opening the lid can sometimes(*) fix the problem.  In no event do I get any error text displayed in X.

(*) 1/1 attempts worked; I'd need a larger sample size to know the trend.

---

### Post by MattressVon on 2008-05-20
I get the same problem except the loud beeps come out of my 5.1 surround speakers and headphones. I also get the error message and amusing a desktop computer going into s3 suspend with s3 suspend to ram enabled in bios. I've gon through litterally hundreds of post on this and have not found a bug filed yet for it with launchpad or ACPi kernal modules. I'm wondering if that means there is a solution. It ony started after i installed 8.04 beta and doing a fresh install of Hardy LTS hasn't stopped it.

---

### Post by MattressVon on 2008-05-20
Update: I attempted to turn off the audio notification in power management and it didn't help.

---

### Post by MattressVon on 2008-05-22
So VOR your suggestion worked after i restarted machine :). i now get no loud beeps. I'd still like to know how to address the issue of whatever is causing the problem in the first place. i know i can just click the don't show this message again option when the error pops up, but I'd like to specifically address the ACPI problem itself. I'm looking on the ACPI kernal bug list and will post here if i see anything.

---

