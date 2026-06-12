---
title: "Sane Scanner Support needs EHCI, which Skylake Removes?"
date: 2016-01-18
forum: General Help
---

### Post by NertSkull on 2016-01-18
I just upgraded my hardware to the new Skylake i7 6700k, and a Maximus VIII HERO MB. My understanding is Skylake/Z170 has removed EHCI support, and only supports XHCI. (To be honest, I'm not 100% sure I understand what is/is not supported, but a google search of skylake ehci will bring up lots of reports saying it isn't supported).

Problem is, it appears the SANE scanner stuff does not play well with XHCI. My scanner is no longer consistently recognized, and has lots of I/O errors on the rare occasions it does get recognized.

I've searched around a lot, and EVERYTHING that matches my problem says to disable XHCI and rely on the old EHCI/USB 2 stuff.  Problem is, with the new skylake system, I don't have that option.

[This]("http://sane.10972.n7.nabble.com/Fujitsu-S1500-unable-to-stay-connected-td18987.html") post, explains my situation perfectly, but again the solution is turning off XHCI, which I can't do.  I have checked my motherboard BIOS, and there is NO option to turn off XHCI.

There was one post I found that suggested upgrading to the mainline kernel may help, but I'm not thrilled with trying that, but I'm willing of someone else really thinks that would help.  Currently I'm on Kubuntu 14.04/3.19.0-43-generic.

So I think this is really a SANE issue.  My scanner is the Fujitsu ScanSnap S1500, which else-wise appears to have good support.  But all of my USB ports (2 & 3) are controlled by xhci, and I can't get it to recognize now on this new system.

Anyone have any ideas of what to try?

---

### Post by cbraxton on 2016-01-18
How about installing a USB 2.0 card for the scanner? Will EHCI then be enabled for those ports?

