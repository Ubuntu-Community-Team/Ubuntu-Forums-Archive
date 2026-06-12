---
title: "why does this work? 2 different computers"
date: 2016-09-09
forum: General Help
---

### Post by wepage on 2016-09-09
I have been using 16.04 on an asrock (i5) motherboard system. I attached the boot drive to an older zotac (atom) computer and it booted up and worked fine.
Can I always switch an ubuntu 16.04 boot drive between different computers like this?  seems amazing.

---

### Post by sudodus on 2016-09-09
Well, yes, within certain limits :-)

PC computers with Intel and AMD processors work with the same program code. But there are 32-bit and 64-bit computers. 64-bit computers work with 32-bit program code, but 32-bit computers do not work with 64-bit program code. You have probably noticed, that there are two sets of iso files, i386 alias 32-bit, and amd64 alias 64-bit. (amd64 code works with both AMD and Intel processors, it is only a name for 64-bit code for PC computers).

But computers with arm processors, like Raspberry PI, and computers with powerpc processors, like old Apple computers, do not work with PC iso files.

So the basic architecture of the PC computers is the same in many computers. But there are other obstacles. The reason why linux is so portable compared with Windows is that linux has built-in drivers, that are bundled with the kernel, and there is automatic detection of a lot of hardware components. But there are exceptions, for example some chips/cards for graphics and wifi need proprietary drivers (with secret source code), and it is the same with many peripheral devices like printers and scanners.

There is also a complication with UEFI and BIOS, where UEFI is the new, more complicated and less standardized method for booting. Or should I say, some companies do not follow the standards, which makes it difficult for us to figure out how to boot and how to install linux.

-o-

Not only the live systems but also installed linux systems are portable, if you avoid proprietary drivers.

You can find more about this subject at the following link and links from it: [Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](https://ubuntuforums.org/showthread.php?t=2230389)

---

### Post by wepage on 2016-09-09
Thank you Sudodus. Very informative for a windows user.

---

### Post by sudodus on 2016-09-09
You are welcome :-)

---

