---
title: "GRUB menu doesn´t appear, boots straight to Windows 7"
date: 2012-11-25
forum: General Help
---

### Post by Veren on 2012-11-25
Hello there,
a friend of mine has got a new desktop PC with Windows 7 preinstalled. It is an HP, that means it had had 4 primaries by default. We deleted the system recovery partition so that we could have made there an extended partition instead. We installed Ubuntu 12.04 to dual-boot with Windows 7 and installed bootloader to /dev/sda. We made just a basic set-up with a / and /home partitions. When booting, no GRUB menu appears. The PC boots straight to Windows without any other OS being recognized. I can´t get an internet connection there so I can´t even install boot-repair on a USB live system. If you could give me some advice as to what to do it would be greatly appreciated. Thanks

---

### Post by carl4926 on 2012-11-25
Just to be sure
Try booting and hold SHIFT as you do so

---

### Post by NikTh on 2012-11-25
Hi  ,

try to use [boot repair](https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu) , I'm almost certain the problem will be corrected.

Use the second option (link I gave points to that option) , boot from Live-Ubuntu (CD/DVD/USB) , install boot repair and run the [Recommended Repair]. 

Thanks

---

### Post by Veren on 2012-11-25
> **NikTh said:**
> Hi  ,

try to use [boot repair](https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu) , I'm almost certain the problem will be corrected.

Use the second option (link I gave points to that option) , boot from Live-Ubuntu (CD/DVD/USB) , install boot repair and run the [Recommended Repair]. 

Thanks

Thank you NikTh, that was the direction I was heading and I am pretty positive that it will help, but unforttunately I can´t get to the internet on the machine. Can I somehow get it offline ?

Yes, there is, UbuntuSecureRemix

---

### Post by Bashing-om on 2012-11-25
Veren; Hi !

set bios to boot CD device as 1st boot priority;
Internet: When you boot up the installCD and choose "try ubuntu" ..do you not have internet capabilities ?
Eventually should boot to the desk top ..left side of screen (12.04 version) is the launcher, firefox web browser is third icon from the top.
[INDENT]simply try'n to help <== BDQ

[/INDENT]

---

### Post by personalpc on 2012-11-25
Sounds like grub failed to install. Launch into installer and preform a expert install. you should have grub install as an option. Cheers!

---

### Post by greatsirkain on 2012-11-25
Try pressing f12 at boot to get a list of all bootable devices. Was it grub2 you installed? I don't think grub can boot Ubuntu because it uses the ext4 file system

---

### Post by YannBuntu on 2012-11-26
> **veren said:**
> yes, there is, ubuntusecureremix

+1

---

