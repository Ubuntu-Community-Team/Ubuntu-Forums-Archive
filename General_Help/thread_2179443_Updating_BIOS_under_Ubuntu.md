---
title: "Updating BIOS under Ubuntu"
date: 2013-10-08
forum: General Help
---

### Post by goplayer on 2013-10-08
Hello,

I have just installed Ubuntu 12.04 on a Dell Inspiron N5010 laptop. I am having problems with battery charging and understand that an update to the BIOS might be necessary to improve the battery charging and also the heat issue that causes the computer to shutdown if not used on a cooling pad. I looked on Dell's site and found the latest BIOS but unfortunately it is an .EXE file which I can't run in Ubuntu (I tried running ti with wine but get errors). Is there a way to run the file and/or update the BIOS without a windows image disk which I have but wants to install windows. Thanks in advance for any help offered.

---

### Post by philinux on 2013-10-08
> **goplayer said:**
> Hello,

I have just installed Ubuntu 12.04 on a Dell Inspiron N5010 laptop. I am having problems with battery charging and understand that an update to the BIOS might be necessary to improve the battery charging and also the heat issue that causes the computer to shutdown if not used on a cooling pad. I looked on Dell's site and found the latest BIOS but unfortunately it is an .EXE file which I can't run in Ubuntu (I tried running ti with wine but get errors). Is there a way to run the file and/or update the BIOS without a windows image disk which I have but wants to install windows. Thanks in advance for any help offered.

Before you mess with the bios why not try Jupiter out.

[http://www.ubuntugeek.com/jupiter-light-weight-power-and-hardware-control-applet.html](http://www.ubuntugeek.com/jupiter-light-weight-power-and-hardware-control-applet.html)

[http://ubuntuhandbook.org/index.php/2013/07/jupiter-is-available-for-ubuntu-13-04/](http://ubuntuhandbook.org/index.php/2013/07/jupiter-is-available-for-ubuntu-13-04/)

If you search ubuntu jupiter there are more hits.

---

### Post by goplayer on 2013-10-08
Thanks philinux. I'll give it a try but the problem is that with Dell laptops is that if the computer does not recognize the charger as a Dell charger it will not charge the battery. What is happening is that sometimes the charger is recognized and sometimes it is not and as a result the battery is not charging all the time that the charger is plugged in. Also this makes it impossible to use third party chargers which is big racket in my opinion. Anyway, thanks and will give it a try and see.

---

### Post by goplayer on 2013-10-08
Thanks philinux. I'll give it a try but the problem is that with Dell laptops is that if the computer does not recognize the charger as a Dell charger it will not charge the battery. What is happening is that sometimes the charger is recognized and sometimes it is not and as a result the battery is not charging all the time that the charger is plugged in. Also this makes it impossible to use third party chargers which is big racket in my opinion. Anyway, thanks and will give it a try and see. The BIOS update is supposed to take care of this problem from what I understand.

---

### Post by philinux on 2013-10-08
> **goplayer said:**
> Thanks philinux. I'll give it a try but the problem is that with Dell laptops is that if the computer does not recognize the charger as a Dell charger it will not charge the battery. What is happening is that sometimes the charger is recognized and sometimes it is not and as a result the battery is not charging all the time that the charger is plugged in. Also this makes it impossible to use third party chargers which is big racket in my opinion. Anyway, thanks and will give it a try and see. The BIOS update is supposed to take care of this problem from what I understand.

I found this with a simple net search.

[https://wiki.ubuntu.com/DellBIOS](https://wiki.ubuntu.com/DellBIOS)

[https://help.ubuntu.com/community/BiosUpdate](https://help.ubuntu.com/community/BiosUpdate)

[http://askubuntu.com/questions/100945/how-do-i-update-the-bios-of-a-dell-laptop](http://askubuntu.com/questions/100945/how-do-i-update-the-bios-of-a-dell-laptop)

Search "update bios ubuntu" there were other hits. Read them all first before you have a go.

---

### Post by whitesmith on 2013-10-08
I encountered the same problem once. There's a free tool called Bart's PE Disk that boots to the preboot environment of Windows from which different commands can be run. Microsoft's normal restrictions are not applicable. Just put the flash code on a USB, boot from Bart, drop to the command line and rfun your flash. But don't forget to hook up a UPS beforehand...if power problems intervene, it's all over!

---

### Post by YMJzskD on 2013-10-08
You can update the BIOS using dell tools. I have an Inspiron 1720 that I updated the BIOS on running Ubuntu. Here is one source of info and tools: [http://en.community.dell.com/support-forums/software-os/w/linux/bios-updates-and-linux-and-other-operation-systems.aspx](http://en.community.dell.com/support-forums/software-os/w/linux/bios-updates-and-linux-and-other-operation-systems.aspx) and here is the wiki link: [http://linux.dell.com/wiki/index.php/Repository/firmware](http://linux.dell.com/wiki/index.php/Repository/firmware)

---

### Post by goplayer on 2013-10-08
Thanks all for the suggestions and the tips. I tried several of the methods suggested but unfortunately nono worked. However, I was able to update the BIOS simply by creating a DOS (yes DOS) bootable thumb drive using [rufus]("http://rufus.akeo.ie/") and copying the N5010A15.EXE file to the thumb drive, booting in DOS and then running the BIOS updatefile. It worked. Again, thanks for taking the time to answer my question and offer help.

---

