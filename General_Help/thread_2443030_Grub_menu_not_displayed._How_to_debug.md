---
title: "Grub menu not displayed. How to debug ?"
date: 2020-05-10
forum: General Help
---

### Post by georgesgiralt on 2020-05-10
Hello,
I own an old Lenovo E540 (i7 4702MQ CPU with 16GB ram and an Nvidia GT740 Mobile card) It has the latest available BIOS from Lenovo (Version 2.28) mandatory because of the Spectre vulnerablity.
I've installed on it an Ubuntu version (18.04 LTS) using LVM and secure boot (Windows 10 is also on this machine).
The Grub menu does not show unless I remove the fonts unicde.pf2 font from /boot/grub and /boot/grub/fonts directories. Doing this I can see the menu but it looks terrible. 
I tried to upgrade to 19.10 In order to see if the new grub fixes the problem but it does not.
This afternoon I upgraded to 20.04 LTS to check again. Nope. 

I wonder if there is a way to get very verbose GRUB messages written to disk when it starts in order to check what is wrong and make displaying the menu impossible ?
Many thanks in advance for your help and advice !
Have a nice day ! 

P.S. : This laptop ran a 18.04 version of Ubuntu without the problem for a long time but the secure boot was not on, BIOS was an earlier version and it was on Legacy BIOS mode. I switched for the new BIOS when I decided to put it back to use and replaced the Windows 7 OS with Windows 10. Secure Boot forced me to switch to UEFI which showed the bug.

---

### Post by CelticWarrior on 2020-05-10
You can (and should) have both systems installed in UEFI mode.
You don't have to enable Secure Boot. Some other UEFI settings may need changes.

---

### Post by georgesgiralt on 2020-05-10
Hello Changan,
Thank you for your prompt answer,
I did not make myself clear. I need to have UEFI AND secure boot enabled on this machine. It  is, for me, mandatory.

---

### Post by CelticWarrior on 2020-05-10
> **georgesgiralt said:**
> I did not make myself clear. I need to have UEFI AND secure boot enabled on this machine. It  is, for me, mandatory.

May I ask why?
It certainly isn't because of the dual-boot with Windows (it works with or without Secure Boot).
It is for work? If so it's a ridiculous requirement (someone in IT doesn't know what SB really is).

---

### Post by georgesgiralt on 2020-05-10
No, I test and use a lot of software some of it from dubious source.  and, believe it or not, Secure boot is a very good thing. It force software maker to think a little ... Not a bad thing.

---

### Post by CelticWarrior on 2020-05-10
> **georgesgiralt said:**
> No, I test and use a lot of software some of it from dubious source.  and, believe it or not, Secure boot is a very good thing. It force software maker to think a little ... Not a bad thing.

So it's you who don't know what Secure Boot is (or what it does) and there's nothing mandatory here, at all, just your insistence due a deep misunderstanding.

Please note I never said it was a bad thing. As a matter of fact the Linux Foundation agrees with and promotes Secure Boot. What I said was, explicitly, you don't need it enabled for a UEFI installation.

Good luck.

---

### Post by georgesgiralt on 2020-05-10
But the main problem remains. Even with secure boot off, the Grub menu does not show. So the problem is not at all secure boot relevant. 
I _do_ know that I can have UEFI enabled and secure boot disabled. But if you turn secure boot on, it mandate UEFI. 
And I need UEFI and secure boot for my tests. 
And my understanding, or not, of secure boot itself or it's mechanism has nothing to do with the Grub not showing it's menu and the way to debug it. . 
Have a nice and bright day.

---

### Post by yancek on 2020-05-10
> No, I test and use a lot of software some of it from dubious source.  and, believe it or not, Secure boot is a very good thing 

Secure Boot isn't going to protect a user from downloading malware as it is only in the boot process that it has any use.  Explanation in the link below.  Second link has additional info at the microsoft site.  Are you unable to boot Ubuntu now or is it just the fonts that are not readable that is the problem?  Did you install both windows/ubuntu UEFI?    

[https://www.tenforums.com/tutorials/85279-enable-disable-secure-boot-windows-10-pc.html](https://www.tenforums.com/tutorials/85279-enable-disable-secure-boot-windows-10-pc.html)

[URL="https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/disabling-secure-boot"]https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/disabling-secure-boot
[/URL]

---

### Post by georgesgiralt on 2020-05-10
OK, you did not get me.
I MUST HAVE THE SECURE BOOT ENABLED. It has nothing to do with the grub menu not displayed. It does not display even if secure boot is turned off.
I WOULD LIKE TO KNOW HOW I CAN GET AS MUCH GRUB DEBUG AS POSSIBLE AND HAVE IT SAVED TO DISK. For now, I can't make it to save the messages to the disk.
I use secure boot to test how some software behave when prevented loading, even far away from boot time. And this is why I use it.
So I close this thing. Continue to talk about the pro and cons of secure boot and how it is supposed to behave. I'm out and won't come back.
Have a long and bright day.

---

### Post by wildmanne39 on 2020-05-10
> So I close this thing. Continue to talk about the pro and cons of secure boot and how it is supposed to behave. I'm out and won't come back.
Have a long and bright day. On that note thread closed!

---

