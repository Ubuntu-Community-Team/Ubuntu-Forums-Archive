---
title: "Migrated to Linux (Ubuntu).. Need help"
date: 2012-10-15
forum: General Help
---

### Post by Hoffadder on 2012-10-15
Hi there,

I have recently left Microsoft behind after the umpteenth system failure, and am committed to making a full transition to Linux.
I chose Ubuntu 12.04.01 64 bit, as my assumption was that Ubuntu would have the best support for hardware, and I also was impressed by its ease of use compared to other distro's software managers.

Everything installed fine, and I thought all was well.

But:
1. When surfing on Chrome, there are several webpages that do not function properly and seem broken (scroll bars do not work, cannot fill in forms etc.) and there are glitches while watching Youtube.

2. At the same time when watching a high-def movie with VLC, after 30 minutes (aprox) the sync goes to hell.

3. I have at the same tame noticed that the CPU load is very erratic never falling bellow 14% and spiking intermittently at 76-100%.

I have installed restricted drivers, and tried both installing catalyst from AMD's webpage and tried the propitiatory drivers in Ubuntu's "additional drivers" menu, but alas nothing is helping.

Can anyone guide me in the right direction?
I consider myself semi-computer literate, and can usually find sollutions online my self, but not this time.  
Is this a Kernel issue? 
Would I have better luck waiting for 12.10 (newer kernel)
Should I consider a different distro?

My specs are:
Intel I5 275 on MSI P55-CD53 motherboard
ATI HD 4890 1GB
60 GB SSD, 1TB WD caviar for /home folder
16 GB Corsair Vengeance (because I could :) )

Thanks in advance

P.s.

If this is a GPU issue, what are my options? As far as I can make out there might be support problems for the HD 4xxx series in linux. Does this mean I have to buy a new GPU :(

---

### Post by Ace..... on 2012-10-15
The likely fix for your issues with chrome can be found here:

[http://ubuntuforums.org/showthread.php?t=2065621](http://ubuntuforums.org/showthread.php?t=2065621)

:p

---

### Post by Hoffadder on 2012-10-15
Thx for the heads up Ace.

I will give it a try.

In the mean time I have read that flash hasn't been very well supported on 64 bit.  I never had problems using FF or Chrome in Windows, so I assume this as well is a Linux issue.

I chose Chrome over Firefox due to Adobe not supporting Linux any longer.  But is this still the case?

---

### Post by Ace..... on 2012-10-15
> **Hoffadder said:**
> Thx for the heads up Ace.

I will give it a try.

In the mean time I have read that flash hasn't been very well supported on 64 bit.  I never had problems using FF or Chrome in Windows, so I assume this as well is a Linux issue.

I chose Chrome over Firefox due to Adobe not supporting Linux any longer.  But is this still the case?

Not sure of the politics, but I run chrome and firefox as my normal setup.

For firefox, I installed flash-aid - its a an icon that will live top-right of firefox.
It will load the correct code for your sys.

It works a treat.

By using both these fixes, both my browsers are flying along.
Chrome flies just that little bit faster (as it happens). :wink:

---

### Post by Pilot6 on 2012-10-15
Regarding browsing in Chrome.
Install flashplugin-installer package.
Then in Chrome goto chrome://plugins, click details in the right corner and disable pepperflash.
Pepperflash which is built in Chrome does not work well with AMD graghics.

Adobe does not make new versions of flash for linux, but they issue security updates for 11.2. It works quite well.

---

### Post by Pilot6 on 2012-10-15
Regarding high cpu loads when playing video install xvba-va-driver.

---

### Post by jerrrys on 2012-10-15
Have you installed URE?

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by Hoffadder on 2012-10-15
Hi all, and thanks to everyone that has replied.

I have installed URE and the XVBA-VA-driver.

I went into Chrome, but could not see pepperflash anywhere.
What I have is:

Flash (2 files) - Version: 11.4.31.110
Shockwave Flash 11.4 r31
Name:	Shockwave Flash
Description:	Shockwave Flash 11.4 r31
Version:	11.4.31.110
Location:	/opt/google/chrome/PepperFlash/libpepflashplayer.so
Type:	PPAPI (out-of-process)
 	 Disable
MIME types:	
MIME type	Description	File extensions
application/x-shockwave-flash	Shockwave Flash	
.swf
application/futuresplash	FutureSplash Player	
.spl
Name:	Shockwave Flash
Version:	11.2 r202
Location:	/usr/lib/flashplugin-installer/libflashplayer.so
Type:	NPAPI
 	 Disable
MIME types:	
MIME type	Description	File extensions
application/x-shockwave-flash	Shockwave Flash	
.swf
application/futuresplash	FutureSplash Player	
.spl

Still the same problem on say Facebook.  Nothing works.

There must be a way, but until I can find a fix I will have to start using Firefox (which was my preferred browser until I was persuaded to try Chrome).

The next experiment wil be to see how the GPU is faring.  I was thinking of installing Playonlinux and trying to install some of my Windows games (Skyrim?), or should I try a native game.  I just want to pressure test the system.

I will try to watch a HD-movie to see if there are still any glitches.

---

### Post by Ace..... on 2012-10-15
RE pepper flash

I had the same prob as you..... unable to find it.
Hence why I figured out the fix that I first posted to you.

It might not be elegant..... but it definitely worked/works and it solved all the display problems I had in chrome, and dramatically speeded it up. ;)

---

### Post by Hoffadder on 2012-10-15
@Ace:  It worked!

Thanks a lot.  I presume that I will have to launch Chrome from the Desktop from now on, but that is a minor inconvenience.

---

### Post by Ace..... on 2012-10-15
> **Hoffadder said:**
> @Ace:  It worked!

Thanks a lot.  I presume that I will have to launch Chrome from the Desktop from now on, but that is a minor inconvenience.

No.

Re-read the fix.

You drag the chrome icon to the launch bar, and it just slots in.
Then Rclick and Lock.

Your desktop icon stays on the desktop, but you also have it in your launch bar.

Perfect - and thanks for confirming that it worked :)

---

