---
title: "Should I use Truecrypt or a better alternative? what's the standard now?"
date: 2022-10-09
forum: General Help
---

### Post by david503 on 2022-10-09
So, 10 years ago I used to use Truecrypt in Windows.  I know it runs in linux too but it's support is sketchy.   

What's the current most popular?  (I don't want to use Ubuntu's built in one that it does offers during installation.)

I only want to encrypt a partition, so not the / partition with the OS on it. 

Anyway, recommendations?  Which ones do you like most, or should I just go back to truecrypt?

thanks,

-dw

---

### Post by TheFu on 2022-10-10
You can use LUKS without choosing it at install time, i.e. for 1 partition.  It integrates with some file managers too - like Caja.
Two videos and 1 text location

* Creating Part1: [Https://youtu.be/vk9Z2_rEUak](Https://youtu.be/vk9Z2_rEUak) (nerds should find this very funny)
* Accessing Part2: [Https://youtu.be/ELEVo6SbYl0](Https://youtu.be/ELEVo6SbYl0) seems to be it.
* Text version: [Https://baldnerd.com/add-a-drive-to-linux-and-encrypt-it](Https://baldnerd.com/add-a-drive-to-linux-and-encrypt-it)

LUKS is secure, fast, flexible, and built-in.  Of course, it only work on Linux, so if you mush have access cross platform, then other alternatives, usually less secure, should be considered.  Veracrypt is the replacement for Truecrypt and has been audited a few times, but it has some known security liabilities which are solved in LUKS thanks to having 8 slots for 8 different methods/keys to access the same encrypted storage.  I've been using LUKS since about 2013 and use both passphrase and hardware token challenge-response access methods.  

 LUKS integrates with standby modes, which might be important for some people. I put a laptop into standby mode nearly every night. It is fully LUKS encrypted, and wakes the next morning without any issues.

---

### Post by TheFu on 2022-10-20
LUKS has never been hacked directly and is native to Linux with less than 3% overhead on modern CPUs.

VeraCrypt has definitely replaced Truecrypt and brought plausible deniability for hidden encrypted areas, but it doesn't take much to see that space inside the VeraCrypt container isn't used, thus is the container really hidden if it is obviously there?  The guys beating you with a rubber hose to get access aren't likely to stop.

LUKS has 8 different slots to use for decrypting the storage, which brings flexibility that doesn't exist in other solutions. It is handy to use a HW device in challenge-response mode to gain access to encrypted storage, but also have a 200 character passphrase as a backup, should that device be lost/stolen/destroyed.  Plus different users can have their own method of access. Sharing credentials is always a bad idea.

Just some things to consider.

---

