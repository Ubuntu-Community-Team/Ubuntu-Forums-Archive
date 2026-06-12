---
title: "installing hal"
date: 2012-11-08
forum: General Help
---

### Post by Skele on 2012-11-08
I ran 'sudo apt-get install hal' and it started doing something until it showed me this message:
"TrueType core fonts for the Web EULA                                                                                                              END-USER LICENSE AGREEMENT FOR MICROSOFT SOFTWARE IMPORTANT-READ CAREFULLY: This Microsoft End-User License Agreement ("EULA") is a legal agreement between you (either an individual or a single entity) and Microsoft Corporation for the Microsoft software accompanying this EULA, which includes computer software and may include associated media, printed materials, and "on-line" or electronic documentation ("SOFTWARE PRODUCT" or "SOFTWARE"). By exercising your rights to make and use copies of the SOFTWARE PRODUCT, you agree to be bound by the terms of this EULA. If you do not agree to the terms of this EULA, you may not use the SOFTWARE PRODUCT. SOFTWARE PRODUCT LICENSE The SOFTWARE PRODUCT is protected by copyright laws and international copyright treaties, as well as other intellectual property laws and treaties. The SOFTWARE PRODUCT is licensed, not sold.
1. GRANT OF LICENSE. This EULA grants you the following rights:  • Installation and Use. You may install and use an unlimited number of copies of the SOFTWARE PRODUCT.
  • Reproduction and Distribution. You may reproduce and distribute an unlimited number of copies of the SOFTWARE PRODUCT; provided that each copy shall be a true and complete copy, including all copyright and trademark notices, and shall be accompanied by a copy of this EULA. Copies of the SOFTWARE PRODUCT may not be distributed for profit either on a standalone basis or included as part of your own product.
2. DESCRIPTION OF OTHER RIGHTS AND LIMITATIONS.
  • Limitations on Reverse Engineering, Decompilation, and Disassembly. You may not reverse engineer, decompile, or disassemble the SOFTWARE PRODUCT, except and only to the extent that such activity is expressly permitted by applicable law notwithstanding this limitation. Restrictions on Alteration. You may not rename, edit or create any derivative works from the SOFTWARE PRODUCT, other than subsetting when embedding them in documents.
  • Software Transfer. You may permanently transfer all of your rights under this EULA, provided the recipient agrees to the terms of this EULA.                                                       
  • Termination. Without prejudice to any other rights, Microsoft may terminate this EULA if you fail to comply with the terms and conditions of this EULA. In such event, you must destroy all copies of the SOFTWARE PRODUCT and all of its component parts.
 
3. COPYRIGHT. All title and copyrights in and to the SOFTWARE PRODUCT (including but not limited to any images, text, and "applets" incorporated into the SOFTWARE PRODUCT), the accompanying printed materials, and any copies of the SOFTWARE PRODUCT are owned by Microsoft or its suppliers. The SOFTWARE PRODUCT is protected by copyright laws and international treaty provisions. Therefore, you must treat the SOFTWARE PRODUCT like any other copyrighted material.
                                                                              
 4. U.S. GOVERNMENT RESTRICTED RIGHTS. The SOFTWARE PRODUCT and documentation are provided with RESTRICTED RIGHTS. Use, duplication, or disclosure by the Government is subject to restrictions as set forth in subparagraph (c)(1)(ii) of the Rights in Technical Data and Computer Software clause at DFARS 252.227-7013 or subparagraphs (c) (1) and (2) of the Commercial Computer Software - Restricted Rights at 48 CFR 52.227-19, as applicable. Manufacturer is Microsoft Corporation/One Microsoft Way/Redmond, WA 98052-6399.
