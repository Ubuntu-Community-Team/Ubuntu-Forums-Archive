---
title: "New install only sees half of my RAM"
date: 2015-04-09
forum: General Help
---

### Post by annandul on 2015-04-09
I just installed Lubuntu from the 14.04 Ubuntu netinst image on my Acer C720, and it appears that only half of my 2GB of ram is being seen or used. Top, the Task Manager, and the System Profiler and Benchmark applications all report somewhere around 1GB. How do I troubleshoot this?

Thanks in advance.

---

### Post by sandyd on 2015-04-10
Hi, can you post the output of
```

sudo lshw
```
please?

Thanks.

---

### Post by kerry_s on 2015-04-10
> **annandul said:**
> I just installed Lubuntu from the 14.04 Ubuntu netinst image on my Acer C720, and it appears that only half of my 2GB of ram is being seen or used. Top, the Task Manager, and the System Profiler and Benchmark applications all report somewhere around 1GB. How do I troubleshoot this?

Thanks in advance.

have you tried opening her up make sure both ram are fully seated ?

---

### Post by annandul on 2015-04-10
> **sandyd said:**
> Hi, can you post the output of
```

sudo lshw
```
please?

Thanks.

Here it is, thanks!: [http://pastebin.com/ws2bsft6](http://pastebin.com/ws2bsft6) 


[QUOTE=kerry_s]
have you tried opening her up make sure both ram are fully seated ?
[/QUOTE]

It's a laptop with RAM that's soldered in.

---

### Post by matt_symes on 2015-04-10
Hi

> 
*-memory           description: System memory

           physical id: 1

           size: 992MiB

It's only seeing 1G of memory as you say.

Can you also post the output of (Capital M above).

```
dmesg | grep Memory
```

Also can you run this command

```
sudo apt-get install dmidecode
```

and then post the output of this command

```
sudo dmidecode -t memory
```

Kind regards

---

### Post by kerry_s on 2015-04-10
how much ram is showing in your bios ? just to rule out bad ram.

---

### Post by annandul on 2015-04-11
I'm on mobile, afk, will try those commands when I'm home. As far as I am aware my Chromebook won't give me a BIOS display of RAM.

---

### Post by kerry_s on 2015-04-11
the fact that it's a chromebook should have been told up front.

---

### Post by annandul on 2015-04-11
Output of  "dmesg | grep Memory"
```
[    0.000000] Memory: 994060K/1047092K available (8148K kernel code, 1137K rwdata, 3920K rodata, 1420K init, 1292K bss, 53032K reserved, 0K cma-reserved)
[    3.604507] [drm] Memory usable by graphics device = 2048M

```

dmidecode, with or without switches, returns "/dev/mem: No such file or directory"

Thanks for the continued help!


EDIT: Tried running the same commands in an Arch live environment (Arch is what I was previously running before wanting to switch to Lubuntu), got different results. All of this was written down by hand and typed back up, I may have made an error.

lshw had this in its output:
```
*-memory
description: system memory
physical id: 1
size: 1879 MiB

```

dmidecode +t memory:
```
#dmidecode 2.12
SMBIOS 2.7 present

```

dmesg | grep Memory
```
[0.0...] Memory: 1900682k/2035732k available (5481k kernel code, 908k rwdata, 1720k rodata, 1160k init, 1184 bss, 135040k reserved)
[4.05....] [drm] Memory usable by graphics device = 2048 M

```

Now I'm left more bewildered than before. I'll try running a memory test, see if the stick of RAM is failing somehow.

---

### Post by matt_symes on 2015-04-15
Hi

Sorry for th late reply. Life has a habit of getting in the way.

Maybe something different between the two kernels on Arch and Ubuntu ? Is Arch using a newer kernel ? That would be my bet.

What kernel version are Arch and Ubuntu running ? 

From both the Arch and Ubuntu command line...

```
uname -r
```

The simple answer is to use Arch. A fine distro in itself.

If not you can use on of the mainline Ubuntu kernels like i am (i'm slightly behind as 4.0 has been released but i don't want to reboot this lappy yet) ....
```

matthew-laptop:/home/matthew:1 % cat /etc/lsb-release&& uname -r
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.2 LTS"
4.0.0-040000rc7-generic
matthew-laptop:/home/matthew:1 % 
```

They can be found here...

[http://kernel.ubuntu.com/~kernel-ppa/mainline/#](http://kernel.ubuntu.com/~kernel-ppa/mainline/#)

...****but make sure the hardware is compatible****.

Kind regards

---

