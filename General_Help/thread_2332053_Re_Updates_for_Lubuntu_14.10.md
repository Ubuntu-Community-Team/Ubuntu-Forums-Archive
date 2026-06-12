---
title: "Re: Updates for Lubuntu 14.10 ?"
date: 2016-07-27
forum: General Help
---

### Post by Jaque_Clarke on 2016-07-27
Installed Lubuntu 14.10 on an old Compaq Presario tower after Windows XP died on me, but on booting multiple "System problem found" warnings pop up.   
Cancel them and OS seems to work all right, dispite a few quirks. 
Are any updates available, and if so how can I download and install them? 
I'm not a real Linux whiz, and have had major problems trying to install packets.  
If the OS keeps going all weird on me, should I re install it from the CD?

Found the little icon lower right which brings up a menue containing "Check for Updates" - > "Failed to retrieve repository information".  
Oh; that's helpfull.../s

---

### Post by kansasnoob on 2016-07-27
14.10 went end of life in October 2014.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

It would be best to start with 16.04.1 at this point:

[https://wiki.ubuntu.com/XenialXerus/ReleaseNotes](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes)

Depending on your taste in desktop environments and possibly the computer specs you may prefer a different flavor:

[https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#Official_flavour_release_notes](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#Official_flavour_release_notes)

If you opened a terminal in 14.10 and posted the output of these commands we could possibly recommend which flavor would be best suited:

```
cat /proc/cpuinfo | head -10
```

```
lspci -v -s `lspci | awk '/VGA/{print $1}'`
```

```
free -m
```

Ubuntu MATE has a tweak tool that allows you to choose a Redmond layout that's quite similar to Win XP, and it runs fairly light with the Marco window manager.

---

### Post by Jaque_Clarke on 2016-07-27
Cant' run any video that relies on shockwave flash or uses HTML5 format.  
Any suggestions?

I tried copy pasting those codes into my terminal, and that is a no go.  
Typed it in and got "try cat -help" or something liek that, and that brought up a bunch of stuff about which I have nary a clue what it means.  
None of the other codes produce anything intelligible either. 
I think LINUX would be a great OS if I were smart enough to figure out how to use it properly.

This from Summary; Systems info:

```
-Computer-
Processor        : Intel(R) Pentium(R) 4 CPU 2.80GHz
Memory        : 1530MB (879MB used)
Operating System        : Ubuntu 14.10
User Name        : jaque (Jaque)
Date/Time        : Wed 27 Jul 2016 11:30:49 PM EDT
-Display-
Resolution        : 1024x768 pixels
OpenGL Renderer        : Unknown
X11 Vendor        : The X.Org Foundation
-Multimedia-
Audio Adapter        : ICH4 - Intel ICH5
-Input Devices-
 Sleep Button
 Power Button
 AT Translated Set 2 keyboard
 ImExPS/2 Logitech Explorer Mouse
-Printers-
No printers found
-SCSI Disks-
ATA ST3200822A
HL-DT-ST DVDRRW GWA-4166B
GoldStar CRD-8240B
Kingston DataTraveler SE9
Generic SD/MMC/MS/xD
Generic MicroSD/M2
Generic USB SD Reader
Generic USB CF Reader
Generic USB SM Reader
Generic USB MS Reader
```

---

### Post by Bucky Ball on 2016-07-28
You will get nowhere with an archaic, unsupported release like 14.10. It didn't reach end of life in October 2014, it was released then and was out of support nine months later.

Suggest you install a [supported release, 16.04 LTS]("http://lubuntu.me/downloads/") for instance, and we can give you support with that. You will get little to none with your current install as there is not a lot you can do. You have obsolete software which you can't update and the machine is a security risk if its online as it hasn't had a security update in over a year.

So the answer to your question is no. There are no updates for 14.10 and won't be in future. That release is now part of history. :)

---

### Post by grahammechanical on 2016-07-28
To make things a little clearer for anyone reading this thread,

Each  release of Ubuntu has its own set of software repositories. These  repositories contain the applications that we can install from the  software centre. They are also the place that updates are put.

When  each version of Ubuntu reaches the end of its support period its  repositories are closed. In fact that are moved to another location.  Therefore, all the URLs that point to the repositories for that version  are broken.

And that is why we cannot update an out of life version of Ubuntu or install any applications.

There  is a real cost to providing support for each version of Ubuntu. The  more versions that are supported the more costly it becomes especially  as Quality Assurance (testing all software) is very important to Ubuntu  maintainers. We get a new release of Ubuntu every six months. And every  two years at the end of April we get a Long Term Support (5 years)  release. In between those LTS releases the Interim versions only have 9  months support.

We get a good deal but we should be prepared to  upgrade to the latest version if we are running on an Interim version or  the latest LTS version if we are running on an LTS version.

Even the experts in Linux will not get any success if using an out of support version of Ubuntu.

Regards.

---

### Post by kansasnoob on 2016-07-28
> **Bucky Ball said:**
> You will get nowhere with an archaic, unsupported release like 14.10. It didn't reach end of life in October 2014, it was released then and was out of support nine months later.

Oops, should have said reached EOL July 2015. That was only about the 40th mistake I made yesterday :oops:

---

### Post by Bucky Ball on 2016-07-28
> **kansasnoob said:**
> Oops, should have said reached EOL July 2015. That was only about the 40th mistake I made yesterday :oops:

Hehe. It happens. Only proves you're human. :)

---

