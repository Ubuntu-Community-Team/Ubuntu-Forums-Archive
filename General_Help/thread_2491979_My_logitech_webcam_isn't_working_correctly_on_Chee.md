---
title: "My logitech webcam isn't working correctly on Cheese"
date: 2023-10-26
forum: General Help
---

### Post by SpaceManJack on 2023-10-26
So yeah I've got the HD 1080p Logitech webcam but it's currently not working right on Cheese and it's my only webcam so I'm not sure if it's Cheese or the webcam. I think it's Cheese to be honest though, in fact I'd even say I think it's Linux because I had used Windows for over 20 years and my Logitech webcams always worked flawlessly on Windows. Also don't forget Logitech has their own first party software you're supposed to use with your Logitech camera but guess what, Logitech doesn't support Linux so their software isn't available on Linux.

Now I need to be honest here, my Logitech webcam didn't act properly on Cheese back on Ubuntu 20.04 either! I'm telling you it's not Ubuntu's fault it's Linux, Linux is the problem! So I've only been using Linux for a couple of years now but my Logitech webcams always performed flawlessly on Windows, and of course, Logitech doesn't even support Linux so you can't use Logitech's software on Linux. I used to always use the Logitech software on Windows. But I switched over to Linux so I don't even own a Windows machine anymore.

So yeah I don't think Cheese is to blame, I think Linux is to blame. 

Btw was Cheese last updated 3 years ago? 

I also downloaded the Camera app from the Ubuntu store and my webcam works good but the picture quality isn't perfect, it's funny, the picture quality is better in Cheese but here's what's happening, the video will play for a second and then keep looping itself over and over again so I'll just see the same 1 second recording over and over again, this is what's happening in Cheese, but the picture quality is much better in Cheese than the Camera app with the same webcam, go figure.

I've been thinking about reaching out to Logitech and telling them that they should support Linux cause this is ********, why would they make their first part software only available for Windows and Mac (and I think they even support Chrome too, you know those Chrome books) but they do not support Linux. So yeah I'll probably eventually send an email to Logitech telling them they need to support Linux. Hell even Google makes sure Google Chrome browser is supported on Linux but Logitech won't even bother.

So, yeah Cheese didn't even work right with my HD 1080p Logitech webcam back on Ubuntu 20.04 and it's still not working right on 22.04. And I've only been on Linux now for a couple of years, I was a lifelong Windows user prior to switching to Linux.

So what can I do to fix this?

---

### Post by dragonfly41 on 2023-10-26
I'm interested in this topic since I was thinking of buying a Logitech webcam to complement my Logitech keyboard and mouse.

Found this ..