LIMITED WARRANTY
NO WARRANTIES. Microsoft expressly disclaims any warranty for the SOFTWARE PRODUCT. The SOFTWARE PRODUCT and any related documentation is provided "as is" without warranty of any kind, either express or implied, including, without limitation, the implied warranties or merchantability, fitness for a particular purpose, or noninfringement.
The entire risk arising out of use or performance of the SOFTWARE PRODUCT remains with you. NO LIABILITY FOR CONSEQUENTIAL DAMAGES. In no event shall Microsoft or its suppliers be liable for any damages whatsoever (including, without limitation, damages for loss of business profits, business interruption, loss of business information, or any other pecuniary loss) arising out of the use of or inability to use this Microsoft product, even if Microsoft has been advised of the possibility of such damages. Because some states/jurisdictions do not allow the exclusion or limitation of liability for consequential or incidental damages, the above limitation may not apply to you.    
MISCELLANEOUS                                                                
If you acquired this product in the United States, this EULA is governed by the laws of the State of Washington.                                      
If this product was acquired outside the United States, then local laws may apply. Should you have any questions concerning this EULA, or if you desire to contact Microsoft for any reason, please contact the Microsoft subsidiary serving your country, or write: Microsoft Sales Information Center/One Microsoft Way/Redmond, WA 98052-6399.

Reference: http://www.microsoft.com/typography/fontpack/eula.htm"

And then it had an ok button under it that I couldn't press. Now I love microsoft very much, but can anyone tell me how I can get forward in this?

---

### Post by hal8000 on 2012-11-08
If you want to install MS fonts these are called mscorefonts the link below gives more detailed instructions:

