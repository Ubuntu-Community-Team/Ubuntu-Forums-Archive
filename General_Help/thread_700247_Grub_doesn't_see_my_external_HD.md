---
title: "Grub doesn't see my external HD"
date: 2008-02-18
forum: General Help
---

### Post by mercedesj on 2008-02-18
- I installed Wubi 7.10 on my second external HD (NFTS system file), and   it seems that was OK. I have Windows XP. The  2 HD is new, the first think that I do is install Wubi.

- I reboot my notebook and I choose the option UBUNTU-LINUX and ...

- I have the error:
   find --set-root-- ignore-floppies /ubuntu/install/boot/grup/menu.lst
   Error 17: File not found
  However the file exits!!!

- It seem that grub doesn't see the external HD.
  If I write in the commandline: "root (hd1,0)"
  I have  "error 26: Selected disk does not exists"

[B]
Anyone has any idea ? I don't know what to do!!![/B]

---

### Post by gla22 on 2008-02-24
yeah i have the same problem here is my boot.ini if that is the problem
```

[boot loader]
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
timeout=15
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional Edition" /fastdetect /NoExecute=OptIn /TUTag=RKM5NZ
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="OS for testing new boot screen" /fastdetect /NoExecute=OptIn /TUTag=RKM5NZ /KERNEL=NewBoot.exe
C:\wubildr.mbr="Ubuntu"

```

any suggestions, should I change C:\wubildr.mbr to the directory that my external HD is?

edit:So I changed my bios settings to load the external hard drive first and I get an error 17. Any help?

I have wubi on partition #3 of my external hard drive. So it should be sda(something, 3). What do i change?

---

### Post by ago on 2008-02-24
Can you please try 8.04? It is possible though that external drives are not supported by bios/bootloader.

---

