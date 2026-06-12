---
title: "ubuntu / windows 8.1 uefi dual boot"
date: 2014-09-29
forum: General Help
---

### Post by startas on 2014-09-29
Whats the status of uefi for ubuntu ? is it possible to have uefi dual boot ubuntu/windows 8.1 without problems ?

---

### Post by rbmorse on 2014-09-29
It's absolutely possible. 

The key, as in all dual-boot installations involving Windows, is to install Windows on the host machine first and make sure it is properly configured and stable before installing any other O/S.  From there, getting one of the 64-bit Ubuntus going is mostly a matter of making sure you're using the EFI mode installer and not letting the partition manager overwrite the existing Windows installation.

---

### Post by startas on 2014-09-30
I read some stories, that linux dualboot with windows win8.1 in uefi can mess up windows, is that true ?

---

### Post by oldfred on 2014-10-01
There is a bug where using an auto install when re-installing will erase entire hard drive even if it says it is replacing previous Ubuntu install. 
But if you have full backups even that is not an issue. 
But as long as you use the Something Else or manual install option, there are no issues as you totally control which partitions you use.
Some vendors modify UEFI to only boot Windows but there are several work arounds that just require copying a file or two.
Often some UEFI/BIOS settings are required.

See links in my signature for lots more info:

       UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)
But I suggest using Windows to shink Windows and reboot Windows first. But do not create any partitions with Windows disk tools.
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

What brand/model computer. Many have posted on how it worked or what issues they had with various models from just about every brand.

---

### Post by grahammechanical on 2014-10-01
Take note of the advice in this wiki page

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Read through some of the posts on this forum and you will see that many do have problems. But then again we do get those who have problems. Those who do not have problems do not post on forums asking for help. But keep in mind that the retailers and Microsoft are not going out of their way to make it easy for us to dual boot their products.

Regards

---

