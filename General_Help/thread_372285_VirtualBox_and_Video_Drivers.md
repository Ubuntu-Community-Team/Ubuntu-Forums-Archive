---
title: "VirtualBox and Video Drivers"
date: 2007-02-28
forum: General Help
---

### Post by kodoku on 2007-02-28
Hello all,

For those who use VirtualBox, I have a few questions.  I currently virtualized Windows XP while running edgy, as as far as I'm concerned, its freaking amazing.  However, I do have a few small issues that I hope someone can help with.  Now before I'm slaughtered for not looking for support at VB's website, I did try and post on their forum and inquire in their IRC channel. Unfortunately it seems a bit deserted over there.

Just for fun, I tried installing Starcraft in the virtualized XP, and it runs beautifully.  However, after poking around with VB, I found the Guest Additions, and installed them.  Cool.  Even more functionality!  However, then I realized that the video drivers that came with it can only support down to 16-bit color.  (But I need 8-bit for starcraft!)  Is there anyway to have the additions installed yet tweak it to support 8-bit (256 colors in other words)?

Also, does anyone have stability issues with VB, for instance, seemingly random aborts.  I thought VB was just unstable at first because after running the os for about 10 minutes (especially watching videos) or so, the thing would just abruptly abort.  I blamed the culprit on beryl, which when shut off, VB doesn't crash.  I hope this solves the issue once and for all *crosses fingers*.  Does anyone have similiar issues?

PC Specs:
P4 HT 2.4 Ghz
1.5 Gb RAM
nVidia GeF 6200 256 mb
160 Gb HD

---

### Post by Jamin3D on 2007-03-14
I ended up removing the VirtualBox display driver and going w/ the driver it initially installs in order to get Age of Empires working again (the Guest Addition video driver caused DirectDraw to stop working or something).

Did you try XP's compat mode? (right click on the game's icon, Properties, Compatibility, then choose 256 color mode)

---

### Post by zvezdafolk on 2007-03-18
I got the same problem : I am unable to run starcraft with broodwar extension in virtualbox...

> Did you try XP's compat mode? (right click on the game's icon, Properties, Compatibility, then choose 256 color mode)
That didn't work.

---

### Post by michwill on 2007-05-25
Has anyone made any progress on this front?

---

### Post by bodhi.zazen on 2007-05-29
Yes. First install the so called addons (Install the addons on the guest OS NOT THE HOST).

Then in a terminal :

```
VBoxManage controlvm "Guest" setvideomodehint "1440" "900" "24"
```


Where :

[list][*]"Guest" is the name of the Guest OS.
[*]"1440" and "900" are the desired resolution.
[*]"24" is the desired color depth (8,16,24)[/list]

For further information : [http://doc.gwos.org/index.php/VirtualBox](http://doc.gwos.org/index.php/VirtualBox)

---

### Post by 043087m135 on 2007-08-08
So everybody knows, the Virtualbox video driver is completely incapable of providing anything less than 16 bit color. Here's a link from the virtualbox team itself.

[http://www.virtualbox.org/ticket/196](http://www.virtualbox.org/ticket/196)

I'll paste it here too for reference, in case they remove the ticket location.
******************************************************
Ticket #196 (closed enhancement: wontfix)

Opened 5 months ago

Last modified 5 months ago
Guest Additions Video Driver
Reported by: 	kodoku 	Assigned to: 	
Priority: 	major 	Version: 	VirtualBox 1.3.6
Keywords: 	video driver, guest additions 	Cc: 	
Description ¶

Having the Guest Additions Video Driver provides MUCH greater stability to the VM. However, the Additions drivers do not support 256 color support (8bit). It is capable of 16 colors, 16, 24 and 32bit. Many applications (some older games for instance) still require 256 color mode. If the driver is installed, using the XP Compatibility mode is useless, becase 256 colors isn't even listed as an option. A solution is to uninstall the Addition drivers and use XP's generic video drivers. However, I have found that using the generic driver causes much too many memory corruption errors that will abort VirtualBox repeatedly. It would be great if I can have the Guest Additions installed AND have 256 color support. Thank you!
Change History
03/15/07 10:20:14 changed by michael ¶

    * status changed from new to closed.
    * resolution set to wontfix.

I'm afraid that we won't be able to add a 256 colour mode to the additions in the foreseeable future (the usual problem - no paying customers interested in it). You might want to look into doing it yourself (the driver code is in src/VBox/Additions/WINNT/Graphics; it shouldn't be too much work to extend the existing code), or alternatively to look for someone in the community who would be interested in doing it.

By the way, you are welcome to open a separate ticket concerning the memory corruption you mentioned (also specify which host, which version of XP as guest and whether it is VirtualBox or the XP guest which crashes).
******************************************************

SO BASICALLY, In order to run programs that require 256 mode, you must use windows' default VGA video drivers, which suck and only provide 1024 resolution. But that's how it is - for now - until somebody out there programs a more fully functional driver for VirtualBox, since they're not going to unless some corporation suddenly has the distinct need to install starcraft on all their employee's virtual machines. Anybody got a corporate uncle who'll write a letter? (:

Peace.

~043087m135

---

### Post by UK-Wobbie on 2007-08-08
> **kodoku said:**
> Hello all,

For those who use VirtualBox, I have a few questions.  I currently virtualized Windows XP while running edgy, as as far as I'm concerned, its freaking amazing.  However, I do have a few small issues that I hope someone can help with.  Now before I'm slaughtered for not looking for support at VB's website, I did try and post on their forum and inquire in their IRC channel. Unfortunately it seems a bit deserted over there.

Just for fun, I tried installing Starcraft in the virtualized XP, and it runs beautifully.  However, after poking around with VB, I found the Guest Additions, and installed them.  Cool.  Even more functionality!  However, then I realized that the video drivers that came with it can only support down to 16-bit color.  (But I need 8-bit for starcraft!)  Is there anyway to have the additions installed yet tweak it to support 8-bit (256 colors in other words)?

Also, does anyone have stability issues with VB, for instance, seemingly random aborts.  I thought VB was just unstable at first because after running the os for about 10 minutes (especially watching videos) or so, the thing would just abruptly abort.  I blamed the culprit on beryl, which when shut off, VB doesn't crash.  I hope this solves the issue once and for all *crosses fingers*.  Does anyone have similiar issues?

PC Specs:
P4 HT 2.4 Ghz
1.5 Gb RAM
nVidia GeF 6200 256 mb
160 Gb HD


I had windows xp working on vbox on ubuntu :) It worked ok but the screen size was a bit out of the vbox window!

---

### Post by hoctro on 2008-05-06
Starcraft works fine with new virtualbox 1.6

---

### Post by deltaprime on 2008-05-21
thanks [[COLOR=#D40000]**bodhi.zazen**[/COLOR]]("http://ubuntuforums.org/member.php?u=89054") that helped!

;)

just made some :popcorn: for the videos im going to watch now in my vbox just for the hack of it cause the res fits now haha

that:guitar:

---

