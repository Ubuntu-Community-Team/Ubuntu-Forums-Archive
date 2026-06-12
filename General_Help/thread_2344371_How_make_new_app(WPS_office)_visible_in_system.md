---
title: "How make new app(WPS office) visible in system?"
date: 2016-11-24
forum: General Help
---

### Post by juntjoo2 on 2016-11-24
I just downloaded their app and apparently it comes already assembled and ready to go right from it's folder after extracting it but the system won't see it if you search for it by the search for apps app nor will it find it if you try to manually open a file and choose which app you want to use. Although I can go straight to the folder I download and open the app there and use it to find then open my files. So how do you get it to be seen by the system? Is there a folder I need to put it in? Thanks

Oh okay. It's an "RPM" file meaning it's special somehow. I'll be back...

---

### Post by #&amp;thj^% on 2016-11-24
'RPM'= originally called the Red-hat Package Manager, IE Fedora, Redhat OpenSuse..
You Probably are looking for .Deb IE Debian Based.

---

### Post by mastablasta on 2016-11-25
yup, you need to download one of these two: 

for Ubuntu 32bit:

wps-office_10.1.0.5672~a21_i386.deb
SHA1SUM: a5e33090a58289db4b6ed7c0a05532e51428f9a7

for Ubuntu 64bit:

wps-office_10.1.0.5672~a21_amd64.deb
SHA1SUM: 80d884c47eaeee3305958ed87e61eafbee30b0cf

download link:
[SIZE=2]http://wps-community.org/downloads
[/SIZE]

---

### Post by juntjoo2 on 2016-11-25
Thanks

> **mastablasta said:**
> yup, you need to download one of these two: 

for Ubuntu 32bit:

wps-office_10.1.0.5672~a21_i386.deb
SHA1SUM: a5e33090a58289db4b6ed7c0a05532e51428f9a7

for Ubuntu 64bit:

wps-office_10.1.0.5672~a21_amd64.deb
SHA1SUM: 80d884c47eaeee3305958ed87e61eafbee30b0cf

download link:
[SIZE=2]http://wps-community.org/downloads
[/SIZE]

what about this one: [wps-office-10.1.0.5672-1.a21.x86_64.rpm]("http://kdl.cc.ksosoft.com/wps-community/download/a21/wps-office-10.1.0.5672-1.a21.x86_64.rpm")

I tried installing this one because I thought it's what my system needed being "intel" and not "amd" though I'm not so sure of the difference or why there are two versions of the 64bit version.  Anyway, it appears they stopped supporting this linux version of their software and when I tried installing this "x86" version I got a lot of errors which I'm guessing has to do with the discontinuation though idk.  I'll try this amd one I guess...

also, what about this "rpm" one? is it not supposed to be compatible? as I mentioned the extracted folder contains working apps though just not installed into the system as I'd prefer.  Would you(or anyone) happen to know how to integrate this into my system so I don't have to go to the folder every time I want to use it?  The apps appear to be compatible. Should they not be?

---

### Post by vasa1 on 2016-11-25
> **juntjoo2 said:**
> Oh okay. It's an "RPM" file meaning it's special somehow. I'll be back...

> **juntjoo2 said:**
> what about this one: [wps-office-10.1.0.5672-1.a21.x86_64.rpm]("http://kdl.cc.ksosoft.com/wps-community/download/a21/wps-office-10.1.0.5672-1.a21.x86_64.rpm")

I tried installing this one because I thought it's what my system needed being "intel" and not "amd" though I'm not so sure of the difference or why there are two versions of the 64bit version.  Anyway, it appears they stopped supporting this linux version of their software and when I tried installing this "x86" version I got a lot of errors which I'm guessing has to do with the discontinuation though idk.  I'll try this amd one I guess...

Look for .deb versions, not .rpm versions. Ubuntu is based on _Deb_ian and uses .deb packaging.

---

### Post by Impavidus on 2016-11-25
> **juntjoo2 said:**
> 
I tried installing this one because I thought it's what my system needed being "intel" and not "amd" though I'm not so sure of the difference or why there are two versions of the 64bit version.

amd64 is called like that for historical reasons: AMD designed the 64 bit technology (at least, the version everyone uses), Intel copied it under some patent exchange agreement. So the amd64 version is the one you need on 64 bit systems, both Intel and AMD.

There are 2 major package management systems on Linux: RPM, used by Fedora, Redhat etc. and dpkg, used by Debian, Ubuntu etc. For use on Ubuntu you can best pick the .deb file, which is designed for the dpkg package manager. It's the same software, packaged differently. Double click it after download and your computer should know how to install it.

---

### Post by vasa1 on 2016-11-25
In your earlier thread [clueless. where to start?]("https://ubuntuforums.org/showthread.php?t=2343846"), people suggested that installing software from anywhere but the standard repos isn't advisable until you really know what you're doing (posts #4, #6, and #8) to which your response (post #10) was> thanks guys. i hear ya. ill stick with the wizards when possibleSo I'm guessing this WPS Office is something you really need? LibreOffice won't suffice?

---

### Post by fenrice on 2016-11-25
There's nothing wrong with WPS, I've used it for a while. LibreOffice has wrecked some more complicated documents for me that WPS handled just fine. 

Original Poster, like other people said if you're going to get stand alone software for your system. Make sure they point out which version of your operating system (Ubuntu 16.10) in my case. You need to find the ".deb" packages. .rpm versions will not work for you, especially at your level of experience. It's not a mac, you can't just drop the installer somewhere. You have to actually install it like you do on windows. In Ubuntu you should be able to click on it and Ubuntu will pop up and install option.

---

### Post by juntjoo2 on 2016-11-25
> **Impavidus said:**
> amd64 is called like that for historical reasons: AMD designed the 64 bit technology (at least, the version everyone uses), Intel copied it under some patent exchange agreement. So the amd64 version is the one you need on 64 bit systems, both Intel and AMD.

There are 2 major package management systems on Linux: RPM, used by Fedora, Redhat etc. and dpkg, used by Debian, Ubuntu etc. For use on Ubuntu you can best pick the .deb file, which is designed for the dpkg package manager. It's the same software, packaged differently. Double click it after download and your computer should know how to install it.

Thank you. I eventually got it installed using the command terminal because apparently my package manager/installer doesn't work or something.  It just hangs after hitting install.

> **vasa1 said:**
> In your earlier thread [clueless. where to start?]("https://ubuntuforums.org/showthread.php?t=2343846"), people suggested that installing software from anywhere but the standard repos isn't advisable until you really know what you're doing (posts #4, #6, and #8) to which your response (post #10) wasSo I'm guessing this WPS Office is something you really need? LibreOffice won't suffice?

I haven't had much luck with my installer plus I wanted to start figuring out how to use the command terminal since there seems to be a lot of apps that need that to work.

As far as libreoffice, I'm coming from ms office and they have a great app for android which I like to use so I'm experimenting with different ways to keep that setup. There is an openoffice app for android which is really cool as a straight port of the desktop app but not really optimized for mobile.  It's a possibility but I'd prefer to stick to ms format

---

