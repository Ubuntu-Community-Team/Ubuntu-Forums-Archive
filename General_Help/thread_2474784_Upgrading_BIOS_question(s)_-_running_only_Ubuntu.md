---
title: "Upgrading BIOS question(s) - running only Ubuntu"
date: 2022-05-07
forum: General Help
---

### Post by jmichaels29 on 2022-05-07
Running only Ubuntu 22.04 lts on both of my HP systems. 

The webpage at HP support, of course, are concerned only with Windows.

The 2 computers are, with their HP BIOS pages on the net:

HP Elitedesk 800 G1:  [https://support.hp.com/us-en/drivers/selfservice/swdetails/hp-elitedesk-800-g1-small-form-factor-pc/5387475/swItemId/vc-186570-2](https://support.hp.com/us-en/drivers/selfservice/swdetails/hp-elitedesk-800-g1-small-form-factor-pc/5387475/swItemId/vc-186570-2)

&

HP Pavilion Notebook 17-5161us:  [https://support.hp.com/us-en/drivers/selfservice/hp-pavilion-17-g100-notebook-pc-series/8499304/model/8788292](https://support.hp.com/us-en/drivers/selfservice/hp-pavilion-17-g100-notebook-pc-series/8499304/model/8788292)


I've fetched the 2 .exe files that are the updates.  Naturally, I'd like assistance with how to upgrade the bios on my 2 systems running only Ubuntu lts

Addendum:  I found this webpage.  I will proceed with the instructions here.  Just wanted to check with users here that these instructions should work with 22.04 lts, as I don't want to brick a system since bios is pretty serious stuff

---

### Post by jmichaels29 on 2022-05-07
Concerning the desktop.  I went into the bios configuration setup.  I  did not see anywhere where I could fetch the bios file from a plugged in  usb thumb drive.  However, there were options where it seems like I can  fetch and upgrade the bios via a "network."  Perhaps network means  internet, perhaps not (?)
 
Here are 3 photos from the desktops bios config. screens:

[[https://live.staticflickr.com/65535/52057733356_fee3cd8b12_5k.jpg](https://live.staticflickr.com/65535/52057733356_fee3cd8b12_5k.jpg)]("https://flic.kr/p/2njausQ")[IMGP0813]("https://flic.kr/p/2njausQ")  by [Michael Piziak]("https://www.flickr.com/photos/piziak/"), on  Flickr

[[https://live.staticflickr.com/65535/52056692292_b78fca3fe3_5k.jpg](https://live.staticflickr.com/65535/52056692292_b78fca3fe3_5k.jpg)]("https://flic.kr/p/2nj59Zs")[IMGP0812]("https://flic.kr/p/2nj59Zs")  by [Michael Piziak]("https://www.flickr.com/photos/piziak/"), on  Flickr

[https://www.flickr.com/photos/piziak/52057733866/in/dateposted-public/](https://www.flickr.com/photos/piziak/52057733866/in/dateposted-public/)

The last of the 3 photos above, you may need to click url to see it.  
I did an exit without saving any changes for the time being.

Concerning  the laptop.  I went into the bios configuration setup.  I did not see  anywhere where I  could fetch the bios file from a plugged in usb thumb drive.   Furthermore, there were no options to upgrade it via a network.   (?)

---

### Post by oldfred on 2022-05-07
Please Attach screenshots or photos.
Not everyone has high speed Internet.
You can easily attach using Forum's Advanced Editor and paperclip icon.


HP UEFI update - extract .bin from .exe file and copy into FAT32 partition.
[https://askubuntu.com/questions/539120/how-to-perform-a-hp-bios-upgrade-with-only-ubuntu/1234098#1234098](https://askubuntu.com/questions/539120/how-to-perform-a-hp-bios-upgrade-with-only-ubuntu/1234098#1234098) & 
[https://h30434.www3.hp.com/t5/Notebooks-Archive-Read-Only/How-to-update-BIOS-on-Linux/m-p/5441775#M1205498](https://h30434.www3.hp.com/t5/Notebooks-Archive-Read-Only/How-to-update-BIOS-on-Linux/m-p/5441775#M1205498)

---

### Post by jmichaels29 on 2022-05-08
Thanks for the links and the other recommendations.

I've tried a lot of things and can't seem to pull off a bios upgrade for the desktop...

hmmm

Formatted the thumb drive properly and put the .bin file on it, put the file in a folder at location "Hewlett-Packward/BIOS/New/"  <- then, put the entire folder in there and also tried just putting the .bin file in there, even tried to update the bios from "network" which it appeared to download "stuff" off the internet and install, etc...    

I'll keep at it.  I'm only getting a quick error message upon startup.  All seems to work good, so I may just learn to live with it...

---

### Post by poorguy on 2022-05-08
If your computers are working without problems running the current bios I'd leave them be.

I've watched many users turn a perfectly good working computer into a door stop by upgrading the bios.

I'm using computers from 2007 with the original oem bios.

```


lubuntu@hp-compaq:~$ inxi -b
System:
  Host: hp-compaq Kernel: 5.15.0-27-generic x86_64 bits: 64
    Desktop: LXQt 0.17.1 Distro: Ubuntu 22.04 LTS (Jammy Jellyfish)
Machine:
  Type: Desktop System: Hewlett-Packard
    product: HP Compaq dc7800p Small Form Factor v: N/A
    serial: <superuser required>
  Mobo: Hewlett-Packard model: 0AA8h serial: <superuser required>
    BIOS: Hewlett-Packard v: 786F1 v01.04 date: 07/18/2007


```

---

### Post by GhX6GZMB on 2022-05-08
Why do you want to upgrade BIOS on the two machines? Don't they work?

---

### Post by oldfred on 2022-05-08
While an old BIOS system may be ok without an update, UEFI is a bit more complex.

Spectre virus, repoline firmware update
Almost all systems need UEFI updates, anyway, for mitigation of Meltdown and Spectre CPU vulnerabilities from cpu speculative execution and caching. 
Many also need SSD firmware updates.

UEFI update required for USB-C port issues 2017 thru 2019 models
ThinkPad models including the ThinkPad X1 Carbon (5th Gen to 7th Gen), X1 Yoga (2nd Gen to 4th Gen), and P-series 
[https://www.cnet.com/news/is-your-thinkpads-usb-c-port-not-working-upgrade-its-firmware/](https://www.cnet.com/news/is-your-thinkpads-usb-c-port-not-working-upgrade-its-firmware/)

And I have seen a lot of threads where UEFI updates have solved various issues.
Not sure if I have seen anyone have an issue with updates causing more problems.

Many devices can now be updated directly from Linux.
Devices using LVFS for firmware updates
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist)

And Windows does updates as part of its update process.

---

### Post by poorguy on 2022-05-08
> **oldfred said:**
> 
And I have seen a lot of threads where UEFI updates have solved various issues.
Not sure if I have seen anyone have an issue with updates causing more problems.


I've witnessed some and some users seem to want to upgrade bios as soon as a new bios release comes out. 

None of my Linux computers are UEFI so don't know anything about what they need or require and the last time I upgraded bios I used a bootable cd I created back in 2009 so it's been a bit.

---

### Post by ActionParsnip on 2022-05-08
I've heard FreeDOS is a way around this stuff

---

### Post by jmichaels29 on 2022-05-08
I've read the 3 replies since my last reply to this thread, and here's an update (if you can call it that).

To answer some questions.  Both computers work fine.  
I just got some error messages, quickly flash across the screen, on both computers.  Occurred only after upgrading both to 22.04 lts

One example, on the desktop "ima: error communicating to tpm chip"  Then when "hiding" tpm in bios, a different message would quickly occur - "Can't evaluate _CRS 12311"

On the laptop, I would get this message when tpm was on: [[IMG]https://live.staticflickr.com/65535/52060022211_40c9205fd7_5k.jpg[/IMG]]("https://flic.kr/p/2njndRR")[withTPM]("https://flic.kr/p/2njndRR") by [Michael Piziak]("https://www.flickr.com/photos/piziak/"), on Flickr

And with TPM turned off/hidden, I would get:  [[IMG]https://live.staticflickr.com/65535/52060022226_6b806404e5_5k.jpg[/IMG]]("https://flic.kr/p/2njndS7")[noTPM]("https://flic.kr/p/2njndS7") by [Michael Piziak]("https://www.flickr.com/photos/piziak/"), on Flickr

After my failed attempts to update bios in the desktop yesterday, I decided to try to update it on the laptop today.  No success again, after trying many different things (as with the desktop). 
 
I've decided to just live with the messages, since nothing seems to be affected.  I've spent hours trying to pull this off.    I am curious if other computer manufacturers are as difficult to update the bios.  I have always been loyal to and somewhat of a fan of HP computers & other devices, but this experience has somewhat changed my thinking on this/that.
 
Regards,

Michael

Addendum:  I reduced the file size of my photos in Gimp.  I understand that everyone may not have high speed internet.

---

### Post by poorguy on 2022-05-08
I also get TPM errors at start up on some of my computers.
 No worries as I don't have any TPM on my old computers.

I also get DMAR errors on some of my computers.

These errors occur on several of my computers using different Linux distros so just not related to Ubuntu 22.04 or Ubuntu 22.04 official flavors.

I don't believe I'd be to concerned about those errors and if the computers are working I'd leave them be.

As for any security vulnerabilities that bios updates may help when you use computers as old as mine there aren't any security updates as the manufacturers don't create them so I rely on the Linux developers and the browsers developers to keep my computers safe.

My two bits.

---

