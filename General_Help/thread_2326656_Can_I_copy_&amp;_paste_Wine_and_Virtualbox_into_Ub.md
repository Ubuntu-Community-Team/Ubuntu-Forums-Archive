---
title: "Can I copy &amp; paste Wine and Virtualbox into Ubuntu while in Windows?"
date: 2016-06-03
forum: General Help
---

### Post by christaliise on 2016-06-03
THIS WOULD PROBABLY NEED TO BE ANSWERED BY A DEVELOPER OF UBUNTU.


Obtaining a distro that has "Wine" and "Virtualbox" installed by default would be ideal, but that is not possible.


Can I download "Wine" and "Virtualbox" into my Windows 10 laptop then copy and paste those applications into Ubuntu that I have already downloaded and still in my Windows 10 laptop, and with the amended Ubuntu download, burn it to a DVD, then insert into the DVD Drive and install into my new computer?


When I click on the Ubuntu download, which is in my Windows 10 laptop, I come up with folders just the same as in Windows.


If that will work, I need to know where to download "Wine" and "Virtualbox" from.


Then I need to know which folders to paste "Wine" and "Virtualbox" into.


My Internet connection is an USB Stick and Windows based so I need one or both to get online, with my new computer.


If I plug the USB Stick into a Windows computer the console automatically installs. But nothing happens if I plug the USB Stick into Ubuntu.


I am not yet connected to the Internet with my new laptop, so please no answers assuming I'm connected to the Internet with my new laptop.


I am only connected to the Internet with my old laptop which has Windows 10.

---

### Post by grahammechanical on 2016-06-03
> THIS WOULD PROBABLY NEED TO BE ANSWERED BY A DEVELOPER OF UBUNTU.

This is a user forum. You will not get an answer from a developer on this forum. But if you will accept an answer from a lowly user, then if copy & paste of folders was the way to install programs, then we would all be doing it. We would not need installer programs to do the job for us. Windows users cannot install programs by copying folders to the disk drive. Neither does it work that way in Linux.

Windows programs will not run on Linux. Likewise, Linux programs will not run on Windows. You need to install a Windows version of Virtualbox. Then install Ubuntu into a virtual machine using the Ubuntu ISO image and then install Wine inside Ubuntu using the Ubuntu Software Centre.

> Presently, VirtualBox runs on Windows, Linux, Macintosh, and Solaris hosts and supports a large number of [guest operating systems]("https://www.virtualbox.org/wiki/Guest_OSes")  including but not limited to Windows (NT 4.0, 2000, XP, Server 2003,  Vista, Windows 7, Windows 8, Windows 10), DOS/Windows 3.x, Linux (2.4,  2.6, 3.x and 4.x), Solaris and OpenSolaris, OS/2, and OpenBSD.