[http://www.amazon.com/StarTech-com-Express-Profile-Speed-PEXUSB4DP/dp/B002RL8V7E/ref=dp_ob_title_ce](http://www.amazon.com/StarTech-com-Express-Profile-Speed-PEXUSB4DP/dp/B002RL8V7E/ref=dp_ob_title_ce)

---

### Post by NertSkull on 2016-01-19
> **cbraxton said:**
> How about installing a USB 2.0 card for the scanner? Will EHCI then be enabled for those ports?

[http://www.amazon.com/StarTech-com-Express-Profile-Speed-PEXUSB4DP/dp/B002RL8V7E/ref=dp_ob_title_ce](http://www.amazon.com/StarTech-com-Express-Profile-Speed-PEXUSB4DP/dp/B002RL8V7E/ref=dp_ob_title_ce)


That's not a bad idea, I'll have to look into it.  

My initial gut reaction is that no, it wouldn't work, since what I've read says its the processor that no longer works with EHCI. But I clearly am not an expert on processors, so I don't know that for sure. I'll look into it though.  My assumption though, is that since the same processor would be running a USB 2.0 card, it would still use XHCI to handle it? I actually think it may be the chipset (Z170) the prevents it.  BUT, again, this are all wild assumptions on my part. If anyone know I'm wrong for sure, let me know. I'll report back if I learn anything.

For the time being, assuming that a USB 2.0 card wouldn't work, does anyone have any other thoughts?

---

### Post by NertSkull on 2016-01-25
Anyone? 

My current thought is to try to update to the mainline kernel. I've never done that, but I read somewhere that the 4.1+ kernel fixes scanners with USB 3.0 issues. But I've never used the mainline kernel, so I'm hoping there is someone that knows an easier fix to get scanners working.

---

### Post by fermin on 2016-01-26
Did you have any luck? I have no idea about that Skylake you're mentioning but I'm trying to setup a Fujitsu ScanSnap  S1500M on Ubutu 14.04 LTS to no avail.It seems to have been solved in OpenSuse as mentioned in the above cited thread

[http://sane.10972.n7.nabble.com/Fujitsu-S1500-unable-to-stay-connected-td18987.html](http://sane.10972.n7.nabble.com/Fujitsu-S1500-unable-to-stay-connected-td18987.html)

but not in Ubuntu repositories. I have exactly the same problem as in that thread but in Ubuntu 14.04. It's supposed to be completely  supported by the SANE project drivers:

[http://www.sane-project.org/sane-backends-1.0.23.html#S-FUJITSU](http://www.sane-project.org/sane-backends-1.0.23.html#S-FUJITSU)

with the version currently distributed with the Ubuntu repositories [v1.0.23]("http://www.sane-project.org/sane-backends-1.0.23.html#S-FUJITSU"),  but it just doesn't work at all through Xsane, Easyscan, gscan2pdf or  sane terminal commands like "scanimage -L", they all report not being  able to find the scanner or an I/O error when it intermittently is  recognized. I know it is recognized by the USB system because dmesg  reports

```
[12343.432592] usb 3-1: new high-speed USB device number 15 using xhci_hcd
[12343.470668] usb 3-1: New USB device found, idVendor=04c5, idProduct=11a2
[12343.470690] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[12343.470692] usb 3-1: Product: ScanSnap S1500
[12343.470694] usb 3-1: Manufacturer: Fujitsu 
```

lsusb in the terminal also reports the scanner is recognized:

```
franco@ensenada:/etc/sane.d$ lsusb
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 8087:07da Intel Corp. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 012: ID 04f2:1026 Chicony Electronics Co., Ltd 
Bus 003 Device 017: ID 04c5:11a2 Fujitsu, Ltd 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

So it seems to be recognized by linux but somehow not working with the  sane drivers as it is supposed to. Trying to solve the problem I tried  sane-find-scanner and it says there is no USB device!

```
franco@ensenada:/etc/sane.d$ sudo sane-find-scanner 
[sudo] password for franco: 

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

could not fetch string descriptor: Pipe error
could not fetch string descriptor: Pipe error
  # No USB scanners found. If you expected something different, make sure that
  # you have loaded a kernel driver for your USB host controller and have setup
  # the USB system correctly. See man sane-usb for details.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.
```

The sane-fujitsu backend is active in the fujitsu.conf file in  /etc/sane.d/ and the brand and model of this scanner even appears on  this list as

```

#S1500 & S1500M
usb 0x04c5 0x11a2
```

In the Easyscan interface it shows up in the scanner selection dropdown  list but it says it can't connect when I try to scan. So everything  seems to be configured right and it seems like the sane drivers are not  doing their job somehow. I know the scanner works because I can scan  with it using the proprietary VueScan in the same machine, even in the  Ubuntu! Any ideas?

UPDATE: I tried updating the Linux Kernel to 4.2.0.27.21 used in the newer Wily (previously I had 3.13.0.77.83 used in Trusty LTS) thinking this apparent USB problem could've been solved in the kernel as I read this is how it was solved "patching the kernel" in OpenSuse, but it didn't work. I'm guessing it either hasn't been solved in the Ubuntu repositories kernels or it is some other SANE related problem. I will try a proposed solution I found in 
[http://www.gaggl.com/2013/08/paperless-office-on-a-budget/](http://www.gaggl.com/2013/08/paperless-office-on-a-budget/)
and report.

---

### Post by fermin on 2016-01-26
I solved the problem following the instructions in

[https://www.gaggl.com/2013/08/paperless-office-on-a-budget/comment-page-1/#comment-51572](https://www.gaggl.com/2013/08/paperless-office-on-a-budget/comment-page-1/#comment-51572)

It worked like a charm on Ubuntu 14.04 LTS, thanks a lot! I had been looking for a solution for some time! Two things though:
1) The same "scanbuttond" package file (scanbuttond_0.2.3.cvs20090713-14_i386.deb) is available now in the repositories, probably after installing the cited ppa:rolfbensch/sane-git, so there's no need to download it from the pkgs.com website, just type "sudo apt-get install scanbuttond".
2) The actual button on the scanner does nothing when pressed so I'm not sure what the purpose of the "scanbuttond" software actually is, so probably it is not needed anyway if you don't mind missing this functionality. If the purpose of the software is just to have this physical button work then it doesn't though, at least in my case. I scanned through Easyscan, Xsane and gscan2pdf and all worked perfectly.

Ah by the way I got it running in a Panasonic Let&#8217;s note laptop and there where no usb port power saving issues here. I hope it helps. Good luck!

EDIT:  I would recommend doing the "Scanner config" and "Permissions" sections in the reference article and checking if it works, if it doesn't then go to "Install dependencies" through the PPA and check again. At last I would install the scanbuttond and configure it.

---

### Post by NertSkull on 2016-01-26
Success! 

So the Scanner config and Permissions sections of that article are already taken care of as part of default sane install.  So nothing to do there.

BUT, the sane-git ppa worked.  It must have updated code that works for me.

All I did was 

sudo add-apt-repository ppa:rolfbensch/sane-git
sudo apt-get update
sudo apt-get upgrade

And now my scanner works.

Thank you so much!!!

---

