---
title: "Hyperthreading in Ubuntu 8.04"
date: 2008-04-27
forum: General Help
---

### Post by ubockto on 2008-04-27
How do I enable it? I have tried to edit the lilo.conf, but that file doesnt exist, unless it is hidden

---

### Post by chewit on 2008-04-27
what graphics card are you using?

---

### Post by ubockto on 2008-04-27
Nvidia Geforce 7600gs, has that any relevance?

---

### Post by bettlebrox on 2008-04-27
I think U need to install a SMP kernel.

---

### Post by ubockto on 2008-04-27
And how do I do that?

---

### Post by ubockto on 2008-04-28
*bump*

---

### Post by rubicon on 2008-04-28
Tell us please, why do you think HT is disabled by default?

---

### Post by ubockto on 2008-04-28
Because I had the function in windows vista and xp with the same processor

---

### Post by sloggerkhan on 2008-04-28
None of the posts in this thread seem to make coherent sense in relation to each other.

---

### Post by fasten on 2008-04-28
Hi,

To check if your CPU is hyperthreading capable, check if there's the "ht" flag in the output of ```
cat /proc/cpuinfo
```

If there's the "**ht**" flag, and only 1 cpu available, then it means hyperthreading is probably disabled in the BIOS.
Hyperthreading works when the ouput of 'cat /proc/cpuinfo' counts 2 CPUs (in the case of a mono-cpu config, obviously.)

On the same machine with a hyperthreading-capable CPU ("ht" flag):

_Hyperthreading enabled machine:_
```

# cat /proc/cpuinfo | grep processor
processor       : 0
processor       : 1

```

_Hyperthreading disabled :_
```
 $ cat /proc/cpuinfo | grep processor
processor       : 0

```

Cheers,
Stef

---

### Post by ubockto on 2008-04-28
For some strange reasons, that file is blank, unless I am doing something wrong, considering that I am a noobie, it is more likely that I am doing something wrong here, so anyway I can open this through the terminal?

---

### Post by ubockto on 2008-04-28
> **sloggerkhan said:**
> None of the posts in this thread seem to make coherent sense in relation to each other.

Don't blame me, I am asking the questions, they keep asking what kind of graphics card I have, what thats got to do with Hyper-threading on the cpu, I dont know:confused:

---

### Post by kostkon on 2008-04-28
Firstly, you can simply go to *System -> Adminstration -> System Monitor* and check if in the *Resources* tab you can see 2 processors instead of 1.

---

### Post by ubockto on 2008-04-28
> **kostkon said:**
> Firstly, you can simply go to *System -> Adminstration -> System Monitor* and check if in the *Resources* tab you can see 2 processors instead of 1.

Can only see one, but I know this is a Hyper-threading cpu, since I have used it in XP and Vista, and they both "saw" it

---

### Post by mc4man on 2008-04-28
you should go back to post by fasten and paste that command into the terminal. I have a ht cpu and Hyperthreading  is enabled. (as long as it's enabled in bios)

---

### Post by ubockto on 2008-04-28
> **fasten said:**
> Hi,

To check if your CPU is hyperthreading capable, check if there's the "ht" flag in the output of ```
cat /proc/cpuinfo
```

If there's the "**ht**" flag, and only 1 cpu available, then it means hyperthreading is probably disabled in the BIOS.
Hyperthreading works when the ouput of 'cat /proc/cpuinfo' counts 2 CPUs (in the case of a mono-cpu config, obviously.)

On the same machine with a hyperthreading-capable CPU ("ht" flag):

_Hyperthreading enabled machine:_
```

# cat /proc/cpuinfo | grep processor
processor       : 0
processor       : 1

```

_Hyperthreading disabled :_
```
 $ cat /proc/cpuinfo | grep processor
processor       : 0

```

Cheers,
Stef

Ok, thanks its says the one with the Hyperthreading disabled

---

### Post by ubockto on 2008-04-28
> **mc4man said:**
> you should go back to post by fasten and paste that command into the terminal. I have a ht cpu and Hyperthreading  is enabled. (as long as it's enabled in bios)

How did you enable yours then?

---

### Post by mc4man on 2008-04-28
When you boot up usually there is a quick message in corner usually like 
F2 setup
F12 boot menu
You want setup - the keys aren't standard if you don't see anything start with F2 key and work your way up  (start tapping key right as boot up begins)
You should see way to set ht in the bios setting -don't make changes at random

edit: usually you only get one chance to get right key per boot
reedit - if you don't see setting for ht try hitting key for enable or reset defaults - you'll usually see list at top/bottom of bios screen

---

### Post by ubockto on 2008-04-28
> **mc4man said:**
> When you boot up usually there is a quick message in corner usually like 
F2 setup
F12 boot menu
You want setup - the keys aren't standard if you don't see anything start with F2 key and work your way up  (start tapping key right as boot up begins)
You should see way to set ht in the bios setting -don't make changes at random

edit: usually you only get one chance to get right key per boot
reedit - if you don't see setting for ht try hitting key for enable or reset defaults - you'll usually see list at top/bottom of bios screen

I know how to access the BIOS, I have been doing that for the last 5 years, but there is no option to enable the hyperthreading, since its been like it since I have bought it

---

### Post by ubockto on 2008-04-28
Ah, this has something to do with ACPI?

EDIT: Yup, sure has, enabled acpi in my BIOS system, then edited the GRUB bootloader to include the line acpi=ht

source: [https://wiki.ubuntu.com/DebuggingACPI](https://wiki.ubuntu.com/DebuggingACPI)

---

### Post by x001 on 2008-04-28
In the BIOS screen does it list the manufacturer/model of the processor?

---

### Post by ubockto on 2008-04-28
> **x001 said:**
> In the BIOS screen does it list the manufacturer/model of the processor?

Yuh, its an intel P4 3000Mhz (3.0ghz) etc. I ahve booted up with the acpi=ht in the grub boot manager, but that is a temporary solution, but is there a way to make that permanent?

---

### Post by x001 on 2008-04-28
You should modify:  /boot/grub/menu.lst

Check out: [https://help.ubuntu.com/community/BootOptions]("https://help.ubuntu.com/community/BootOptions")

---

### Post by mc4man on 2008-04-28
from link
> try booting with "acpi=ht"

This disables all of ACPI except just enough to enable Hyper Threading


The logic being you just enabled ACPI in bios - why disable it except for ht
Have you checked without that line ie with just the new bios setting
note - sorry about bios instr. tend to assume newbie at times

---

### Post by ubockto on 2008-04-28
thanks, much appreciated, it works now

---

### Post by ubockto on 2008-04-28
> **mc4man said:**
> from link

The logic being you just enabled ACPI in bios - why disable it except for ht
Have you checked without that line ie with just the new bios setting
note - sorry about bios instr. tend to assume newbie at times

the fact is, if I did that without the acpi=ht, it wouldnt of installed at all, then it wouldnt boot up

---

### Post by ubockto on 2008-04-29
the only problem now, is it wont shut down properly, lol

---

