---
title: "DualBooting and Windows 7 bootloader question"
date: 2014-03-01
forum: General Help
---

### Post by sonyboyj on 2014-03-01
if i dual boot using this tutorial [http://www.instructables.com/id/How-to-Dual-boot-Linux-and-Windows-on-a-PC-with-W/](http://www.instructables.com/id/How-to-Dual-boot-Linux-and-Windows-on-a-PC-with-W/)  and if i dont like Linux i can delete the linux partition and give it  back to windows but im told Windows wont boot after deleteing linux and  ill need a Disk to fix the boot loader if this true or will windows boot  fine. i wanna be able to if i dont want ubuntu any more give the partiton or shirinked volume back to Windows which i know i can. But i want my PC to boot in to windows next time around will it do so

---

### Post by OrangeCrate on 2014-03-01
> **sonyboyj said:**
> if i dual boot using this tutorial [http://www.instructables.com/id/How-to-Dual-boot-Linux-and-Windows-on-a-PC-with-W/](http://www.instructables.com/id/How-to-Dual-boot-Linux-and-Windows-on-a-PC-with-W/)  and if i dont like Linux i can delete the linux partition and give it  back to windows but im told Windows wont boot after deleteing linux and ** ill need a Disk to fix the boot loader** if this true or will windows boot  fine. i wanna be able to if i dont want ubuntu any more give the partiton or shirinked volume back to Windows which i know i can. But i want my PC to boot in to windows next time around will it do so

That's correct. I'm not at a Windows computer right now, and I haven't used an installation disk for a while, so, I don't remember exactly how to get to the CMD prompt, but here's the instruction you'd enter at the prompt, to return the boot to windows.

```
bootrec.exe /fixmbr
```

Search for articles that contain that instruction, and they will give you any other details you're lacking...

Edit:

Did it for you, here you go:

[http://windows7themes.net/how-to-fix-mbr-in-windows-7.html](http://windows7themes.net/how-to-fix-mbr-in-windows-7.html)

---

### Post by sonyboyj on 2014-03-01
> **OrangeCrate said:**
> That's correct. I'm not at a Windows computer right now, and I haven't used an installation disk for a while, so, I don't remember exactly how to get to the CMD prompt, but here's the instruction you'd enter at the prompt, to return the boot to windows.

```
bootrec.exe /fixmbr
```

Search for articles that contain that instruction, and they will give you any other details you're lacking...

Edit:

Did it for you, here you go:

[http://windows7themes.net/how-to-fix-mbr-in-windows-7.html](http://windows7themes.net/how-to-fix-mbr-in-windows-7.html)

i dont have a actuall Windows disk its a recovery one that i made cause HP didnt give one and said to use the recovery program to make one. but once i get into windows and enter this command will i boot normal from then on or do i need to do this forever

---

### Post by OrangeCrate on 2014-03-01
> **sonyboyj said:**
> i dont have a actuall Windows disk its a recovery one that i made cause HP didnt give one and said to use the recovery program to make one. but once i get into windows and enter this command will i boot normal from then on or do i need to do this forever

When I've done this from a disk (I have a full retail version of Windows 7 for one of our computers), it only required it once from the command line. If you're opting to use the F8 instruction while you're already in Windows, I would assume you only need to do it once. I've never tried that option, so, I'm not completely sure. Hopefully someone else, more familiar with modern Windows releases, can confirm for you...

---

### Post by sonyboyj on 2014-03-01
Thanks for all the help

---

### Post by OrangeCrate on 2014-03-02
> **sonyboyj said:**
> Thanks for all the help

You're welcome, sorry I couldn't have helped more.

---

