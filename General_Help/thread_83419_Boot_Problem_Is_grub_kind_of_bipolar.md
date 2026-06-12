---
title: "Boot Problem: Is grub kind of bipolar??"
date: 2005-10-28
forum: General Help
---

### Post by guyomarj on 2005-10-28
I've got boot problems. I dual boot Ubuntu adnd XP through GRUB.

If I **shutdown** my PC and then boot, all is fine. Grub asks me what I want and I can boot both systems.

But if I **reboot,** either from Ubuntu, XP, or manually, GRUB give me the grub command line or a weird error:

```
Grub 1.5

Grub loading...
Error 24
```

And freeze. (The number following "Error" changes from time to time...). And I've got to shutdown the machine and then boot.

Any ideas??

---

### Post by Kyral on 2005-10-28
Yanno, I wish there was a place where we could lookup these GRUB error numbers....

It would help me help you ;P

---

### Post by guyomarj on 2005-10-28
[QUOTE=Kyral]Yanno, I wish there was a place where we could lookup these GRUB error numbers....

It would help me help you ;P[/QUOTE]

Like a "GRUB's Errors in a Nutshell"... Yep, that would ne nice :D

If some of you use alternatives to GRUB, I'm open minded...

---

### Post by MichaelM on 2005-10-28
Taken from [http://www.gnu.org/software/grub/manual/grub.html#Troubleshooting]("http://www.gnu.org/software/grub/manual/grub.html#Troubleshooting"):
> 24 : Attempt to access block outside partition
This error is returned if a linear block address is outside of the disk partition. This generally happens because of a corrupt filesystem on the disk or a bug in the code handling it in GRUB (it's a great debugging tool). 
Hope that helps :)

---

### Post by guyomarj on 2005-10-28
[QUOTE=MichaelM]Taken from [http://www.gnu.org/software/grub/manual/grub.html#Troubleshooting]("http://www.gnu.org/software/grub/manual/grub.html#Troubleshooting"):[/QUOTE]

Thx for the manual MichaelM. It sure helps.

But it is still a mystery why Grub crash on **reboot** but not on **shutdown+boot**...

I'll read the manual and see what I can find.

---

