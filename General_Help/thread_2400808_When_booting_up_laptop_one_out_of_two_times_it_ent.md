---
title: "When booting up laptop one out of two times it enters the grub prompt"
date: 2018-09-10
forum: General Help
---

### Post by jorritTyb on 2018-09-10
So the subject almost says it all. This is on a dual boot laptop (MSI Gaming laptop) with Windows 10 on the first SSD and Kubuntu 18.04 on the second SSD. Grub is installed on the second SSD. Everything works fine. I can boot up in windows and I can boot up in linux. However, about 50% of the time after turning on my laptop I don't get the boot menu but instead I just enter in the grub commandline. From there I can do exit and then proceed as normal but this is slightly annoying. Any solution for this? Thanks

---

### Post by oldfred on 2018-09-10
Are you hibernating either system?
Is Windows fast start up on, which is hibernation?

       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Just run the summary report, the auto fix sometimes can create more issues.
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot, only use ppa download into Ubuntu live installer.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by jorritTyb on 2018-09-11
> **oldfred said:**
> Are you hibernating either system?
Is Windows fast start up on, which is hibernation?

       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Just run the summary report, the auto fix sometimes can create more issues.
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot, only use ppa download into Ubuntu live installer.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

No I disabled fast startup. So no hibernation as far as I know. I don't understand your other suggestions. Also note that the problem is not 100% reproducable. It doesn't happen all the time.

Thanks

---

### Post by oldfred on 2018-09-11
Looking for the detailed configuration report from Boot-Repair. Just post the link it provides.
If if boots, report may not show anything, but perhaps something is out of place and UEFI is defaulting sometimes to an incorrect boot mode.

Some other MSI threads. Many seemed to need boot parameters. Not sure what else they suggest.
Have you updated UEFI form MSI? 

       MSI GS65  Boot parameter: modprobe.blacklist=nouveau 
[https://askubuntu.com/questions/1061109/dual-boot-windows-10-cannot-boot-latest-ubuntu-but-only-older-versions](https://askubuntu.com/questions/1061109/dual-boot-windows-10-cannot-boot-latest-ubuntu-but-only-older-versions)
MSI GE63 Update UEFI then acpi=off not required
[https://askubuntu.com/questions/1059029/18-04lts-msi-ge63-boot-issues](https://askubuntu.com/questions/1059029/18-04lts-msi-ge63-boot-issues)
[https://askubuntu.com/questions/1038637/how-to-install-ubuntu-on-msi-ge63-without-acpi-off](https://askubuntu.com/questions/1038637/how-to-install-ubuntu-on-msi-ge63-without-acpi-off)
MSi GT72VR-6RE Dominator Pro - some settings required
[https://ubuntuforums.org/showthread.php?t=2365997](https://ubuntuforums.org/showthread.php?t=2365997)
Failing to Boot Ubuntu 16.10 in MSI GP72
[http://askubuntu.com/questions/838212/failing-to-boot-ubuntu-16-10-in-msi-gp72](http://askubuntu.com/questions/838212/failing-to-boot-ubuntu-16-10-in-msi-gp72)
[SOLVED] MSI GT72S 6QE - Freezes on boot unless acpi=off is used
[http://ubuntuforums.org/showthread.php?t=2303544](http://ubuntuforums.org/showthread.php?t=2303544)

---

### Post by jorritTyb on 2018-09-11
> **oldfred said:**
> Looking for the detailed configuration report from Boot-Repair. Just post the link it provides.
If if boots, report may not show anything, but perhaps something is out of place and UEFI is defaulting sometimes to an incorrect boot mode.

Some other MSI threads. Many seemed to need boot parameters. Not sure what else they suggest.
Have you updated UEFI form MSI? 

       MSI GS65  Boot parameter: modprobe.blacklist=nouveau 
[https://askubuntu.com/questions/1061109/dual-boot-windows-10-cannot-boot-latest-ubuntu-but-only-older-versions](https://askubuntu.com/questions/1061109/dual-boot-windows-10-cannot-boot-latest-ubuntu-but-only-older-versions)
MSI GE63 Update UEFI then acpi=off not required
[https://askubuntu.com/questions/1059029/18-04lts-msi-ge63-boot-issues](https://askubuntu.com/questions/1059029/18-04lts-msi-ge63-boot-issues)
[https://askubuntu.com/questions/1038637/how-to-install-ubuntu-on-msi-ge63-without-acpi-off](https://askubuntu.com/questions/1038637/how-to-install-ubuntu-on-msi-ge63-without-acpi-off)
MSi GT72VR-6RE Dominator Pro - some settings required
[https://ubuntuforums.org/showthread.php?t=2365997](https://ubuntuforums.org/showthread.php?t=2365997)
Failing to Boot Ubuntu 16.10 in MSI GP72
[http://askubuntu.com/questions/838212/failing-to-boot-ubuntu-16-10-in-msi-gp72](http://askubuntu.com/questions/838212/failing-to-boot-ubuntu-16-10-in-msi-gp72)
[SOLVED] MSI GT72S 6QE - Freezes on boot unless acpi=off is used
[http://ubuntuforums.org/showthread.php?t=2303544](http://ubuntuforums.org/showthread.php?t=2303544)

I don't know what Boot-Repair is and how to get configuration report from it. Sorry, but I'm a bit of a noob when it comes to things like this.

By updating UEFI, you mean the bios? In that case I didn't update as I already had the latest version as available on the site.

Thanks

---

### Post by oldfred on 2018-09-11
If you click on the link I posted above about Boot-Repair, it shows how to install it using a ppa.
Best to go to site, so you can familiarize yourself on what is can do.
It really is only two lines (one at a time) in terminal to install & run. Then copy & paste the full link to an online report here.

---

