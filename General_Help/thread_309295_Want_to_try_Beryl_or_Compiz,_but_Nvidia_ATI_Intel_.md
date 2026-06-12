---
title: "Want to try Beryl or Compiz, but Nvidia? ATI? Intel? how can I know?"
date: 2006-11-29
forum: General Help
---

### Post by shane2peru on 2006-11-29
Ok, I have wanted to try Beryl, or Compiz, but all the how to's specify for Nvidia, or ATI or Intel, or something else.  How can you tell what you need?  I don't want to follow the ATI directions if I don't have ATI, and I don't want to follow the Nvidia instructions if I don't have Nvidia, and if I don 't have either what do I do?  
I have a Toshiba Satellite MX35 laptop.  Is there a command I can run in a terminal to determine what type of display I have?  Thanks.

Shane

---

### Post by Rodneyck on 2006-11-29
Hi there,

I know there is a command to use in the Terminal that will tell you what video card you have and what drivers, but I can not find it at the moment, so do a search or maybe someone else knows.

I do want to say that I have installed beryl on my computer a couple of days ago and love it. I believe there is no more Compiz, it actually morphed into Beryl, but I could be wrong here, not exactly sure on the development paths.  A couple of things you should know though before taking the plunge. 1. back up your system files in the event something goes wrong. 2. I have used a couple of "install guides" but found that many were out of date or some of the repo links were no longer valid, which can cause some problems and headaches during the installation process.

This guide is the one I used and it worked. You do need to know what video card you have though.  Start under section 1.8... Good luck.

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Beryl.2FAIGLX_.28Nvidia.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Beryl.2FAIGLX_.28Nvidia.29)

---

### Post by bazerk on 2006-11-29
I'm 99% sure it'll be intel, I have a satellite also (slightly different model). Beryl (+compiz) is great although I'd suggest upgrading to edgy as it has aiglx built in (what beryl runs on). I'm unsure of the command to show the hardware although I know there is one, I'll keep a look out untill someone lets us know.good luck.

---

### Post by shane2peru on 2006-11-29
Thanks guys, I think it is Intel now that you say that, I think I seen it in some linux distro setup.  I don't remember though.  Oh, I guess I should update my thing on the side as I'm using Edgy now.

Shane

---

### Post by Ramses de Norre on 2006-11-29
```
lspci
```
and look for the VGA compatible controller and Display controller.

---

### Post by shane2peru on 2006-11-29
> **Ramses de Norre said:**
> ```
lspci
```and look for the VGA compatible controller and Display controller.
Hey Thanks Ramses de Norre!

```
shane@shane-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
[COLOR=Red]00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)[/COLOR]
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)

``` That would be my relevant one, meaning my computer is of the Intel family.  Thanks.

Shane

---

### Post by shane2peru on 2006-11-29
> **Rodneyck said:**
> Hi there,

I know there is a command to use in the Terminal that will tell you what video card you have and what drivers, but I can not find it at the moment, so do a search or maybe someone else knows.

I do want to say that I have installed beryl on my computer a couple of days ago and love it. I believe there is no more Compiz, it actually morphed into Beryl, but I could be wrong here, not exactly sure on the development paths.  A couple of things you should know though before taking the plunge. 1. back up your system files in the event something goes wrong. 2. I have used a couple of "install guides" but found that many were out of date or some of the repo links were no longer valid, which can cause some problems and headaches during the installation process.

This guide is the one I used and it worked. You do need to know what video card you have though.  Start under section 1.8... Good luck.

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Beryl.2FAIGLX_.28Nvidia.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Beryl.2FAIGLX_.28Nvidia.29)


I assume in this guide I would follow the intel 915 directions?
> 
** How to install Beryl/AIGLX (Intel i915) **

Edit:  I just realized that post send me [here.]("http://wiki.beryl-project.org/index.php?title=Install/Ubuntu")

Of which I still have choices.  
> 
** Ubuntu 6.10 (Edgy Eft) **

 [LIST]
[*] [Graphic Card Drivers]("http://wiki.beryl-project.org/index.php?title=Install/Ubuntu/Edgy/GCDrivers")[/LIST] [LIST]
[*] [XGL]("http://wiki.beryl-project.org/index.php?title=Install/Ubuntu/Edgy/XGL")
[*] [AiGLX]("http://wiki.beryl-project.org/index.php?title=Install/Ubuntu/Edgy/AiGLX")
[*] [nVIDIA beta drivers]("http://wiki.beryl-project.org/index.php?title=Install/Ubuntu/Edgy/nVIDIA") (runs directly on inbuilt AiGLX)
[*] Installing latest svn snapshots from repository[/LIST]Do I want XGL, or AiGLX?  What is the difference?
Thanks!

