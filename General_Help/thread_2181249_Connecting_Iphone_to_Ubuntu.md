---
title: "Connecting Iphone to Ubuntu"
date: 2013-10-17
forum: General Help
---

### Post by kuwaiti on 2013-10-17
Please I need help ,, 

I have a copy of Ubuntu Version 13.4 and i can't connect my iPhone 5 to my Ubuntu 13.4 machine, and every time i receive this message ,, .. Trust This Computer ..  When i chose : Trust .. The same message comes again &#128553;

---

### Post by CamPsych on 2013-10-26
Yep, I am having the same problem with an iPhone 4, any of the music players (Banshee, Clementine) all seem to crashe when the phone is plugged in. I have looked around and there seems to be very little on a workaround for this issues.

---

### Post by kylakemike on 2013-10-28
Same issue same question. Cannot mount iphone on the laptop and the iphone shows the trust/don't trust dialogue box to which I reply "trust" yet the dialogue persists. This using Ubuntu 13.10 and iphone 42 running iOS 7.03. Any and all help greatly appreciated.

---

### Post by tgalati4 on 2013-10-28
The "Circle of Trust" is also known as the "Walled Garden".  As long as you are using Apple products, they will talk to each other.  Venture outside of the Walled Garden, and you will have problems.

This page needs some updating:  [https://help.ubuntu.com/community/PortableDevices/iPod](https://help.ubuntu.com/community/PortableDevices/iPod)

Perhaps detailing your experiences with iPhone 4 and 5 with Ubuntu 13.04 (or 13.10) can help improve this page.

What works and what doesn't?

---

### Post by kylakemike on 2013-10-30
Nothing works on 13.10 with iOs 7.03 on iPhone 4S. All that happens is you wind up in the trust/don't trust circle. Cannot access files, cannot sync with any music program. Nothing.

---

### Post by kylakemike on 2013-11-03
Anyone else experiencing this issue? Anyone have any thoughts on a resolution? 

TIA - Kylakemike

---

### Post by smith-chad12 on 2013-11-03
> **tgalati4 said:**
> The "Circle of Trust" is also known as the "Walled Garden".  As long as you are using Apple products, they will talk to each other.  Venture outside of the Walled Garden, and you will have problems.

This page needs some updating:  [https://help.ubuntu.com/community/PortableDevices/iPod](https://help.ubuntu.com/community/PortableDevices/iPod)

Perhaps detailing your experiences with iPhone 4 and 5 with Ubuntu 13.04 (or 13.10) can help improve this page.

What works and what doesn't?

Wouldn't quite say "as long as you're using Apple Products," as they work just fine on Windows, more like "As long as you're using products Apple will provide support on."  Apple just doesn't provide support for Linux but it works on Windows since Apple provides support for iTunes on Windows.  From what I have understood it seems to be a problem with iOS7 with a new security feature (a pretty good one I must say) and the older versions of iOS.

---

### Post by kylakemike on 2013-11-04
> **smith-chad12 said:**
> Wouldn't quite say "as long as you're using Apple Products," as they work just fine on Windows, more like "As long as you're using products Apple will provide support on."  Apple just doesn't provide support for Linux but it works on Windows since Apple provides support for iTunes on Windows.  From what I have understood it seems to be a problem with iOS7 with a new security feature (a pretty good one I must say) and the older versions of iOS.

Definitely an issue with ios 7 as it has worked previously with earlier ios versions. There has got to be a workaround for the security in ios 7.

---

### Post by kylakemike on 2013-11-19
Would appear this issue remains as I received a bug report update today indicating that is the case.

---

### Post by kylakemike on 2013-12-11
Has anyone located any information that this problem is being addressed?

TIA - kylakemike

---

### Post by CamPsych on 2013-12-11
I don't believe that there will be a resolution any time soon, as this has been an issue with Linux/Apple for a long time. Essentially, from my understanding, the issue is that it is an Apple/Apple problem, and yes, it is OK on Windows, but this is because the Apple program iTunes is able to be run on that OS. Unfortunately, even in WINE iTunes will not work. Hate to be the bearer of bad news, but I'm not seeing a work around. 

On the other hand, for music, so MP3 players (I think the one I use is MP3 Player) on the App Store, will allow you to drop music into them on the iPhone, but they will not allow syncing, or deletion of music if it is already there from previous interaction with iTunes. They can be used through WiFi, so no need to plug in and get that infernal Trust circle.

---

### Post by dusanyu on 2013-12-18
Last report is on the page for [libimobiledevice](http://www.libimobiledevice.org/)

> 20.08.2013: iOS 7 is working but we want it to work beautifully. There is need for refactoring of the architecture a bit on Linux, too. The next release of version 1.1.6 will provide proper support without the hickups.

---

### Post by Eugene King on 2013-12-18
If you go to the Ubuntu Specialized Support section of this forum there is a Apple section.

As for the mounting problem. 

I am using Kernel 3.8 on my USB Lubuntu 12.04 and after the latest update it was fixed. it now tethers VIA USB under Auto ethernet.

I can also access pictures and movies.

---

### Post by frncz on 2013-12-19
Even though my iphone is not mounted and I have the 'Trust/Don't Trust' screen on my iphone, Shotwell does find all the photos on my iphone. I can therefore import selected photos to my desktop!

Shotwell finds the way to connect!

---

### Post by GrouchyGaijin on 2014-01-25
> **Eugene King said:**
> 

I am using Kernel 3.8 on my USB Lubuntu 12.04 and after the latest update it was fixed. it now tethers VIA USB under Auto ethernet.

I can also access pictures and movies.

I'm on 12.04 of Ubuntu and only have kernel 3.5.0-45, which I thought was up to date since that is the latest I've gotten via the Update Manager.
I have noticed however that as long as I ignore the *Do you trust *message on the iPhone 5, I can use a home made script I have to remove images and videos from the camera then upload the images to the web server.

_**If I click yes**_ I trust this computer on the phone, I _cannot access_ the images or videos that are on the phone.

---

### Post by Dudule Crapouille on 2014-02-22
[TABLE]
[TR]
[TD="class: votecell"]        

              
[/TD]
                [TD="class: answercell"]                  I'm Using 13.10 x86_64. The solution for me was to download  libimobiledevice4_1.1.6-git20140105_amd64.deb. 
This can be found here:

  [https://launchpadlibrarian.net/161787269/libimobiledevice4_1.1.6-git20140105_amd64.deb](https://launchpadlibrarian.net/161787269/libimobiledevice4_1.1.6-git20140105_amd64.deb)

[/TD]
[/TR]
[/TABLE]

---

### Post by Douglas_Twyman on 2014-03-04
This worked for me as well 

> **Dudule Crapouille said:**
> [TABLE]
[TR]
[TD="class: votecell"]
              [/TD]
[TD="class: answercell"]                  I'm Using 13.10 x86_64. The solution for me was to download  libimobiledevice4_1.1.6-git20140105_amd64.deb. 
This can be found here:

  [https://launchpadlibrarian.net/161787269/libimobiledevice4_1.1.6-git20140105_amd64.deb](https://launchpadlibrarian.net/161787269/libimobiledevice4_1.1.6-git20140105_amd64.deb)
[/TD]
[/TR]
[/TABLE]


---

