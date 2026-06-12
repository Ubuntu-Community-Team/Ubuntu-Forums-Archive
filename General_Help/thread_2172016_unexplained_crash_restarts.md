---
title: "unexplained crash restarts"
date: 2013-09-02
forum: General Help
---

### Post by tdit2 on 2013-09-02
Hi all,

I have a problem which is giving me grief and I need some suggestions.

I have a simple box Zotac Box with a dual core Atom 64 bit cpu and 4gb of ram + 500gb drive. This machine used to run windows 7 32bit without issue. 

I'm running Ubuntu 12.04 32bit and I have a random crash restart problem. I have a lot of browser windows open - 15 to 30 on average, and there is a relation there. The crash restart only happens when I have the browsers open. If i'm only in a document file, it's stable. I tried Firefox and now Chromium. the problem persists. I've run hardware checkers including the Ubuntu memery scanner. No errors are found even after a burn in test of 12 hours. 

Is there any way I can log the crashes and look for a cause?

Any help greatly appreciated.

---

### Post by tdit2 on 2013-09-04
No one can tell me how to check Ubuntu logs for causes of these crashes? Don't be shy now! Any pointers appreciated! Thanks all

---

### Post by VMC on 2013-09-04
There located in "/var/log" Specially look at *syslog*, *kernlog*. Also *dmesg* can be run from a terminal.

---

### Post by ian-weisser on 2013-09-04
Please clearly describe what you mean by "crash restart".
Do you mean that the system restarted/rebooted (BIOS, grub, login screen, everything)
Do you mean that the session crashed/aborted (login screen only)
Or do you mean some other behavior?

---

### Post by tdit2 on 2013-09-05
> **ian-weisser said:**
> Please clearly describe what you mean by "crash restart".
Do you mean that the system restarted/rebooted (BIOS, grub, login screen, everything)
Do you mean that the session crashed/aborted (login screen only)
Or do you mean some other behavior?

Thanks for your reply:

I mean: Do you mean that the system restarted/rebooted (BIOS, grub, login screen, everything)

Just as if the power was pulled then put back in. Sometimes I get a slight warning that the system will hang (unresponsive) for a few seconds only then bang - crash restart. But that occurs rarely. 

I'm going to post the log results after the next one (per the log suggestions above).

Cheers

---

### Post by tdit2 on 2013-09-05
> **VMC said:**
> There located in "/var/log" Specially look at *syslog*, *kernlog*. Also *dmesg* can be run from a terminal.

Thanks, I'll check them after the next restart. More than likely tonight when I'm working the machine hard.

---

### Post by tdit2 on 2013-09-05
what does dmesg do and how can I paste the results here?

---

### Post by ian-weisser on 2013-09-05
> **tdit2 said:**
> I mean: Do you mean that the system restarted/rebooted (BIOS, grub, login screen, everything)

Just as if the power was pulled then put back in. Sometimes I get a slight warning that the system will hang (unresponsive) for a few seconds only then bang - crash restart. But that occurs rarely. 

That is usually a hardware issue. Most commonly overheating.
Ubuntu does not have any known software failure mode that causes a reboot, clues in the logs may be sparse or non-existent.
Overheating, for example, is handled by the hardware and bios directly. Nothing is logged...because the system is off.

---