Shane

---

### Post by PriceChild on 2006-11-29
AIGLX with intel :)

Faster and better in every way...

---

### Post by Rodneyck on 2006-11-29
My best guest is to go with Aiglx. It works the best according to many on this forum and for me as well, it is what I chose, less buggy, fast, etc.  Edgy Eft already has it built in so you just need to add the repos and install Beryl, as the link suggests.

Edit to add this link:

[http://en.wikipedia.org/wiki/AIGLX](http://en.wikipedia.org/wiki/AIGLX)

---

### Post by shane2peru on 2006-11-29
Great, thanks guys!  I will have to give this a try later this evening!

Shane

---

### Post by steevk on 2006-11-29
Basically, XGL is a re-write of X.org with the new stuff thrown in, AIGLX is X.org with that stuff added to it.

There isn't that big of a difference from the user's perspective. Maybe one or the other works better...

---

### Post by Rodneyck on 2006-11-29
Here is the beryl forum with lots of great help and info..

[http://forum.beryl-project.org/index.php](http://forum.beryl-project.org/index.php)

..and here is a repository with more beryl add-on plugins.. 

[http://3v1n0.tuxfamily.org/dists/edgy/beryl-svn/](http://3v1n0.tuxfamily.org/dists/edgy/beryl-svn/)

---

### Post by shane2peru on 2006-11-29
Ok, I gave Beryl a try, and really it looks neat, but, it is too - slow, unstable, risky.  I couldn't boot into it, when I tried to restart.  It worked really well, and was really neat looking, but I need to work on this computer.  It also made my computer run much like windows does - slow.  I read that there was a setting to change about the blur, but I couldn't find it.  I will keep it installed and use it every now and then, but no startups for me, not for now.  Thanks for the help!  The install easy, and it runs fine, needs work on the startup issues it has though.  That is my $.02 worth.

Shane

---

### Post by strabes on 2006-11-29
i hope you set up a separate session for AIGLX.

---

### Post by shane2peru on 2006-11-30
Yes, I setup a separate session, that is the best way to do it so that you can log into a normal Gnome session if that fails - which it did.  

Shane

---

### Post by Rodneyck on 2006-11-30
Just checking, but you said it was slow and unstable.  Did you update your nvidia drivers from the link on the beryl guide, or did you use some other how-to guide?  I recommend the one on that guide. It sounds like it might be a video card driver problem, like the wrong one installed.  It is very smooth and fast on my computer, then again, not sure of your specs.

---

### Post by shane2peru on 2006-11-30
I guess slow is relative.  I followed the guide that you had posted > This guide is the one I used and it worked. You do need to know what video card you have though. Start under section 1.8... Good luck.

[http://ubuntuguide.org/wiki/Ubuntu_E....28Nvidia  .29]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Beryl.2FAIGLX_.28Nvidia.29") - it lead me to another place, and I followed that guide.  I don't have Nvidia, I have Intel, so I followed the link that was there for the Intel, and then installed the AiGXl one.  Maybe unstable was too strong, and by slow, I mean it seemed to make ordinary tasks take longer.  One I really noticed was when I clicked on **Places - Home**  it took a little bit (may 5 - 10 sec) for Nautilus to open.  That is how Windows XP runs on my computer, and consequently one of the reasons I use Ubuntu Gnome, it is slick and fast.  I tried FC6, but it wasn't as fast as Ubuntu.  Perhaps I'm just impatient.  Oh, I also didn't like what it did to my adesklets - that was another minor negative, it turned them into ugly black boxes on my desktop - not very impressive.  I don't need the fancy desktop switching, and wiggly windows etc, it does look nice, and is cool, but I don't feel like configuring any more.  I have configured, tweaked, and am content with my desktop.  If it 'just' worked without configuration, I may be interested.  Thank you for the help, I do have it installed, and can show it off, but it isn't for me for daily use.

Shane

---

### Post by PriceChild on 2006-12-01
Yeah beryl does make things run a little slow.

I've been building beryl from svn lately (NOT reccomended) and the speed increase is incredible!

Just wait for 0.1.3 and hope it stays like this :)

---

### Post by Rodneyck on 2006-12-01
Here is another option. There is a program called reconstructor that anyone can use to make your own install disk from Ubuntu. For example, graphics people can make a graphics ubuntu that loads with all the needed graphic progams already installed. 

Someone has made a Beryl Ubuntu that installs with beryl installed. You just click on the icon on the desktop to start it up. Of course, you have to do a complete install, but an option if you want to take it for a test drive and can't get it going yourself.

[http://www.ubuntuforums.org/showthread.php?t=309704](http://www.ubuntuforums.org/showthread.php?t=309704)

---

