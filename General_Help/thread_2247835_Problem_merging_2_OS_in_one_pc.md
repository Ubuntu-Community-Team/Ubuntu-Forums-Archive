---
title: "Problem merging 2 OS in one pc"
date: 2014-10-10
forum: General Help
---

### Post by joonwo on 2014-10-10
hello,
i recently installed ubuntu 14.04 on a new SSD and it's great.
but sometimes i still need to work with solid edge (a windows programm). 

My 17" Laptop can hold 2 harddrives. So i want to put Linux and Windows 7 in this laptop. 
i installed them both separately on 2 different SSD. 
right now when i switch between the systems i just go into my bios and change the boot order.
but that's quite inconvenient.

what is the best way to go ? i already read grub, easyBCD, etc.

---

### Post by sudodus on 2014-10-10
I have such dual boot systems, in one as well as more than one drive. I suggest that you use grub for selecting which OS to boot.

If both systems are installed in BIOS or both in UEFI and both drives are connected, you can run the following terminal window command in Ubuntu

```
sudo update-grub
```

and it should create an entry also for Windows in the grub menu.

If one system is installed in BIOS and the other in UEFI, you must continue like you do now, or re-install one of the systems. (It is probably easier to re-install Ubuntu.) UEFI needs the GPT partition table (not the old standard MSDOS partition table).

---

### Post by joonwo on 2014-10-10
> **sudodus said:**
> I have such dual boot systems, in one as well as more than one drive. I suggest that you use grub for selecting which OS to boot.

If both systems are installed in BIOS or both in UEFI and both drives are connected, you can run the following terminal window command in Ubuntu

```
sudo update-grub
```

and it should create an entry also for Windows in the grub menu.

If one system is installed in BIOS and the other in UEFI, you must continue like you do now, or re-install one of the systems. (It is probably easier to re-install Ubuntu.) UEFI needs the GPT partition table (not the old standard MSDOS partition table).

thanks for fast reply! i have some questions about grub.
i am a little bit concerned about grub because i might not keep my windows ssd in my laptop for long. i am building a desktop soon and want to use my windows drive for it.  i read that grub messes up your windows master boot record.
i am afraid after using grub and then removing the windows drive will give the windows ssd trouble starting in the new desktop pc. 

Is that the case ?

---

### Post by sudodus on 2014-10-10
If both systems are running in BIOS, things are straight-forward, and doing what I suggested would not mess with the Windows drive at all, and it would work.

If both systems are running in UEFI, doing what I suggested would not mess with the Windows drive at all,but it might not work. There are mechanisms on the Windows side that change what I think should not be changed by operating systems.

On the other hand, your installed Windows will most likely fail, if you simply move its drive to another computer. You need to make a new installation, which is possbile if you have a full and flexible Windows version. If you have an OEM Windows version, it is probably locked to the laptop, where you run it now.

---

