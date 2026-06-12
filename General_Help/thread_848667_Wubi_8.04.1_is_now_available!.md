---
title: "Wubi 8.04.1 is now available!"
date: 2008-07-03
forum: General Help
---

### Post by ago on 2008-07-03
We are pleased to announce the release of Wubi 8.04.1

It can be downloaded from: [http://wubi-installer.org](http://wubi-installer.org)

Please note that Wubi 8.04.1 requires the new 8.04.1 desktop CD/ISO, you will not be able to reuse the 8.04 CD/ISO. Alternate and DVD CD/ISOs will not work with 8.04.1. It is recommended to let Wubi download the ISO for you. If you prefer to download the ISO manually, here is the address: [http://releases.ubuntu.com/8.04.1/](http://releases.ubuntu.com/8.04.1/)

Wubi 8.04.1 addresses most of the issues that emerged after the 8.04 release, in particular it provides fixes for the following:

* LP217348: Ubuntu cannot boot when there are multiple hard disks
* LP224311: Ubuntu gets stuck at reboot with the message: "Turning on gate A20" or "...upper memory..."
* LP204128: Vista jams Wubi when ejecting the CD
* LP222690: install failed during "import document and setting" at 88% - French windows XP
* LP223250: Improved country detection
* LP226622: Wubi has unclear error message on NTFS dirty flag
* LP224697: Disable hibernation if swap is on file
* LP136682: File with non-C/special characters in host computer disappear
* LP236741: Wubi may erase the wrong ubuntu directory when uninstalling
* LP227023: Vista bootloader does not get updated in some circumstances
* LP223155: Wubi failed to install with 255.488MB of RAM (this is now a warning)

If you already have a working Ubuntu installation, there is no need to use Wubi 8.04.1. Simply run the updates from within Ubuntu.

Unsupported Set-Ups:

* Installation over (software) RAID 0 or 1 is NOT supported, this will be supported in the 8.10 release.
* Installation over encrypted disks is not supported.
* Windows ME is not supported at the moment.
* Please note that some hardware may require special boot parameters. This is not a Wubi specific issue, the same applies to standard Ubuntu. You can enable more boot options by pressing ESC at boot after selecting "Ubuntu"
* DVD ISO and Alternate ISO are NOT supported, again this version only supports the 8.04.1 DESKTOP ISO (pay attention to the .1 at the end...)

Known issues:

* The installer may get stacked when using a physical CD while extracting the ISO file stating that the CD is in use. In this case simply run Wubi WITHOUT the CD in the tray. If you already have an ISO, you need to download Wubi.exe from the link above and place it in the same folder as the ISO (do not use the wubi.exe version within the CD as that cannot detect local ISOs). LP230716.
* Installation on a very fragmented drive may fail with an error message while the swap device is being formatted. In this case, uninstall Wubi, run JKDefrag on your drive and reinstall Wubi.
* If you used rev 505, the uninstaller may fail when Wubi is not installed under C:. In this case you can use [https://wiki.ubuntu.com/WubiGuide?action=AttachFile&do=get&target=Uninstall-Ubuntu.exe](https://wiki.ubuntu.com/WubiGuide?action=AttachFile&do=get&target=Uninstall-Ubuntu.exe) to remove ubuntu/wubi

---

### Post by garferi on 2008-07-04
Hi!

I noteiced there is a "rev 501" text in the installer window.
Is this left from the previous version? :)

Thank You!

---

### Post by ago on 2008-07-04
Both Wubi available on the 8.04.1 CD and the one on wubi-installer.org are rev505. Where did you get wubi from?

---

### Post by plastichero on 2008-07-05
Does it work with Xubuntu 7.10 ?
I want a wubi for Xubuntu 7.10 CD. where can I get that?

---

### Post by NIMBUS007 on 2008-07-05
um ago i just wanted you to know that this 'http://releases.ubuntu.com/8.04.1/' link isnt working

maybe this 'http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-i386.iso' will help :D

( i was just about to whine... than i changed my mind )

---

### Post by ago on 2008-07-05
> **plastichero said:**
> Does it work with Xubuntu 7.10 ?
I want a wubi for Xubuntu 7.10 CD. where can I get that?

8.04.1 is recommended with Xubuntu 8.04.1 and it goes around the 256M memory limit

---

### Post by ago on 2008-07-05
> **NIMBUS007 said:**
> um ago i just wanted you to know that this 'http://releases.ubuntu.com/8.04.1/' link isnt working

That gives you a page with all download options

---

### Post by NIMBUS007 on 2008-07-05
hehe well it didnt gave it to me before...

---

### Post by dheaton5 on 2008-07-06
they had a beta version b4 but im glad they came out with a final version!!!!:KS:KS:KS:KS:KS:KS:KS:KS:

---

### Post by coffee-turtle on 2008-07-07
Using Vista on a VM to download Ubuntu using the new Wubi. Not sure why the D/L speed is so low (just 64KB).  It only happens with Wubi. I am using a business class DSL broadband line and all other D/L's are very quick.

Any guidance, please?

---

### Post by ago on 2008-07-07
The mirror is selected randomly in this list ([http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink](http://releases.ubuntu.com/8.04.1/ubuntu-8.04.1-desktop-amd64.metalink)) with precedence to the mirrors that are in your country. There is also a metadl log in c:\ubuntu where you can see the details.

It might be that you were not lucky with the mirror selection. 

If you try again, a different mirror is usually selected (unless you live in a country with exactly one matching mirror in the list). 

Or simply download the ISO manually and save it in the same folder where you have wubi.exe. Make sure to match the version: wubi 8.04.1 requires a Live CD/ISO 8.04.1

---

### Post by creatifx on 2008-07-07
Running Vista x64 Enterprise, Wubi fails repeatedly at two attempts to download installation files. Response:

The download was interrupted with the error:



No error given. Have tried the installer several times, UAC off, as administrator. No luck.

Thoughts?

---

### Post by ago on 2008-07-07
> **creatifx said:**
> Running Vista x64 Enterprise, Wubi fails repeatedly at two attempts to download installation files. Response:

The download was interrupted with the error:



No error given. Have tried the installer several times, UAC off, as administrator. No luck.

Thoughts?

The Kubuntu URLS are inaccurate at the moment, [https://bugs.edge.launchpad.net/ubuntu-cdimage/+bug/246397](https://bugs.edge.launchpad.net/ubuntu-cdimage/+bug/246397) (this is a server issues), Ubuntu and Xubuntu URLs should be fine 

So for kubuntu you have to download the ISO manually or wait for it to be fixed

---

### Post by creatifx on 2008-07-07
Awesome. Thanks a bunch ago. I was just editing my post to say I was selecting Kubuntu. Will give it another go and install kubuntu post-install.

---

### Post by thomas576 on 2008-07-07
same problem as above using any version. just fyi, not sure how to get it work by downloading the 64bit .iso but i'll keep playing.

tom

---

### Post by creatifx on 2008-07-07
I downloaded the 64 bit Ubuntu .iso and had no issues getting install to run. However, I had that nice mishap where I get dumped to a busybox prompt. I think I'm just gonna do a real install.

---

### Post by thomas576 on 2008-07-07
good luck im just playing with wubi, my linux box is fine. found a wine install to play itunes i wanna try in on my windows crap box!


good luck!

---

### Post by ercerd on 2008-07-08
Avast 4.8 says there is a trojan when running wubi in the temp directory. I think its false pozitive. And i wonder is it only me getting this alert.

---

### Post by ago on 2008-07-08
[https://bugs.edge.launchpad.net/wubi/+bug/229548](https://bugs.edge.launchpad.net/wubi/+bug/229548)

---

### Post by philetus on 2008-08-07
I used Wubi 8.04.1 to install Hardy.
Then I downloaded Unetbootin and resized the Windows partition and create two partitions.

Then I rebooted and selected Ubuntu and I get a black screen and no HD activity.

---

### Post by vuvanquang on 2008-09-16
Is that possible to have more than 10Gb for Ubuntu using Wubi?
Cheers
vuvanquang

---

### Post by Orlsend on 2008-09-16
> **vuvanquang said:**
> Is that possible to have more than 10Gb for Ubuntu using Wubi?
Cheers
vuvanquang
Yeah for sure :D

---

