---
title: "PAE problem solved in 14.04. Forcepae option."
date: 2014-03-16
forum: General Help
---

### Post by mörgæs on 2014-03-16
For almost two years, or since Ubuntu 12.04 was released, there has been a steady stream of posts about PAE and related problems. 

12.04 was the first Ubuntu for which a special non-PAE version wasn't available. X/Lubuntu carried on supporting non-PAE processors for one release more, making 12.10 their first PAE-only release.

Several workarounds have been published which enabled the affected hardware (the Banias part of the Pentium M family) to run the latest Buntus.

From 14.04 the boot option **forcepae** has been added, which eliminates the need for these workarounds. More [here]("https://help.ubuntu.com/community/PAE").

I suggest that when people encounter a PAE related question they spread the word and point to Lubuntu 14.04 and the boot option, provided that the person asking is willing to run a beta version, of course.

---

### Post by sanderj on 2014-03-17
Thank you for your post. Useful.

FWIW: that page says 

> Now a string of options is visible, often with '--quiet' or '--quiet splash' at the end.

I checked the boot options, and it says "quiet splash --", which is something else I would say: no '--' before 'quiet'

FWIW2: I tried "forcepae" as boot options, and dmesg says

```
PAE forced!
```

HTH

---

### Post by sudodus on 2014-03-17
> **mörgæs said:**
> For almost two years, or since Ubuntu 12.04 was released, there has been a steady stream of posts about PAE and related problems. 

12.04 was the first Ubuntu for which a special non-PAE version wasn't available. X/Lubuntu carried on supporting non-PAE processors for one release more, making 12.10 their first PAE-only release.

Several workarounds have been published which enabled the affected hardware (the Banias part of the Pentium M family) to run the latest Buntus.

From 14.04 the boot option **forcepae** has been added, which eliminates the need for these workarounds. More [here]("https://help.ubuntu.com/community/PAE").

I suggest that when people encounter a PAE related question they spread the word and point to Lubuntu 14.04 and the boot option, provided that the person asking is willing to run a beta version, of course.

+1

Soon we can spend our efforts on other tasks :-)

---

### Post by deadflowr on 2014-03-17
This thread should be stickied when 14.04 is finally released.
I myself, have bookmarked it, as well as the wiki.

---

### Post by mörgæs on 2014-03-17
Thanks everybody :-)

Sanderj, feel free to edit the wiki page if something is not correct. Goes for the English language as well...

---

### Post by sanderj on 2014-03-17
> **mörgæs said:**
> Sanderj, feel free to edit the wiki page if something is not correct. Goes for the English language as well...

Done. Thanks.

---

### Post by mörgæs on 2014-03-20
After an install built on forcepae the output of **lshw** or similar shows a CPU description which contains PAE, for example 

     ```
product: Intel(R) Pentium(R) M processor 1500MHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.9.5
          size: 1500MHz
          capacity: 1500MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 tm pbe bts est tm2 cpufreq
```


This might lead to incorrect statements like 'see, I already had PAE, so why did you want me to add the boot option?' 

Just for stating the obvious, the PAE flag is not output from the processor itself, it comes from a software modification of the output. When helping beginners we might need to explain this more than once.

---

### Post by devzero-c on 2014-03-20
hi, i`m one of the guys who worked on this solution, it`s not a problem that the flag is inserted by software, as that insertion only takes place on processors which are pae capable. there are many pentium M which actually CAN do PAE, but the don`t correctly tell about, i.e. if you ask those cpu for their capabilities they won`t tell that they have PAE - and that´s the reason why a PAE kernel won`t boot on such cpu`s. so, just force it and things go smooth again. and to have a smooth upgrade path, forcepae also fixes the missing-pae-flag in /proc/cpuinfo problem (as update packages check for it)

---

### Post by mörgæs on 2014-03-20
Thousands of Banias users owe you a big thank you :-)

---

### Post by dave9469 on 2014-04-26
I have a viglen MCP and I'm trying to install the latest Lubuntu. I got the pae error and found this thread so added forcepae after the -- in the boot options but I still get the message "This Kernel requires the following features not present on the CPU:pae"

Does anybody know why and is there a work round. I'm using the lubuntu-14.04-desktop-i386 iso on a USB stick.

---

### Post by mörgæs on 2014-04-26
For the Banias processors the problem is that there's PAE capability but no indication of that. Adding a fake PAE flag solves the problem.

If [this]("https://wiki.ubuntu.com/ViglenMPC") is our guy it has a Geode processor unrelated to Banias. I believe (but am not sure) that is lacks PAE capability, not only the flag. 

I suggest that you try the non-PAE version of Bodhi Linux, but it's an oddball processor and I can't promise that it will work. 

Be aware that it is weak hardware regardless of which operative system you are able to run.

---

### Post by sudodus on 2014-04-27
If you are interested in trying the new Ubuntu Trusty with a non-pae kernel, you can install a minimal text only 'flavour' with the experimental 9w installer. After installing and rebooting you can add a window manager or light desktop environment.

See this link

[I uploaded a 9w installer file so that ***you*** can also test the non-pae kernel now ]("http://ubuntuforums.org/showthread.php?t=2216356&page=2&p=13003216#post13003216")

- Please get the iso file [SIZE=3]**[FONT=courier new]Trusty-npae124-text.iso[/FONT]**[/SIZE] from

[http://phillw.net/isos/linux-tools/9w/](http://phillw.net/isos/linux-tools/9w/)

-o-

But there might be issues with some hardware driver that has been dropped in Ubuntu Trusty, so that you will have better luck with ***Bodhi*** as adviced by *mörgæs*, or with ***Bento*** or ***LXLE***, which are re-spins from the same fundament, Ubuntu 12.04 LTS. If your computer has less than 512 MB RAM, you should also try some ultra-light linux distros, for example DSL, Puppy and Tiny Core.

---

### Post by daileng on 2014-10-18
> **dave9469 said:**
> I have a viglen MCP and I'm trying to install the latest Lubuntu. I got the pae error and found this thread so added forcepae after the -- in the boot options but I still get the message "This Kernel requires the following features not present on the CPU:pae"

Does anybody know why and is there a work round. I'm using the lubuntu-14.04-desktop-i386 iso on a USB stick.

As stupid as it sounds I got this message when I put in "forcepae" immediately after the "--" so it read "--forcepae" like you might expect for a command flag BUT I was 100% positive that mine supported PAE so I tried putting a space so it read "-- forcepae" and was able to run the installation :-D

---

