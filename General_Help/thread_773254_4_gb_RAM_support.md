---
title: "4 gb RAM support?"
date: 2008-04-28
forum: General Help
---

### Post by ZeldaFan on 2008-04-28
Is there support for 4 GB of RAM on my laptop with 32 bit Ubuntu Hardy Heron, or does it have to be 64-bit?

---

### Post by damis648 on 2008-04-28
it must be 64-bit, 32-bit will only recognize 3.5 gb. I have 4 gb installed, however i was getting funky errors when trying to install ubuntu x64 so i am using x32 and i get 3.5 gb which isnt bad.

PS. I know my processor supports 64 bit so dont even ask :P

---

### Post by seamuso on 2008-04-28
pretty much 64bit .. The 160GB drive in my signature has hard x32 installed (was my linux drive in my previous machine) .. when I booted it in my current system, I saw a nice 2.5GB of my 4GB

---

### Post by reiki on 2008-04-28
4 GB will probaly be seen as 3.2 or 3.2 ... something like that. If you want to see all 4 you'd need 64-bit

---

### Post by dschaller on 2008-04-28
I haven't tried it myself, but if you compile your own kernel, I believe you can then configure it to see 4gb on a 32-bit system. See this thread:

[http://ubuntuforums.org/showthread.php?t=574494](http://ubuntuforums.org/showthread.php?t=574494)

---

### Post by ZeldaFan on 2008-04-28
Thanks for the replies. But for some features of 64-bit, such as flash and what not, doesn't ubuntu use 32-bit software. As a result, it should not be able to use all 4 gb of RAM, correct? And also, is the amount of RAM visible to me with 32 bit variant or should it be the same for everybody? Because I am probably going to install 64 bit ubuntu hardy on a portable external hard drive but on my primary internal hard drive, I have 32 bit vista installed. I wonder how much RAM will be supported under that OS.

---

### Post by Spenzer4Hire on 2008-04-28
I'm no expert but here goes:

Yes, some software in the 64 bit Ubuntu is 32 bit, but it is running in a compatibility mode (using 32 bit libraries) or in other cases a wrapper.  Ubuntu 64 bit can see over 4 GB but any of the 32 bit applications running inside of it can't use more than 4 GB each.

Each little block of RAM is numbered.  When you hit 4 GB the number becomes too large to fit in 32 bits.  So, in a 32 bit OS the entire OS can't address more than 4 GB of RAM, but in a 64 bit OS the addressable limit is much much higher.  The 32 bit addressable limit is then applied to each 32 bit application individually, I think.

Also, don't quote me on this, but I think the 4 GB limit includes swap space (and maybe the page file in Windows?).  So if I have that right, your usable RAM is 4 GB minus the size of your swap partition.  I think a similar rule applies to Windows, but I'm not really sure.

---

### Post by ebelog on 2008-04-29
> **Spenzer4Hire said:**
> I'm no expert but here goes:

Yes, some software in the 64 bit Ubuntu is 32 bit, but it is running in a compatibility mode (using 32 bit libraries) or in other cases a wrapper.  Ubuntu 64 bit can see over 4 GB but any of the 32 bit applications running inside of it can't use more than 4 GB each.

Each little block of RAM is numbered.  When you hit 4 GB the number becomes too large to fit in 32 bits.  So, in a 32 bit OS the entire OS can't address more than 4 GB of RAM, but in a 64 bit OS the addressable limit is much much higher.  The 32 bit addressable limit is then applied to each 32 bit application individually, I think.

Also, don't quote me on this, but I think the 4 GB limit includes swap space (and maybe the page file in Windows?).  So if I have that right, your usable RAM is 4 GB minus the size of your swap partition.  I think a similar rule applies to Windows, but I'm not really sure.


A 32-bit OS can address about 4GB of memory total. That includes the normal memory as well as the video RAM. Some memory is also reserved by the kernel and doesn't show up as available, and that's why you'll likely see only 3 to 3.5 GB of memory even if you have 4 GB installed. The swap partition doesn't factor into that limitation.

There are versions of the Linux kernel which allow a 32-bit OS to utilize more than 4GB of RAM, but I don't know if Ubuntu has a packaged version. If not, you're probably better off going with the 64 bit version rather than the alternative of compiling your own kernel.

---

### Post by FredB on 2008-04-29
The simplest way to use 4 Gb = 64 bits distro.

Flash is known to be a firefox 3 killer right now. So, if you want 64 bits, just give swfdec a chance.

---

### Post by Trebaruna on 2008-04-29
According to Ubuntu's website the server edition is compiled with PAE (Physical Address Extension) which will allow a 32-bit kernel to address up to 64GB of RAM.
Of course, this does mean you have to install quite a lot of packages by hand as server does not install X, OpenOffice or a lot of other tools included in the desktop.

---

### Post by tliotis on 2008-04-29
in 32bit system the 4Gb ram will be = 3.25 clean ram, if you have vga onboard then will be less than 3,25

---

### Post by jespdj on 2008-04-29
32-bit software also works on 64-bit Ubuntu.

You do need 64-bit Ubuntu or 32-bit with a [PAE]("http://en.wikipedia.org/wiki/Physical_Address_Extension")-enabled kernel to be able to use the full 4 GB. Compiling your own PAE-enabled kernel is probably not the easiest option.

> **FredB said:**
> Flash is known to be a firefox 3 killer right now. So, if you want 64 bits, just give swfdec a chance.
Not really true. I don't have any problems with running Flash on 64-bit Ubuntu 8.04 on Firefox 3b5. Installing Flash in 64-bit Hardy is just as easy as in 32-bit Hardy:
```
sudo apt-get install flashplugin-nonfree
```

---

### Post by Vivaldi Gloria on 2008-04-29
> **tliotis said:**
> in 32bit system the 4Gb ram will be = 3.25 clean ram, if you have vga onboard then will be less than 3,25

I can use close to 3.5 GB:

```
hasan@narval:~$ cat /proc/meminfo
MemTotal:      3631012 kB
...
```

---

### Post by free2useemail on 2008-04-29
No, sorry. Not possible. ALSO, make sure your processer can reconise 4gb of ram, most processer's can't.

---

### Post by jespdj on 2008-04-29
> **free2useemail said:**
> No, sorry. Not possible. ALSO, make sure your processer can reconise 4gb of ram, most processer's can't.
Sorry free2useemail, but both your statements are false.

To be able to use the full 4 GB, you do have to have a processor that supports PAE (see the posts above) or that supports 64-bit extensions. Most AMD and Intel processors from the past two years or so support these. PAE is a trick that enables the processor to use more than 4 GB RAM (up to 64 GB) in 32-bit mode.

32-bit processors (or 64-bit processors running in 32-bit mode) can address at most 4 GB RAM, but a part of the address space is reserved for devices like the video card, chipset etc., so you can't actually use the full 4 GB.

---

### Post by GiSWiG on 2008-04-29
Sorry if I can't provide more details at the moment, but openSUSE 10.3 (and so did 10.2) 32-bit on my 4GB machine sees 4GB of RAM. I'm going to give Kubuntu 8.04 a try and would like the same. So it should be possible. My question would be how? Without re-compling the kernel, if according to previous posts that the (K)ubuntu kernel has PAE support.

---

### Post by ZeldaFan on 2008-04-29
I have a Core 2 Duo processor, which is 64-bit, correct? But my laptop also has the Intel i945 mobile chipset (I have an HP dv9000t series laptop) which I heard cannot use 4 gb of RAM. Is that true?

---