[https://www.systranbox.com/how-to-install-logitech-webcam-linux-commandline/](https://www.systranbox.com/how-to-install-logitech-webcam-linux-commandline/)

There is a Linux driver .. somewhere.  I connect to Logitech (and other) devices using Bluetooth Manager.
I'll hand back on ordering until I see how your case develops.

---

### Post by Holger_Gehrke on 2023-10-26
Webcams are very much standardized, they are part of the USB Video Class (UVC) which doesn't cover just webcams but basically anything which transfers streams of video data to the computer via USB. You don't need a driver from the manufacturer for an UVC compliant webcam. Even on Windows webcams have been plug-and-play without driver installation since the Windows XP days. So if Logitech's cameras are UVC compatible - and AFAIK they are, except for some early ones which have some quirks - the driver included in the kernel should work just fine unless the camera follows a newer version of the UVC specification than the driver. The last version of the specification (1.5, adds h264 and vp8 as codecs for transfer and mentions USB 3) is from 2012 and is supported by both Windows and Linux.

Both the 'Camera'-app and 'Cheese' are written for Gnome, and Gnome is kind of known for making programmers write programs at a very high level of abstraction and force the use of several layers of libraries. You might get better results with 'guvcview'.

And no, Cheese had updates. The version in the repositories is Cheese 41 (which dates from November 2021, so a bit less than two years) and it is currently available in source code from gnome.org in version 44 (dated July of this year).

Holger

---

### Post by MAFoElffen on 2023-10-26
+1 with trying 'guvcview'. I have had very good luck with that and it has lots of adjustments to it.

---

### Post by SpaceManJack on 2023-10-26
> **Holger_Gehrke said:**
>  You might get better results with 'guvcview'.

And no, Cheese had updates. The version in the repositories is Cheese 41 (which dates from November 2021, so a bit less than two years) and it is currently available in source code from gnome.org in version 44 (dated July of this year).

Holger

What is 'guvcview'? 

Well it says in the Ubuntu store that Cheese was last updated 3 years ago. Cheese automatically updates itself right?

---

### Post by SpaceManJack on 2023-10-26
> **MAFoElffen said:**
> +1 with trying 'guvcview'. I have had very good luck with that and it has lots of adjustments to it.

So is it in the ubuntu store or?

---

### Post by dragonfly41 on 2023-10-27
guvcview was mentioned at the bottom of the blog link I posted. Last  paragraph.
I opened Synaptic, searched for guvcview and there it is in repo.
guvcview
GTK+ base UVC Viewer
Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>

Reading the blog last paragraph .
&#8220;Linux and other distributions like Ubuntu work well with the Logitech BRIO Ultra HD Webcam&#8221;.
I will follow advice and now purchase that webcam.

---

### Post by Holger_Gehrke on 2023-10-27
Yes, guvcview is in the Ubuntu store. It's actually in there twice, once the official Ubuntu release in the repositories and a slightly newer unofficial release as a snap. The same is true of Cheese, there's a newer Cheese (V 44.1) available as a snap. 

Normal packages stay at the released version for the whole length of the life time of an Ubuntu release. So if Cheese was released in the repositories as version 41 then that's the version it will stay at and you'll only get updates if there's a fix for a security problem or a crash and these updates will only fix the problems and not add features (basically they take the source code of the old version and put in the fix(es) for any discovered problem(s)). If you want a newer version of a program, then you need a newer version of Ubuntu.

snaps on the other hand are handled differently. Anybody can make a snap and put it in the store. That's why the format includes quite a few safety measures to protect the system (but not your data) from buggy or malicious snaps. The general dislike for snap stems from several factors:
[LIST]
[*]the safety measures are strong enough to be a real nuisance but not strong enough to be an actual protection.
[*]updates to snap packages are very hard to control. There are some ways to control them to restrict snap from starting an update at an inconvenient time, but in general the idea is to update as soon and as often as possible and the controls are only accessible through the command line.
[*]snaps are bigger then normal packages since they include all the dependencies for each program.
[*]snaps are slow to start the first time they are run in a session because they are compressed and need to be decompressed in memory to be used.
[/LIST]

Holger

---

### Post by ActionParsnip on 2023-10-27
Do you have a full model of the Logitech? They make a wide range of webcams. Simply saying its 1080p doesn't really tell us much

---

### Post by Autodave on 2023-10-27
I have 3 different Logitech web cams here.......and they all work on Cheese.  They always have.  I run Ubuntu, Xubuntu, and Mint.  And they all work.

---

### Post by SpaceManJack on 2023-10-29
> **Autodave said:**
> I have 3 different Logitech web cams here.......and they all work on Cheese.  They always have.  I run Ubuntu, Xubuntu, and Mint.  And they all work.

If I may ask how old is your PC?

My PC was built in 2015, it's got 16 gigs of ram, and mid range AMD CPU and GPU. I just downloaded guvcview from the Ubuntu store and if I select full 1080p resolution it works but it's slow, I think maybe it's cause my PC is old, I bet if I had a more modern PC I probably wouldn't have these problems.

And of course one needs to remember that everything we use was designed for Windows not Linux. Everything was optimized to work for WIndows, and indeed I never had any problems with my Logitech webcams on Windows.

Maybe I should think about buying a new PC.

So yeah how old is your PC?

---

### Post by SpaceManJack on 2023-10-31
> **Autodave said:**
> I have 3 different Logitech web cams here.......and they all work on Cheese.  They always have.  I run Ubuntu, Xubuntu, and Mint.  And they all work.

You there?

---

### Post by SpaceManJack on 2023-11-02
My PC was built in 2015 so next year my PC will be 9 years old, so my PC is kind of old, do you think that's why I'm having issues with my webcam? My webcam was bought just a couple of years ago off of Amazon, it's a 1080p webcam.

---

### Post by dragonfly41 on 2023-11-02
I have just received today a Logitech Brio.

But I have just learned this from Logitech site

*Make sure your BRIO 505 is connected directly into your computer's USB-C port or an adapter with a USB-C port **that supports both power AND video**. Some adapters only support power, in which case your webcam will not appear.*

I tried a powered USB expander (presumably not video)  but I guess I will now have to find an appropriate direct port not on the StarTech USB port expander but near the Dell 3268 Tower motherboard.

---

### Post by dragonfly41 on 2023-11-05
Conclusion: My newly purchased Logitech BRIO works in Windows 10 but not in Ubuntu 20.04.

Tried Cheese guvcview and also building camorama.

The workaround might be running on Windows VM.

No native Ubuntu 20.04 solutions found, even though the device is seen in lsusb.

lsusb | grep BRIO
Bus 002 Device 002: ID 046d:085e Logitech, Inc. Logitech **[COLOR=#ff5454]BRIO[/COLOR]**

v4l2-ctl --device=/dev/video0 --all
Cannot open device /dev/video0, exiting.


Guvcview error 
no video device found

---

### Post by ActionParsnip on 2023-11-05
> **dragonfly41 said:**
> Conclusion: My newly purchased Logitech BRIO works in Windows 10 but not in Ubuntu 20.04.

Tried Cheese guvcview and also building camorama.

The workaround might be running on Windows VM.

No native Ubuntu 20.04 solutions found, even though the device is seen in lsusb.

lsusb | grep BRIO
Bus 002 Device 002: ID 046d:085e Logitech, Inc. Logitech **[COLOR=#ff5454]BRIO[/COLOR]**

v4l2-ctl --device=/dev/video0 --all
Cannot open device /dev/video0, exiting.


Guvcview error 
no video device found

Installing lots of appreciations that access a webcam won't make it magically work. It's like installing Call Of Duty thinking it'll install your Nvidia drivers, in Windows or. Installing Adobe Audition thinking it'll make your sound card jump into life.

---

### Post by dragonfly41 on 2023-11-05
> [COLOR=#000000]Installing lots of appreciations that access a webcam won't make it magically work.
Accepted. But have to experiment. Windows wins the day.

[/COLOR]

---

### Post by iamjiwjr on 2023-11-05
I have best results by replacing cheese with webcamoid.

---

### Post by dragonfly41 on 2023-11-05
Thanks for the tip. It looks very comprehensive. Sadly BRIO still not detected. There must be some generic problem. Works on Windows 10 but, on same port, not my Ubuntu 20.04. I will have to use Windows for webcam session.

---

### Post by SpaceManJack on 2023-12-06
> **dragonfly41 said:**
> Thanks for the tip. It looks very comprehensive. Sadly BRIO still not detected. There must be some generic problem. Works on Windows 10 but, on same port, not my Ubuntu 20.04. I will have to use Windows for webcam session.

How old is your PC build? 

Yeah everything has been designed to run on either windows or mac. Logitech doesn't even provide their first party software for Linux, that shows you right there they don't care about Linux at all. Will you please buy a Logitech 1080p webcam and see how that works with your Linux PC?

My PC build is from 2015 so it's getting old now. I'm thinking that maybe the reason my Logitech 1080p webcam doesn't work well is maybe because my PC is old. All I know is it worked flawlessly on Windows but that's because everything has been designed for Windows and not Linux. 

But then again you've got people here saying that their webcam works good on Linux.

Can I get some help here please?

---

