---
title: "Wrong amount of RAM displayed ?"
date: 2018-05-25
forum: General Help
---

### Post by rouvenster on 2018-05-25
So I have this old computer I just decided to re-use but this time with kubuntu. 
It has a Gigabyte EP45-DS3 motherboard with 4 sticks of 1GB DDR2.

When I turn on the computer, it shows "1024GB RAM" on the post info along with some stuff about my devices and GPU. I was worried, but after installing Kubuntu I ran the command :
```

$ free -m
               total        used        free      shared  buff/cache   available
Mem:           3943        1983         115          78        1845        2000
Swap:          7627           0        7627
```

So I guess the system is using the right amount, but should I consider flashing the BIOS, knowing that this is a pain in the ass to do on a Linux distro (only .exe bios files from Gigabyte) ? Or maybe it doesn't matter the BIOS shows wrong stuff ?
Thanks

---

### Post by mörgæs on 2018-05-25
I doubt it's necessary but flashing a BIOS from a USB stick with Freedos is easy, especially for old computers.

---

### Post by kazakore on 2018-05-25
> **mörgæs said:**
> I doubt it's necessary but flashing a BIOS from a USB stick with Freedos is easy, especially for old computers.

Should be easy using Q-Flash for his motherboard. Whether it's worth the risk when the OS sees the correct amount of RAM is another matter....

[https://www.manualslib.com/manual/358889/Gigabyte-Ga-Ep45-Ds3.html?page=74#manual](https://www.manualslib.com/manual/358889/Gigabyte-Ga-Ep45-Ds3.html?page=74#manual)

---

### Post by Yellow Pasque on 2018-05-25
I wouldn't worry about it since 'free' is showing about 4GB.

---

### Post by rouvenster on 2018-05-26
Thank you everyone, the problem with this motherboard was that Gigabyte only provides .exe BIOS files when ironically qFlash looks for "pure" BIOS files. I managed to find one on a non official website and flashed it but nothing changed. I guess I should not worry though.

---

### Post by kazakore on 2018-05-26
> **rouvenster said:**
> Thank you everyone, the problem with this motherboard was that Gigabyte only provides .exe BIOS files when ironically qFlash looks for "pure" BIOS files. I managed to find one on a non official website and flashed it but nothing changed. I guess I should not worry though.

Using the latest stable BIOS, F9, from: [https://www.gigabyte.com/Motherboard/GA-EP45-DS3-rev-10#support-dl-bios](https://www.gigabyte.com/Motherboard/GA-EP45-DS3-rev-10#support-dl-bios)

You can download the .exe file then extract the contacts using an Archive Manager. This gives you three files: autoexec.bat, ep45ds4.f9 & FLASHSPI.EXE

Once you have done that follow the instructions on the page in the manual I linked to earlier, using the ep45ds4.f9 file. Well if you think it's really worth it as your system does seem to be working correctly.....

Not many manufacturers let you know that you can usually extract the .exe and .msi files to get the actual bios file itself but I've found it's fairly common ;)

---

### Post by rouvenster on 2018-05-28
> **kazakore said:**
> Using the latest stable BIOS, F9, from: [https://www.gigabyte.com/Motherboard/GA-EP45-DS3-rev-10#support-dl-bios](https://www.gigabyte.com/Motherboard/GA-EP45-DS3-rev-10#support-dl-bios)

You can download the .exe file then extract the contacts using an Archive Manager. This gives you three files: autoexec.bat, ep45ds4.f9 & FLASHSPI.EXE

Once you have done that follow the instructions on the page in the manual I linked to earlier, using the ep45ds4.f9 file. Well if you think it's really worth it as your system does seem to be working correctly.....

Not many manufacturers let you know that you can usually extract the .exe and .msi files to get the actual bios file itself but I've found it's fairly common ;)

Wow, thank you, I will definitely try that.

---

