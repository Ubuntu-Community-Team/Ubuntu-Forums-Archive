---
title: "Shutdown operating system but no longer power off"
date: 2021-02-22
forum: General Help
---

### Post by peter228 on 2021-02-22
I have been using Ubuntu since I think Ubuntu 5.04.   Only a few issues over the years and all had a happy ending.  That is until now...  and I am stuck.

I run Ubuntu 20.04 and it is fully up to date, all updates / patches have been installed as soon as they are released. (uname -r  5.8.0-43-generic)  I also keep an early version of 20.04 on a memory stick, it is my disaster recovery tool.  I update this every time there is an LTS release.

That is the background.  This is my issue.

Ubuntu 20.04 used to shutdown and then power off when either you clicked on the icon or issued the command sudo shutdown now.  About three months ago it stopped doing this.  The system closes and then stalls with the Ubuntu name appearing in the bottom centre of the screen.  It does nothing else and does not power off the computer.

Is this the Bios?  The answer is no.  I know because if I boot from the memory stick with the early Ubuntu 20.04 it will power off either from clicking the icon or issuing the shutdown command.

So my conclusion is that one of the magical updates was not so good.  How to fix this ....  I know not.  I find it surprising that I am the only person with this headache.

What to do?

---

### Post by Dennis N on 2021-02-22
Here is one possibility: It could be a stop job running with a minimum time set to release it - often that's 90 seconds - then it will power off. Sometimes, but no always, you can see this in screen messages output if you ESC during that time. 

Wait 5 minutes and see if it turns off by then.

---

### Post by peter228 on 2021-02-22
Thank you for your suggestion Dennis.

I pressed ESC at the end of the sequence and that revealed the system output.  The last four lines were

Reached target Shutdown
Reached target Final Step
Finished Power-Off
Reached target Power-Off

and there it sat for the next ten minutes when I manually powered off.

---

### Post by CatKiller on 2021-02-22
Did you - maybe about three months ago - fiddle with your ACPI settings?

---

### Post by peter228 on 2021-02-22
not at all.  Did not play with anything ...  no time and not enough knowledge.  I am good at digging holes but have learned that it is best to only dig holes I can get out of.

---

### Post by CatKiller on 2021-02-22
That's a shame; if it was something you did, it would be something you could undo. Still, that's the place to look. That's the mechanism through which, amongst other things, the OS sends the signal to the BIOS/UEFI to turn the computer off.

---

### Post by peter228 on 2021-02-22
Yes, that would be easy.  I also just took a look and find that I do not have a directory UEFI on my system and the other directories under boot are efi (empty) and grub.

---

### Post by nuclearmonster on 2021-02-23
I have a similar issue with my 20.10 i7 6700k machine which was shutting off fine for months and now when I go to to shut down it remains on and a message remains onscreen with a timestamp.
[https://imgur.com/a/uRTMs6q](https://imgur.com/a/uRTMs6q)

---