[http://www.howtogeek.com/howto/15495/add-microsoft-core-fonts-to-ubuntu/](http://www.howtogeek.com/howto/15495/add-microsoft-core-fonts-to-ubuntu/)


hal (Hardware Abstraction Layer) is being dropped in favour of udev:

[https://wiki.ubuntu.com/Halsectomy](https://wiki.ubuntu.com/Halsectomy)

If there is some function or reason or hardware problem that you need hal
then you need to give detail, otherwise udev should work.

Hope that helps.

---

### Post by Zill on 2012-11-08
> **Skele said:**
> ...Reference: http://www.microsoft.com/typography/fontpack/eula.htm"

And then it had an ok button under it that I couldn't press. Now I love microsoft very much, but can anyone tell me how I can get forward in this?
To select the "ok" button simply hit tab, then enter to select.  HTH.

---

### Post by Skele on 2012-11-08
I got hal installed through the software center but the reason why I needed it didn't fix anything. But I don't think you can solve the main problem.

---

### Post by 2F4U on 2012-11-08
HAL has been deprecated with 10.04. What version of Ubuntu are you using. On 10.04 and newer hal is not needed.

---

### Post by Zill on 2012-11-08
> **Skele said:**
> I got hal installed through the software center but the reason why I needed it didn't fix anything. But I don't think you can solve the main problem.
It might help if you tell us what "the main problem" is!
> HAL provides an abstract view on hardware.

This abstraction layer is simply an interface that makes it possible to add support for new devices and new ways of connecting devices to the computer, without modifying every application that uses the device. It maintains a list of devices that currently exist, and can provide information about those upon request.
I may be mistaken but, AIUI, HAL has nothing to do with Microsoft TrueType core fonts.  If you simply wish to use Microsoft TrueType fonts then just install ttf-mscorefonts-installer.  I explained in post [#3]("http://ubuntuforums.org/showpost.php?p=12344027&postcount=3") how to select the OK button for the Microsoft EULA.
```
sudo apt-get install ttf-mscorefonts-installer
```
Alternatively, if you would like a few more "goodies", you could install ubuntu-restricted-extras which includes the ttf-mscorefonts-installer along with several other useful packages.
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by pqwoerituytrueiwoq on 2012-11-08
> **2F4U said:**
> HAL has been deprecated with 10.04. What version of Ubuntu are you using. On 10.04 and newer hal is not needed.
some apps still use it, like hwinfo and i am on 12.10

---

### Post by Skele on 2012-11-11
Ok, let's go with the main problem. I have Ubuntu 12.04. I was trying to use a net based application that runs on adobe flash player. The application started smoothly but when I accessed the flash player options with the right mouse button, it showed me the options menu but none of the buttons worked. The application just froze. Same thing was with the "save on computer"-feature, it showed me the "do you want to save on your computer"-window but none of the buttons worked.

Why I needed to know about hal was because there was a solution to getting the problem fixed by installing hal but it didn't work.

---

### Post by dino99 on 2012-11-11
you probably know that adobe have changed , some months ago, their flash policy; its no more a free app.

---

### Post by Zill on 2012-11-11
> **Skele said:**
> Ok, let's go with the main problem. I have Ubuntu 12.04. I was trying to use a net based application that runs on adobe flash player. The application started smoothly but when I accessed the flash player options with the right mouse button, it showed me the options menu but none of the buttons worked. The application just froze. Same thing was with the "save on computer"-feature, it showed me the "do you want to save on your computer"-window but none of the buttons worked...
It might help if you gave us some more information.  For example, assuming that access is not restricted, what is the web address of your problematic "net based application"?

Please also advise which version of flash you have installed and how you installed it.  Are you running a 32 or 64 bit system?

Does flash work OK with other websites?  Do you see any animation when you go to the [Adobe Flash Player test page]("http://www.adobe.com/software/flash/about/")?

---

### Post by Skele on 2012-11-11
My flash player is version 11,2,202,243. I'm running a 32 bit system. Every single adobe application works but every time I try to access the settings or the "save on comp"-window pops up the application freezes no matter what application I am running.

---

### Post by Zill on 2012-11-12
In post [#10]("http://ubuntuforums.org/showpost.php?p=12348517&postcount=10") I asked six questions of which you have answered just two!
> **Skele said:**
> My flash player is version 11,2,202,243.
The current version of Adobe Flash Player for Linux is 11.2.202.251 and so I recommend you upgrade to the current version.  This is why I asked *how* you installed flash because, as you apparently have an older version installed, either it must have been installed manually *or* your system is not fully updated.  If you have installed flash manually then I suggest you totally remove this and then reinstall flash using the latest Ubuntu deb package:
```
sudo apt-get install flashplugin-installer
```
If it is simply that your system has not been fully updated then I suggest you run the following two commands:
```
sudo apt-get update
sudo apt-get upgrade
```
Either way, you should end up with flash version 11.2.202.251
> **Skele said:**
> Every single adobe application works but every time I try to access the settings or the "save on comp"-window pops up the application freezes no matter what application I am running.
I don't understand this statement.  Are you referring to Adobe Flash applications or other Adobe applications such as the PDF reader?

As previously requested, it would be very useful if you would provide a weblink to a site you are having difficulty with.

Again, as previously requested, please advise:
[LIST][*]Does flash work OK with other websites? (such as [YouTube]("www.youtube.com/"))
[*]Do you see any animation when you open the [Adobe Flash Player test page]("http://www.adobe.com/software/flash/about/")?[/LIST]
Finally, which web browser(s) are you running - and which version?

---

### Post by Skele on 2012-11-15
I uninstalled the adobe flash player through ubuntu software center, ran all the commands you said and it still says it's 11,2,202,243 and the problem is still there.

I don't have a adobe based pdf-viewer. Every net-based adobe application freezes when I go to the setting window with the right mouse button. Here's an example [http://www.youtube.com/watch?v=XHUsIU161w4&feature=list_other&playnext=1&list=AL94UKMTqg-9ANxPPPdVGhQ3Hx4Rlr1LbV](http://www.youtube.com/watch?v=XHUsIU161w4&feature=list_other&playnext=1&list=AL94UKMTqg-9ANxPPPdVGhQ3Hx4Rlr1LbV)

The test page shows perfectly. The animation works perfectly. I'm running chromium 20.0.1132.47.

---

### Post by Zill on 2012-11-15
> **Skele said:**
> I uninstalled the adobe flash player through ubuntu software center, ran all the commands you said and it still says it's 11,2,202,243 and the problem is still there...
It *really* would help if you answered *all* the questions I have asked!  I have specifically asked (twice!) *how* you installed flash?  In other words, did you install the flashplugin-installer or ubuntu-restricted-extras package from the Ubuntu repos *or* did you download flash directly from another website (such as get.adobe.com) *or* did you use something like flash-aid?

Please now open a terminal (Ctrl-Alt-t) and enter the following command, then post the full output.  Please enclose the full output in "code" tags.
```
cat /etc/lsb-release
```
Enter the following command, then post the full output.  Please enclose the full output in "code" tags.
```
apt-cache policy flashplugin-installer
```
Enter the following command, then post the full output.  Please enclose the full output in "code" tags.
```
apt-cache policy firefox
```
> **Skele said:**
> ...Every net-based adobe application freezes when I go to the setting window with the right mouse button. Here's an example [http://www.youtube.com/watch?v=XHUsIU161w4&feature=list_other&playnext=1&list=AL94UKMTqg-9ANxPPPdVGhQ3Hx4Rlr1LbV](http://www.youtube.com/watch?v=XHUsIU161w4&feature=list_other&playnext=1&list=AL94UKMTqg-9ANxPPPdVGhQ3Hx4Rlr1LbV)

The test page shows perfectly. The animation works perfectly. I'm running chromium 20.0.1132.47.

As Ubuntu has Firefox installed by default, I suggest it would help if we stuck to Firefox for this exercise, only tackling Chromium after we get things working with Firefox.

I attach my screendump of your example youtube video, showing the right-click menus I have.  Please advise specifically *which* of these menu items do not seem to work correctly for you (or cause freezing) **[COLOR="Red"]when you are using Firefox?[/COLOR]**

---

### Post by Skele on 2012-11-15
I forgot to answer that question. I installed it through the ubuntu software center, but I upgraded with the terminal with both of the codes you gave me. I fixed the update problem on chromium. It had an extra flash-player file in the plugins section in lib and I removed it. Now it's using the newest.

```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"
```

```
flashplugin-installer:
  Installed: 11.2.202.251ubuntu0.12.04.1
  Candidate: 11.2.202.251ubuntu0.12.04.1
  Version table:
 *** 11.2.202.251ubuntu0.12.04.1 0
        500 http://archive.ubuntu.com/ubuntu/ precise-updates/multiverse i386 Packages
        500 http://archive.ubuntu.com/ubuntu/ precise-security/multiverse i386 Packages
        100 /var/lib/dpkg/status
     11.2.202.233ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ precise/multiverse i386 Packages
```


```
firefox:
  Installed: 16.0.2+build1-0ubuntu0.12.04.1
  Candidate: 16.0.2+build1-0ubuntu0.12.04.1
  Version table:
 *** 16.0.2+build1-0ubuntu0.12.04.1 0
        500 http://archive.ubuntu.com/ubuntu/ precise-updates/main i386 Packages
        500 http://archive.ubuntu.com/ubuntu/ precise-security/main i386 Packages
        100 /var/lib/dpkg/status
     11.0+build1-0ubuntu4 0
        500 http://archive.ubuntu.com/ubuntu/ precise/main i386 Packages
```

It doesn't allow me to take a screenshot when I have the right click options on screen, but it's the option labeled "settings" as I said before.

And no, it doesn't work with firefox either.

---

### Post by Zill on 2012-11-15
> **Skele said:**
> ...It doesn't allow me to take a screenshot when I have the right click options on screen, but it's the option labeled "settings" as I said before.
To take a screenshot with the right-click options on screen use a time delay (in seconds).  eg.  Open a terminal and then enter the following code:
```
gnome-screenshot --delay=5
```
Take focus back to the web-browser, hit the right-click, and a couple of seconds later you will have your snapshot, including options.

Just to make sure we are talking about the same thing I have highlighted the "settings" option in my menu.  See attached screendump "Screenshot with highlight.png".

If I click on this option I get five tabs for "Adobe Flash Player Settings", the first being entitled "Display".  This tab contains a checkbox to "Enable Hardware Acceleration".  See attached screendump "Screenshot-1.png".

Using **Firefox** (not Chromium!), do you see the same five tabs?  If so, do they operate normally?  If not, exactly what does happen and when?

If you do get a freeze at any point I suggest you toggle the "Enable Hardware Acceleration" checkbox, then restart Firefox and go back to the same website and test again.

---

