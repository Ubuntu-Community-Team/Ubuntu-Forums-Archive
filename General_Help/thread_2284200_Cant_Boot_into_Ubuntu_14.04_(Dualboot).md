---
title: "Cant Boot into Ubuntu 14.04 (Dualboot)"
date: 2015-06-27
forum: General Help
---

### Post by Jazlaan on 2015-06-27
hi guys,

I did a dual boot with windows 8.1

Most of it did go well. But I couldnt book back into Ubuntu.
Tried the boot-repair

here's my link

```
http://paste.ubuntu.com/11785015/
```

I followed this tutorial

```
http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html#comment-form
```

My ubuntu version is 14.04.2
Thankyou!

---

### Post by oldfred on 2015-06-27
What model Acer?
But all others with any model Acer have UEFI that require you to set a password( never lose that) and then you can enable trust or allow your Ubuntu to boot.

       Acer Aspire ES1-512-C39M Details on password and settings to enable trust on ubuntu entries Also R14 model same fix
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)
Acer S7 14.04 & Windows 8.1 RAID
[http://askubuntu.com/questions/590644/install-ubuntu-14-04-2-lts-alongside-windows-8-1-dual-boot-on-raid-acer-s7-quest](http://askubuntu.com/questions/590644/install-ubuntu-14-04-2-lts-alongside-windows-8-1-dual-boot-on-raid-acer-s7-quest)

 Acer Aspire ES1-512: ubuntu 14LTS USB install over Windows 8.1  Set shim as secure in UEFI
black list some drivers for shutdown issues - post #9 link to Mint
[http://ubuntuforums.org/showthread.php?t=2256083](http://ubuntuforums.org/showthread.php?t=2256083)
Acer E3 requires UEFI password to allow added settings Post #8
[http://ubuntuforums.org/showthread.php?t=2253311](http://ubuntuforums.org/showthread.php?t=2253311)

Aspire E1-522 InsydeH20 Bios unlock -  7 min video
[https://www.youtube.com/watch?v=7SkBFkzOW0A](https://www.youtube.com/watch?v=7SkBFkzOW0A)

---

### Post by Jazlaan on 2015-06-27
Acer V11 Touch (V3-112P-C3YY)

It's a total mess now. :(

---

### Post by oldfred on 2015-06-27
Is not your UEFI similar if not almost identical to all the other Acer model?
Differences usually are small by brand, and each model just only has extra UEFI features for extra options.

---

### Post by Jazlaan on 2015-06-27
I guess I have to start over. How do I reset all the settings back to normal?
My laptop starts with "security boot fail" everytime now..

---

### Post by oldfred on 2015-06-27
That means in UEFI you turned on, or never turned off secure boot.
Best to do that first.
And set password, to open up the other settings you need to change.

Did you make good backups of Windows & a Windows repair flash drive?
If you reinstall, be sure to read caution in link in my signature. Anything other than Something Else install option may erase entire drive.

---

