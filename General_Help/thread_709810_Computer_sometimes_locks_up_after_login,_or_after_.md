---
title: "Computer sometimes locks up after login, or after a couple minutes"
date: 2008-02-27
forum: General Help
---

### Post by bmartin on 2008-02-27
I bought a new Compaq Presario (I don't happen to know the model) for my mother and slapped Gutsy Gibbon on there.

Ever since installation, the computer sometimes locks up at the login screen, or right after signing in, or a couple minutes after signing in. Checking the /var/log/dmesg* files yields no useful information. The LOCK keys on the keyboard all flash when it locks up, indicating a kernel spinlock.

Sometimes the computer works fine for hours on end. If it locks up at all, it's shortly after booting.

This sounds like a driver issue to me. I have Gutsy on many computers which happen to have some of the same hardware as the new one:
-The wireless is the same as in my girlfriend's laptop (Atheros AR5007); the computer locked up before NDISwrapper was installed
-The processor is an Intel Core Duo
-The video driver is a well-known Intel chipset (using the Intel-supplied drivers, not running Compiz, no bells or whistles)
-The ACPI stuff seems to work fine.
-I receive no warnings from dmesg.

Where do I start with a problem like this?

---

### Post by yngens on 2008-02-28
The same issue here. Of course I have different configuration, but the problem in essence the same - Just recently have installed Gutsy Gibbon, everything works fine except from time to time it freezes and I have to reboot by only pressing Power button. 

Ubuntu Forums have lots of different threads on the issue, but no actual solutions. Because as you suggested it seems to be related to driver and Gutsy incompatibility, and every hardware has its own drivers.

I have switched two of my laptop computers to Gutsy Gibbon, Dell 6000 and Dell 9300. While the first one started to work from the very beginning witout any issue, Dell 9300 has been giving me lot's of headaiches, the main one being this freezing issue. And I dont' know where to start to solve it and to say frankly I doubt it is resolvable at all.

---

### Post by bmartin on 2008-02-28
On that same computer, the Feisty live CD won't work at all. Maybe she'll have better luck when Heron comes out. On my laptop, I reverted to Feisty because of the problems I was having... the biggest ones were the "black screen during boot" and the terrible HDD access time.

It's too much to fix new problems every time Ubuntu releases a new version. I'm only going to do the LTS updates from now on. Edgy was good enough... I should've stopped after I got that working.

---

### Post by yngens on 2008-03-24
Read this: [http://ubuntuforums.org/showpost.php?p=4574653&postcount=12](http://ubuntuforums.org/showpost.php?p=4574653&postcount=12)

---

### Post by bmartin on 2008-03-24
> **yngens said:**
> Read this: [http://ubuntuforums.org/showpost.php?p=4574653&postcount=12](http://ubuntuforums.org/showpost.php?p=4574653&postcount=12)
Thanks for the info. My mother lives in NY and she apparently hasn't been having the lock-up issues that I had with her laptop, but that's good to know. I reinstalled Feisty on my laptop after having a number of issues with Gutsy.

I'm glad that they're focusing on stability with Hardy; it's much-needed after these appalling experiences people have been reporting with Gutsy. It worked well on some systems... but on the ones it didn't, it was unbearable. I'm not going to upgrade from Hardy for a long time.

---