[https://www.virtualbox.org/](https://www.virtualbox.org/)

[https://www.virtualbox.org/manual/ch02.html](https://www.virtualbox.org/manual/ch02.html)

---

### Post by jim_deadlock on 2016-06-03
It is possible to create an Ubuntu image with certain software preinstalled, but it's far more complicated than the method you are suggesting. Even if you did manage to get the installer working within Wine/VB, it's designed to install Windows drivers anyway so it would still be no use for Ubuntu. Your whole plan is doomed I'm afraid.

Your best course of action is to install Ubuntu in the normal way via a WIRED connection if possible and do a full update, then you may find that the USB internet stick does work with Ubuntu and you can unplug the cable - Ubuntu is designed to work with a vast number of devices without the need for additional driver software, but sometimes you need to install/update first. I know it's not what you want to hear but you're on a wild goose chase with the Wine/VB thing.

---

### Post by christaliise on 2016-06-03
I have 3 laptops. (1) I bought about 10 years ago and was the cheapest I could buy at the time, with Windows XP, and it was fast, but it died of over work. (2) I bought about 5 years ago originally with Windows 7 but early this year I upgraded to Windows 10, it has always been slow but worse since Windows 10. (3) I bought 1 month ago, with a fast processor and only FreeDOS, I first installed Ubuntu, then SolydK, then Debian. I'm uninpressed with the later two. I am not yet connected to the Internet with my new laptop. The ISP is only Windows based.


If I can't install Wine & Virtualbox into Ubuntu, or I can't download Ubuntu with Wine & Virtualbox already installed, then I have no choice but to abandon Ubuntu. It appears as if my only other choice is go with Windows XP but I'm trying to keep away from MS products.


Ubuntu should be more versatile. Whether we like it or not, Windows based products are very common, obviously because MS are very versatile. But I think slowing down computers is motivated by the selling new computers with Windows installed.


How can I contact the developers of Ubuntu?

---

### Post by christaliise on 2016-06-03
> **grahammechanical said:**
> You need to install a Windows version of Virtualbox. Then install Ubuntu into a virtual machine using the Ubuntu ISO image and then install Wine inside Ubuntu using the Ubuntu Software Centre.

Where do I install the Window version of Virtualbox, in my Windows 10 laptop or my new laptop with no Internet connection?

---

### Post by howefield on 2016-06-03
> **christaliise said:**
> I am not yet connected to the Internet with my new laptop. The ISP is only Windows based.

Is this the issue that is giving rise to the original post, most ISPs will only support Windows but most can be connected to with Linux, that may not be the case for where you are, just wanted to mention it. 

> If I can't install Wine & Virtualbox into Ubuntu, or I can't download Ubuntu with Wine & Virtualbox already installed, then I have no choice but to abandon Ubuntu. It appears as if my only other choice is go with Windows XP but I'm trying to keep away from MS products.

Zorin OS comes with Wine and Play on Linux preinstalled, or at least it used to. I'm not sure about Virtualbox though.

> Ubuntu should be more versatile. Whether we like it or not, Windows based products are very common, obviously because MS are very versatile. But I think slowing down computers is motivated by the selling new computers with Windows installed.

A sensible question would be needed to produce a sensible answer to this.

> How can I contact the developers of Ubuntu?

Depends on your preferred mode of communication, but you might like to try the contact us link at ubuntu.com, funnily enough.

---

### Post by jim_deadlock on 2016-06-03
Am I right in assuming your fixation with Wine/VB is because you want to make the .exe installer work so that you can get your USB stick to connect to the internet via Ubuntu? If so, that WILL NOT WORK even if you manage to set up Ubuntu with Wine/VB because the installer will try to install Windows drivers AND FAIL.

---

### Post by X-RED_Tech on 2016-06-03
> **christaliise said:**
> Where do I install the Window version of Virtualbox, in my Windows 10 laptop or my new laptop with no Internet connection?

Don't go there... It seems your question was misunderstood.

**All you want to do is add software to the standard Ubuntu ISO so it gets installed like the rest of the stuff when you use the new, "cooked" image to install, right?** You mentioned Wine and Virtualbox (both not included by default) but it could be anything else, right? If not please clarify what your goal is so the help can be more assertive. 
Assuming it is, I've heard about some tools for remastering but never used it. The experts here surely can give a couple of suggestions. Problem: There's no such tools for Windows and never will. So, you may be able to do what you want but not in Windows where, at best, you can download the Ubuntu ISO and check its contents.

---

### Post by jim_deadlock on 2016-06-03
I think what everyone is missing is that he wants to install Ubuntu on his new laptop but the only way he has to connect to the internet is with a USB dongle which has a Win installer, so he thinks that if he can install Ubuntu on his new laptop with Wine/VB preinstalled (without any internet connection), then he can run the Windows installer for the driver for his dongle via Wine and connect the laptop that way. It won't work, of course.

---

### Post by QIII on 2016-06-03
Hello!

What end state do you wish to achieve?

Are you assuming that your USB dongle, currently using a Windows driver under Windows, has no Linux driver that will allow it to work with Ubuntu?  Could you provide us the specs of the USB dongle?  It is entirely possible that it will work with Linux.

It seems you may have some fundamental misconceptions about what Wine and VirtualBox are.

---

### Post by christaliise on 2016-06-03
After buying my new laptop at the beginning of May, I installed Ubuntu 16.04 because I was recommended by a PHP developer where he uses Wine & Virtualbox for various Windows applications such as Photoshop and Illustrator which he runs in Virtualbox 5.0, and I was under the impression that Ubuntu came with them already installed. When I found they were not installed I looked for remedies but found none. I then gave up on Ubuntu and searched the Internet to find a distro that has them installed. I tried SolydK and Debian and found they were dysfunctional and worse than Ubuntu. I've come back to Ubuntu with the thoughts of installing them in Windows, but if that can't be done, then the only option is to get Ubuntu with them already installed. If that is not possible then I will be abandoning Ubuntu forever. I have wasted over one month and achieved nothing, all in the belief that a Linux OS was superior.


If I plug the USB Stick into a Windows computer the console automatically installs. But nothing happened when I plugged the USB Stick into my new computer when Ubuntu was installed.


While connecting to the Internet is my primary goal, I do have a Windows based text editor that I'm addicted to, that I'd like to transfer to my new laptop. And there maybe other applications that will arise as time goes on, so I'm thinking it is best to have both Wine & Virtualbox installed at the outset.


Connecting to the Internet and a text editor are simple applications, whether based on Windows, Linux, Macintosh, or Solaris, so I expect Ubuntu to cater for those. If my expectations are too much then Ubuntu will not be suitable.


jim_deadlock - If Wine or Virtualbox wont allow the USB Stick to work, then what will?


QIII - I don't know where to find the specs. Yes, I may have misconceptions about what Wine and VirtualBox are.


I'm almost at the end of my patience. Nothing ever happened like this with my experience in Windows. I had no complaints with Windows XP. But I'm unsure of its current limitations.

---

### Post by jim_deadlock on 2016-06-03
If you can go to a friend's house and borrow a wired internet connection, that will allow you to easily install the default Ubuntu as you've done before. Once you've that and done the normal system updates there is a good chance that your USB will work and you can connect with that instead of the wired connection, You can then you can install Wine, Virtualbox etc.

> And there maybe other applications that will arise as time goes on, so  I'm thinking it is best to have both Wine & Virtualbox installed at  the outset.

It seems that you don't really want to let go of Windows. There are many (better) alternatives to Windows apps but if you are determined to stick with the Windows apps then you might as well stick with Windows as it will always run Windows apps better than Ubuntu.

---

### Post by QIII on 2016-06-03
Wine may not run everything you would like, but it might run what you want.  If you use VirtualBox, you need to install a Windows virtual machine, which will allow you to run whatever Windows software you want natively in Windows.  Those can both be easily installed if we can get you an internet connection.

If you run a Live Ubuntu session, does the dongle work?  If not, can you use an ethernet connection in the interim while we work on this?  

If you can do either of those, there is a script you can run that will tell us most everything we need to know about the wireless USB dongle.

For now, can you tell us the manufacturer and model?

The reason this hasn't happened to you in Windows is that the manufacturer of your dongle made darn sure they had a driver that worked with Windows -- if they hadn't they would have gone broke.  Microsoft does not write those drivers.  The OEMs do.  If they meet Microsoft's standards, they can be included in the DriverBase and the hardware is Plug 'N Play or the driver installs automatically. 

If the hardware doesn't work in Linux because there is no driver for it, it is no fault of the Linux community.

---

### Post by christaliise on 2016-06-04
Thanks howefield, initially I brushed aside your comment "Zorin OS comes with Wine and Play on Linux preinstalled, or at least it used to." as I thought it would be the same as the others I've tried but out of desperation I investigated Zorin at [http://zorinos.com/](http://zorinos.com/) and for the sake of other viewers with the same circumstances I've included Zorin's features;


Multi-functional - Zorin OS is a multi-functionaloperating system designed specifically for newcomers to Linux. It's based on Ubuntu Linux, so you can rely on it for rock-solid performance, dependability and support.


Exclusive Software - Zorin OS features our uniqueLook Changer program that we have created exclusively for Zorin OS. It allows you to change the user interface at the touch of a button. Other unique programs include Background Plus, Web Browser Manager and more.


Flexibility - Zorin OS gives you more flexibility. It allows you to use Zorin OS alongside your current operating system and run Microsoft Windows programs in Zorin OS with the help of WINE and PlayOnLinux.


Super secure - Thanks to Zorin OS's immunity to Windows viruses you will never have to worry about any of that nasty malware. And when a potential security threat arises, software updates usually come in a matter of hours. With Zorin OS you are sure to have peace of mind.


Much faster than your typical OS - Zorin OS is super fast. Zorin OS is faster than Windows and OS X because it is more lightweight. Some Windows programs run even faster in Zorin OS with WINE (which comes pre-installed with Zorin OS) than in Windows.


Out-of-the-box software - Zorin OS is packed with all the software you'll ever need out of the box, from office suites to video editors.


Zorin Look Changer - The Look Changer lets you change your desktop to look and act like either Windows 7, XP, 2000, Ubuntu Unity, Mac OS X or GNOME 2 for ultimate ease of use.


Zorin Web Browser Manager - We have included our exclusive program called the Web Browser Manager which makes it easy to install or uninstall alternate web browsers.


Zorin Background Plus - Background Plus allows you to set a video, audio file or screensaver as your background to enhance your desktop experience.

---

### Post by christaliise on 2016-06-04
I'm not in my native country, as I moved to build a website, but I could not have chosen a worse environment to get a job done. I'm in a Windows orientated environment, even buying a laptop without Windows was a mission.

The Internet connections here are a nightmare. No nothing happened when I plugged the USB dongle into my new computer when Ubuntu was installed. I'm not aware of any ethernet connections here.

I was given the USB dongle when I arrived here, and it is marked with the ISP's name and I think it was part of the ISP's package. The drivers would have been written from the ISP's instructions. Of course they would have gone broke because the majority of the population here are only familiar with Windows. One good thing about the ISP I'm using is that it requires no registration, anybody can use it. Other ISPs require only native users to register.

I intend moving out of this country as soon as my circumstances permit, but as yet I have no preferred option.


Zorin appears my god sent. I'll download it tonight.

---

### Post by howefield on 2016-06-04
> **christaliise said:**
> Thanks howefield, initially I brushed aside your comment "Zorin OS comes with Wine and Play on Linux preinstalled, or at least it used to." as I thought it would be the same as the others I've tried but out of desperation I investigated Zorin at [http://zorinos.com/](http://zorinos.com/)....

If you go with Zorin just watch out for the length of the support period. 

Also upgrading to the next version requires a clean install of the next version. This may not be an issue for you but you might want to be aware. Also they have their own [support forums]("http://zoringroup.com/forum/viewforum.php?f=3").

---

### Post by christaliise on 2016-06-04
> **jim_deadlock said:**
> If you can go to a friend's house and borrow a wired internet connection, that will allow you to easily install the default Ubuntu as you've done before. Once you've that and done the normal system updates there is a good chance that your USB will work and you can connect with that instead of the wired connection, You can then you can install Wine, Virtualbox etc.



It seems that you don't really want to let go of Windows. There are many (better) alternatives to Windows apps but if you are determined to stick with the Windows apps then you might as well stick with Windows as it will always run Windows apps better than Ubuntu.

I'm not in my native country, as I moved to build a website, but I could not have chosen a worse environment to get a job done. I'm in a Windows orientated environment, even buying a laptop without Windows was a mission. I do not like Windows 7 and 10 primarily because they are too slow, and secondly complicated. The Internet connections here are also a nightmare. My mission is to build a website that is simple, uncomplicated and everyone feels comfortable using it. Zorin appears my god sent.

---

### Post by christaliise on 2016-06-04
> **howefield said:**
> If you go with Zorin just watch out for the length of the support period. 

Also upgrading to the next version requires a clean install of the next version. This may not be an issue for you but you might want to be aware. Also they have their own [support forums]("http://zoringroup.com/forum/viewforum.php?f=3").


Yes, it appears the free version Zorin OS 9 has support until April 2019 and the paid version Zorin OS 11 has support until (next month) July 2016.


My mission is to be in a simple environment, so it appears as if Zorin OS 9 will suit best. I'll down load it tonight. Lets hope it functions unlike SolydK & Debian (to be fair the malfunctions maybe caused by my system).

---

