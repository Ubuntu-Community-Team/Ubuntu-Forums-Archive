---
title: "Installed Ubuntu from CD; now the CD drive i gone"
date: 2008-04-26
forum: General Help
---

### Post by thure on 2008-04-26
Hi All, i hope you can help me.

On my laptop I have just burned the 8.04 ISO file to a CD. I rebooted and booted with the Ubuntu CD. I installed Ubuntu from the CD. Now i have a dual boot with Windows XP and Ubuntu 8.04.

I just found out that i cannot find my CD/DVD drive in Ubuntu. I rebooted the laptop, and tried to boot up on a CD -- and it works fine! I returned to Ubuntu, but still no CD drive detected.

Then i booted up in Windows XP, and also here the CD/DVD drive was not found! This is scary.

How can the installation of Ubuntu affect the detection of the CD drive in both Ubuntu _AND_ Windows? How can i solve the problem?

/Regards, thure

---

### Post by knutschr on 2008-04-26
> **thure said:**
> 
I just found out that i cannot find my CD/DVD drive in Ubuntu. I rebooted the laptop, and tried to boot up on a CD -- and it works fine! I returned to Ubuntu, but still no CD drive detected.

Then i booted up in Windows XP, and also here the CD/DVD drive was not found! This is scary.

How can the installation of Ubuntu affect the detection of the CD drive in both Ubuntu _AND_ Windows? How can i solve the problem?

/Regards, thure
It is not possible that Ubuntu installation can affect XP.
Insert a CD, and I think it will be there :-)

Try also
lshw

---

### Post by thure on 2008-04-26
> **knutschr said:**
> It is not possible that Ubuntu installation can affect XP.
Insert a CD, and I think it will be there :-)

Try also
lshw
Thanks, but it is not that simple, unfortunately.

Btw. i did not say that Ubuntu affected XP, but that it affected the detection of the CD drive in both Ubuntu and Windows.

The CD drive worked before the installation (i burned the ubuntu CD), it worked during installation since i installed from the CD, and now it works when Booting up on a CD (for example; it can boot to the Ubuntu CD).

But from within both Ubuntu and XP, the CD drive cannot be found at all.

I am really lost right now.
/thure

---

### Post by thure on 2008-04-29
I just found out, that the drive is detected, when booting up on the Ubuntu LIVE CD "Test Ubuntu without install".

It must be "disabled" or something during the bootup (Sometimes around when the GRUB boot manager is shown).

I can see that i am not the only 1 with the problem. People cannot detect their harddisk or cd drive now.

I am begging you. Please help.

---

