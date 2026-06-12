---
title: "1GB RAM with X64, Lubuntu 32 or 64 bits?"
date: 2014-05-02
forum: General Help
---

### Post by davidafranklin on 2014-05-02
Hi,
Quick question,
My old laptop only has 1 GB RAM with a x64 CPU, I hear for 1 GB  Lubuntu 32bits is better but  with a x64 CPU, it seems I coud  utilize better the CPU
Any suggestion on which version would work best? Right now I have installed the 64 bits version and it is ok but not great.
Thanks

---

### Post by slooksterpsv on 2014-05-02
Do you plan on running any 64-bit software? If not, go with 32-bit. Yes you can get some performance enhancements with 64-bit, but only if your system has the capacity to take use of it.

What kind of laptop is it? Odd to see laptops that are 64-bit with only 1 GB of RAM (unless it's a netbook).

---

### Post by 3rdalbum on 2014-05-03
64-bit is usually better, but 64-bit distros take up more RAM. When you have only 1 GB of RAM it would probably be better to run 32-bit so you don't run out of free RAM so easily. Running out of RAM causes the disk to be used as virtual memory, which really slows things down.

---

### Post by davidafranklin on 2014-05-03
> **slooksterpsv said:**
> Do you plan on running any 64-bit software? If not, go with 32-bit. Yes you can get some performance enhancements with 64-bit, but only if your system has the capacity to take use of it.

What kind of laptop is it? Odd to see laptops that are 64-bit with only 1 GB of RAM (unless it's a netbook).

Thanks,
It is a Gateway MX6426 with a 2.2  GHz AMD Turion 64 Mobile.

If speed gain will be siginificant, i am ok redoing it as I just installed a fresh new distro with 14.04. If not significant, maybe I will wait for the 14.10.

---

### Post by pfeiffep on 2014-05-03
@davidafranklin if you're interested is speed IMO you should increase RAM to 2 GB which is max for this machine.

---

### Post by LastDino on 2014-05-03
Unless you're going to run x64 bit things, don't bother as everything x32 bit will require slightly more RAM/Juice from system on x64 bit OS, especially if system is old and barely supports x64 (Mine is same, but it is a Desktop).  I don't have benchmarks or anything to show for this, but it is my general observation. If its getting lighter  is you aim, then go for x32

---

### Post by ibjsb4 on 2014-05-03
I would of guessed that either 32 or 64 bit would run well on that setup.  I wonder if its a package using up the cpu.  You could monitor your cpu usage, see if that will give you any clues.  In terminal:

```
top
```

[https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal](https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal)

---

### Post by davidafranklin on 2014-10-09
Hello All, after several months on Lubuntu 14.04 (x64), I have increased  my ram to 2 GB (from 1 GB).
I plan to upgrade to Lubuntu 14.10 x32. Will I lose all my data as I go from x64 to x32 at the same time?

Thanks

---

### Post by Olav on 2014-10-10
> **davidafranklin said:**
> Hello All, after several months on Lubuntu 14.04 (x64), I have increased  my ram to 2 GB (from 1 GB).
Did you notice any effect after the memory upgrade? A lightweight 64-bit system with 2 GB RAM should be able to run most things nicely.
> I plan to upgrade to Lubuntu 14.10 x32. Will I lose all my data as I go from x64 to x32 at the same time?

Thanks
If you really want to do this, you will have to do a proper reinstall. I don't think it is possible to upgrade from 64-bit to a 32-bit operating ssytem. If your /home is a separate disk partition it should be possible to keep that intact while you format the other partitions during the installation. Of course you do have a full backup of all your data in case anything should go wrong. If you haven't, that would be your first priority before doing anything else.

---

### Post by davidafranklin on 2014-10-10
I did not notice a huge difference with 2GB ram in speed (the fan just runs a little bit less) but I think the difference will be greater with the 32 bits vs 64. I will do a fresh install, no problem.
Thanks for the advice.

---

