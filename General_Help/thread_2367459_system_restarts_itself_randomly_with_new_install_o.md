---
title: "system restarts itself randomly with new install of 16.04 on HP Elite 8300"
date: 2017-07-30
forum: General Help
---

### Post by dna-8 on 2017-07-30
Hello, I just installed Xubuntu 16.04 on a refurbished HP elite 8300. The system seems to work fine then suddenly restarts without warning. I'm trying to find out what causes this. Is there a way to access a system log or crash report that would tell me what causes the restart?

Sometimes the restart might be associated with particular programs (AssaultCube seems to make it crash after a few minutes) or while transferring files from an external hard drive. But at least once there was nothing going on and it restarted,

Any ideas? Thanks for any help.

---

### Post by #&amp;thj^% on 2017-07-30
Just the mere mention of the term " refurbished" make's me want to say hardware related. (Don't kill the messenger :))
If you are dual booting with another OS installed check to see if it is the same there.

---

### Post by dna-8 on 2017-07-30
I agree, though it could also be a driver issue. Unfortunately there is no dual boot.

---

### Post by dna-8 on 2017-07-30
I was able to get it to crash by playing another game so maybe it is graphics related? It is not overheating, the temp is stable.

---

### Post by Autodave on 2017-07-30
That really sounds like a memory stick failing. Run a memtest on it if you can.

---

### Post by dna-8 on 2017-07-30
Hi dave, a failing memory stick causes a system restart? I did run a test on the memory and hard drive, with no problems indicated.

---

### Post by dna-8 on 2017-07-30
I tried running Memtest86 and could not complete because the computer restarted during the test... What is the likely culprit?

---

### Post by dna-8 on 2017-07-31
Okay, so the same problem (system restarting without warning) happens on both Xubuntu, and when the system is running memtest from a usb.  Anyone know what kind of hardware fault is the likely culprit?

---

### Post by QIII on 2017-07-31
I would suspect a power supply issue given what you have told us.  Is there any warranty on this machine?

---

### Post by dna-8 on 2017-07-31
Yes, it's still within its 30-day return policy, luckily. 


I've found HP support pages for this problem which tell users to use Windows tools for checking for hardware failures. Is there anything similar I can use with Xubuntu?

---

### Post by #&amp;thj^% on 2017-07-31
These tools are very limited, But have a look here: [https://www.linux.com/news/hardware-diagnostics-open-source-tools](https://www.linux.com/news/hardware-diagnostics-open-source-tools)

---

### Post by dna-8 on 2017-07-31
Thanks I'll check those out. Is there any clue I could find from syslog or something like that?

---

### Post by BenginM on 2017-08-01
I like this replay by ian post #4
[https://ubuntuforums.org/showthread.php?t=2335312](https://ubuntuforums.org/showthread.php?t=2335312)

So yes, check syslog and kern.log under /var/log .

---

