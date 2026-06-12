---
title: "Boot into emergency mode, 16.04 host system"
date: 2018-01-26
forum: General Help
---

### Post by antttren on 2018-01-26
[ATTACH=CONFIG]278331[/ATTACH]

I get this error when I start up my computer, after selecting Ubuntu from the Grub menu. Currently, I only have Ubuntu 16.04 installed on my computer. I erased the Windows 10 installation after numerous issues with dual-boot on my Lenovo Yoga 920. 

Leading up to this error, I was in Ubuntu setting up a Windows 10 VM in virtual box. Then my computer froze completely after I hit &#8216;start&#8217;, so I had to hard restart my computer. Then the grub menu appeared when I turned it back on and I got this error message. 

Any help would be greatly appreciated. Let me know if there&#8217;s any further information I can provide.

I have tried following the help in [https://askubuntu.com/questions/646414/welcome-to-emergency-mode-think-it-is-a-fsck-problem](https://askubuntu.com/questions/646414/welcome-to-emergency-mode-think-it-is-a-fsck-problem), but I am unable to boot from a usb. The device doesn&#8217;t appear as an option when I press F12, nor does it start from usb when I change the boot order in the bios. Although the device does appear in the bios as an option to boot from, which is not the case when I hit F12 pre-boot.

---

### Post by antttren on 2018-01-27
Bump

---

### Post by oldfred on 2018-01-27
Lenovo had a flap with its Yoga 900, not sure if yours is similar.
But did you update UEFI on your system?

 [https://linux.slashdot.org/story/16/09/21/1838252/lenovo-denies-claims-it-plotted-with-microsoft-to-block-linux-installs#comments](https://linux.slashdot.org/story/16/09/21/1838252/lenovo-denies-claims-it-plotted-with-microsoft-to-block-linux-installs#comments)
Lenovo Linux support - many obsolete versions of Linux
[https://support.lenovo.com/us/en/documents/pd031426](https://support.lenovo.com/us/en/documents/pd031426)
 Warning: Microsoft Signature PC program now requires that you can't run Linux. Lenovo Yoga 900 ISK2 UltraBook Sept 2016
[https://ubuntuforums.org/showthread.php?t=2337719](https://ubuntuforums.org/showthread.php?t=2337719)
[http://mjg59.dreamwidth.org/44694.html](http://mjg59.dreamwidth.org/44694.html)
[https://hardware.slashdot.org/story/16/09/21/1516230/microsoft-signature-pc-requirements-now-blocks-linux-installation-reports#comments](https://hardware.slashdot.org/story/16/09/21/1516230/microsoft-signature-pc-requirements-now-blocks-linux-installation-reports#comments)
The 13" Lenovo 710S-13ISK is also affected by this. Not providing an AHCI mode makes sure:
- you can't run Linux on it
- you can't use the Gentoo based System Rescue CD to rescue data
- you can't use the Acronis True Image Boot CD (which is also Linux based of course)
- you can't use Crystal Disk Info in Windows to judge your SSD health (doesn't show the disk)
- you can't even install Windows 10 from the normal installation media without putting special drivers on an additional USB stick.

---

