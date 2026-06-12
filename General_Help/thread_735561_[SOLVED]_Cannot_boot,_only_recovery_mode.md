---
title: "[SOLVED] Cannot boot, only recovery mode"
date: 2008-03-25
forum: General Help
---

### Post by Korrontean on 2008-03-25
Since a few days ago, without having changed anything in my configuration, the system refuses to boot.
I get to see the Ubuntu logo, but when the progress bar is about to fill, it gets stuck and goes back to text mode, where I can see the following error message:
```
*Starting Common Unix Printing System: cupsd
cupsd: Child exited on signal 11!
[54.520000] ACPI Exception (battery -0216): AE_SUPPORT, Extracting - BST (20070126)
```
Then, every few seconds I get a new line:
```
[54.520000] ACPI Exception (battery -0216): AE_SUPPORT, Extracting - BST (20070126)
[84.520000] ACPI Exception (battery -0216): AE_SUPPORT, Extracting - BST (20070126)
[114.520000] ACPI Exception (battery -0216): AE_SUPPORT, Extracting - BST (20070126)
[144.520000] ACPI Exception (battery -0216): AE_SUPPORT, Extracting - BST (20070126)
```
and so on...
In recovery mode things seem to work well, although it's first time I use this mode so I don't know if the limitations (no automatic mounting of USB drives, etc.) are due to it or can be a sign of trouble.
I'd appreciate if anyone has an idea of how to sort it out. Only if there is an easy solution, it is not worth wasting too much time and energy as my last re-installing is quite recent and it wouldn't be a big problem to do it again.
THANK YOU!!!! :)

---

### Post by Korrontean on 2008-03-25
By the way, I'm on my way to bed so I won't reply till tomorrow. THANKS AGAIN for your help.

---

### Post by Iowan on 2008-03-25
You might try [this]("http://ubuntuforums.org/showthread.php?t=704873") one to see if ACPI is causing your grief.

---

### Post by Korrontean on 2008-03-26
Thanks Iowan!
Just a few questions:
Is it a very delicate operation?
In case it boots normally after doing it, does it mean I should use my laptop daily with this ACPI disabled?
I read it is quite important for laptops, as it manages the use battery power, is that true?
Do you think a new install would be preferable?
Honestly, I'm a little afraid of messing things up as I don't really understand what I'll be doing. I usually follow instructions without understanding 100% of them (my limited knowledge gives me no other choice), but I'd like to know a little more about removing/disabling ACPI.
I hope you understand. THANKS!!!! :)

---

### Post by Korrontean on 2008-03-26
Hi, I finally decided to do as explained in the thread you recommended me, but the problem is still there. The only difference is I don't get the "child" thing. And instead of:

```
[54.520000] ACPI Exception (battery -0216): AE_SUPPORT, Extracting - BST (20070126)
[84.520000] ACPI Exception (battery -0216): AE_SUPPORT, Extracting - BST (20070126)
[114.520000] ACPI Exception (battery -0216): AE_SUPPORT, Extracting - BST (20070126)
[144.520000] ACPI Exception (battery -0216): AE_SUPPORT, Extracting - BST (20070126)
```

I get:
```
[58.4120000] ACPI Exception (battery -0216): AE_SUPPORT, Extracting - BST (20070126)
```
and then every few seconds:
```
[88.4120000] ACPI Exception (battery -0216): AE_SUPPORT, Extracting - BST (20070126)
[118.4120000] ACPI Exception (battery -0216): AE_SUPPORT, Extracting - BST (20070126)
[148.4120000] ACPI Exception (battery -0216): AE_SUPPORT, Extracting - BST (20070126)
```
Ideas anyone? THANKS...

---

### Post by Korrontean on 2008-03-26
I tried [this slightly different solution]("http://ubuntuforums.org/showthread.php?t=713143&highlight=ACPI+Exception") and it is booting well now.:guitar:
However, I'd appreciate is anybody could tell me if :confused: I can use my laptop normally now, or a more permanent solution (a new install? the problem came suddenly, shouldn't it have appeared from the beginning?) would be preferable.
THANKS!!!:)

---

### Post by kpkeerthi on 2008-03-26
If acpi is turned off, ubuntu will not be able to use the power management features available in your hardware, like CPU/GPU throttling, monitor display turn off, etc.

---

### Post by Korrontean on 2008-03-27
Thank you kpkeerthi, I'm using it this way and I've realized that now I can't turn off my computer automatically from ubuntu and also that I can't see how much battery I have left.

I guess I'll re-install when I have the time :-(

I wish there was an alternative solution to switching ACPI off!

---

