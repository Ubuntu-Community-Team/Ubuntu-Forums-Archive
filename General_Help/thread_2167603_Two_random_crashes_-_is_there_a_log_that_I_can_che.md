---
title: "Two random crashes - is there a log that I can check?"
date: 2013-08-14
forum: General Help
---

### Post by listerdl on 2013-08-14
Just had two completely random black screen of death crashes - the only message said - very briefly - closing apache2.

Anyway - is there a log or a way to see what caused the crash? Thanks

---

### Post by listerdl on 2013-08-14
In fact - I think I have narrowed it down to VirtualBox - could that cause crashes you think? Difficult to say I know hence question on logging...

---

### Post by tgalati4 on 2013-08-14
Logs are kept in /var/log and another helpful tool is dmesg:

```
dmesg | tail -100
```

How are you running virtualbox?  What is the host operating system and what is the guest operating system?

Since VM's use a lot of RAM, I would take the machine apart, clean it out and reseat the RAM.  Hardware issues don't often get logged properly.  Linux expects perfect hardware.  Check your power supply as well.

---

### Post by listerdl on 2013-08-14
thanks for reply. Really - you reckon to re-seat the RAM....Ill do that and see if it crashes again - but yeah, I think you and I agree on the VirtualBox issue....maybe allocate more RAM to VBox as well?

---

### Post by Gilad_Pellaeon on 2013-08-14
> **listerdl said:**
> thanks for reply. Really - you reckon to re-seat the RAM....Ill do that and see if it crashes again - but yeah, I think you and I agree on the VirtualBox issue....maybe allocate more RAM to VBox as well?

You don't want to allocate too much RAM though to VBox because then you're placing more strain on the host operating system too. For example I have a 1gb ram system with a Vbox windows xp setup and I only allocate 192mb ram to it and 32mb video ram. Now, on the other hand if your system has lots of RAM like oh say 4gb, 8gb, or even more then you could allocate more as needed but don't overdo it regardless.

---

### Post by listerdl on 2013-08-14
> **Gilad_Pellaeon said:**
> You don't want to allocate too much RAM though to VBox because then you're placing more strain on the host operating system too. For example I have a 1gb ram system with a Vbox windows xp setup and I only allocate 192mb ram to it and 32mb video ram. Now, on the other hand if your system has lots of RAM like oh say 4gb, 8gb, or even more then you could allocate more as needed but don't overdo it regardless.

Yes you are 100% correct. My machine has 4G RAM and I gave the XP installation 3G RAM which was way too much.

I think that has solved it - in fact, the reason why I have the XP is b/c I prefer to run windows programs in a Virtual state rather than WINE.

Thanks

---

### Post by Gilad_Pellaeon on 2013-08-14
> **listerdl said:**
> Yes you are 100% correct. My machine has 4G RAM and I gave the XP installation 3G RAM which was way too much.

I think that has solved it - in fact, the reason why I have the XP is b/c I prefer to run windows programs in a Virtual state rather than WINE.

Thanks

I'm the same way. I just run a handful of small programs and utilities in my XP VM nothing major. :)

---

