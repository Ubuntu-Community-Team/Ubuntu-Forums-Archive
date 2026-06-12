---
title: "Grub doesn't work"
date: 2016-10-04
forum: General Help
---

### Post by krishkat on 2016-10-04
Today I upgraded my Asus H-170 BIOS to the newest version. I turned Secure-Boot off and wanted to start ubuntu 16.04 LTS. But when I start grub, I will be in grub-rescue.
I can start Win7 64bit.
How can I start Ubuntu again?:confused:

---

### Post by oldfred on 2016-10-04
May be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by krishkat on 2016-10-04
@oldfred
It seems like that my new gtx 1060 doesn't like it when I boot from USB (Monitor says frequence to high!). So I will dismount the card now and will run it with my built-in graphics

---

### Post by krishkat on 2016-10-04
Here is my system before running Boot Repair [http://paste.ubuntu.com/23275422/](http://paste.ubuntu.com/23275422/)
And after [https://paste.ubuntu.com/23275465/](https://paste.ubuntu.com/23275465/)

---

### Post by krishkat on 2016-10-04
After I replaced my gtx 1060 with my r7 250, I ran boot-repair and everything works now

---

### Post by oldfred on 2016-10-04
Glad you got it working.

Some have just used internal video to install, then installed newest nVidia driver from ppa to get nVidia to work. My old nVidia card just works with open source driver.

       NVIDIA GeForce GTX 1060 Offers Great Performance On Linux
[URL="http://www.phoronix.com/scan.php?page=article&item=nv-linux-gtx1060&num=1"]http://www.phoronix.com/scan.php?page=article&item=nv-linux-gtx1060&num=1
[/URL]
 Ubuntu 16.04 LTS installation problem with GA-Z170X-UD5 TH & GTX 1080
[http://ubuntuforums.org/showthread.php?t=2327648](http://ubuntuforums.org/showthread.php?t=2327648) 
      
 Instructions are newest driver for newest cards, must load legacy driver if old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)
Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
sudo apt-add-repository ppa:graphics-drivers/ppa 
    [URL="http://www.phoronix.com/scan.php?page=article&item=nv-linux-gtx1060&num=1"]
      [/URL]
 [https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#fglrx](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#fglrx)
16.04 Release notes
When upgrading to Ubuntu 16.04 from a previous release, both the fglrx driver and the xorg.conf will be removed, so that the system is set to use either the amdgpu driver or the radeon driver (depending on the available hardware).  
   AMD driver discussion with 16.04
[http://ubuntuforums.org/showthread.php?t=2321963](http://ubuntuforums.org/showthread.php?t=2321963)
[http://ubuntuforums.org/showthread.php?t=2327075](http://ubuntuforums.org/showthread.php?t=2327075) 
    [URL="http://www.phoronix.com/scan.php?page=article&item=nv-linux-gtx1060&num=1"]
[/URL]

---

### Post by krishkat on 2016-10-04
So there are NO problems with my installed Operating Systems. When I make an Ubuntu USB-Stick from an .iso file, and then choose an option of the built-in grub, my NEC MultiSync EA193Mi shows the error: Frequency to high!
@oldfred thanks for your help

---

