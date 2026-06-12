---
title: "Ubuntu 16.04 -- &quot;Fatal error: No screens found&quot;"
date: 2018-03-17
forum: General Help
---

### Post by Montserrat on 2018-03-17
My system crashed with the message “Fatal error: No screens found.” I have Ubuntu 16.04 running on a Satellite C55-B, with an Intel Z36xxx/Z37xxx Series graphics card. The desktop displays folders with Libre Office files I can open, but the launcher does not display apps, and I can’t open Terminal through the dash, nor using the CTRL-ALT-T command. 

I’ve searched for similar problems in the forum, and found a few. In one of them, someone had the same “No screens found” message. In that case, it was a corrupted xorg config file. According to an error report I got, the config file in question is compiz-config-profile-setter (Executable Path: /usr/lib/x86_64-linux-gnu/unity/compiz-config-profile-setter). How may I recover this executable, reset to its default, or edit the darn thing so everything works? Hopefully, I can get assistance specific to my system.

Note that I can regain the launcher and terminal if I boot up in failsafe mode, but that doesn’t fix the problem permanently, i.e., the same problem recurs if I’m not in failsafe mode.

---

### Post by T.J. on 2018-03-18
Your X11 installation configuration file has either been damaged or misconfigured; and the system cannot figure out what resolution is safe to start the machine.

If you add "vga=0x318" to your boot parameters you should be able to force the machine into VGA mode and then you can hopefully reconfigure the graphics device.  I've never worked with Intel graphics hardware - not used a lot in high performance - so I am afraid that my advice is limited, but I will do what I can.

---

### Post by Montserrat on 2018-03-19
Thank you very much T.J. Your help is much appreciated. 

I&#8217;m trying to get assistance specific to Ubuntu 16.04. I might be wrong, but in this case, I think that the x.org config file isn&#8217;t the same as with previous Ubuntu distros, i.e., not the xserver-xorg config file. 

I&#8217;m not sure how I might add to my boot parameters, but I should probably first determine the config file I&#8217;ve got, and where to find it. I think that the config file might be one of nine files in usr/share/X11/xorg.conf.d. 

I&#8217;ve probably also got clues in the output for xorg.0.log, but I&#8217;m not sure where to start. 

Thanks again...

---

### Post by T.J. on 2018-03-20
All true.  However, the existence of a /etc/X11/xorg.conf file should take precedence - at least in theory.  Ubuntu is a Debian derivative.

You should be able to generate a new file by running X in configuration mode, usually something like X --config.  I'd have to check, it's been ages.

---

### Post by Montserrat on 2018-03-20
Thanks again T.J. 

I don&#8217;t have an xorg.conf file in /etc/x11. However, I do have an xorg.conf.failsafe file with the following contents.

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

In related efforts, I ran &#8220;lspci -vvnn | grep VGA&#8221; to confirm that I&#8217;ve got Intel, specifically the &#8220;Atom Processor Z36xxx/Z37xxx Series Graphics & Display.&#8221; 

Point well taken that the xorg.conf.d files might not take precedence, but I noticed that one of these files points to AMD hardware for graphics. Again, it&#8217;s at usr/share/X11/xorg.conf.d, and in a file called 10-amdgpu.conf. Just in case, I thought I should ask whether that might be the problem. Somewhere, I need a config file that specifies an Intel driver, correct? 

Thanks again... Meantime, I'll research about running your x -config command.

---

### Post by T.J. on 2018-03-20
> **Montserrat said:**
> Thanks again T.J. 

No worries.  The whole point of a forum is to help out.


 > “Atom Processor Z36xxx/Z37xxx Series Graphics & Display.” 

The first step is to confirm that there is a working driver for your chipset.  Intel graphics support can be good or it can be hit and miss.  You may have to do some work by hand to resolve this problem.  What kind of display device are you using?


>  Just in case, I thought I should ask whether that might be the problem.
Generally, no.  Typically, you can safely ignore those files as they are meant for fallback, and will not be used if your device is configured correctly.


 > Somewhere, I need a config file that specifies an Intel driver, correct? 
Correct.  The first thing we need to do is confirm support for your chipset and then we can deal with creating the appropriate file.

> Thanks again... Meantime, I'll research about running your x -config command.
Normally, you can get this information from the installed man page, which should tell you specific information about your installed version of X.  Something like "man X"

---

### Post by Montserrat on 2018-03-20
Okay, I downloaded specs from the Toshiba site. Perhaps this is a ridiculous level of detail, but here you are. The Satellite C55-B5101 has a 64-bit chipset. The X man tells us that the installed version is X11; xorg.0.log tells us &#8220;X Protocol Version 11, Revision 0,&#8221; and mentions &#8220;xorg-server 2:1.18.4-0ubuntu0.7.&#8221; About the display device, I have a generic laptop PnP Monitor, with the display settings showing a built-in display with a resolution of 1366 x 768. 

About support? &#8230;I expect more support from x.org, or the Ubuntu world, than from Intel directly. As a basic question though, shouldn&#8217;t I configure X, or create the proper config file, before downloading a driver? Note that the system had been working just fine for over a year. I seemed to have a working driver for that duration.

---

### Post by T.J. on 2018-03-20
I apologize.  You misunderstood what I meant, friend. I meant only to see if Ubuntu's X11 provided a specific driver for your video chipset. I'll do some looking about and get back to you.

---

### Post by Montserrat on 2018-03-23
Okay, thanks.

---

### Post by T.J. on 2018-04-20
Sorry I didn't get back to you - been occupied with life.  Did you solve your problem or do you still want help?

---

### Post by Montserrat on 2018-04-24
Well hello T.J. Yes, I could still use some assistance. I've had life problems as well, but I've also gone to other forums, such as Ask Ubuntu, and even Xorg. I've had no luck though.

I've also tried generating a config file as we discussed, which would adapt to system hardware. (This sounds ideal.) Unfortunately, I've not found a command that works. I&#8217;ve tried variations, such as the following.

    X --configure
    Xorg -configure

I tried these with and without prefacing the command with sudo, but in all of these cases got the message "Command not found."

As one other development, I checked for drivers on both of my machines -- healthy and sick -- and found that no proprietary drivers are needed for graphics. This brings me back to editing a config file as the solution. But what possible solutions have you thought of?

---

### Post by T.J. on 2018-04-26
Hmm.  Will think about this and get back to you in a day or so.  Middle of the work week for me.  This time, I'll leave myself a sticky note as a reminder.

---

### Post by mörgæs on 2018-04-27
18.04 solves many problems for Atom processors. A quick test would be trying 18.04 in a live boot.

---

### Post by Montserrat on 2018-05-01
Thank you for the reply Mörgæs. Greetings to Iceland!

I see that a new LTS version of Ubuntu has been released since I opened this thread. I used Startup Disk Creator to make a bootable USB for 18.04, unfortunately it doesn&#8217;t seem to work. Startup Disk Creator apparently can&#8217;t burn bootable USBs that are compatible with UEFI. This would have been an interesting experiment, even though 18.04 isn&#8217;t available as an upgrade until July. 

Would you have any more ideas?

---

### Post by mörgæs on 2018-05-01
Greetings back :-)

There are many ways to create a USB stick. Mkusb and Unetbootin are two other alternatives.

---

### Post by Montserrat on 2018-05-08
Ubuntu 18.04 has passed the test. However, I'd rather upgrade than install, so I'll wait until it's available in July.

I used Unetbootin to create a bootable USB. This involved buying a new USB that Unetbootin liked, and learning the magic key (F12) for booting from USB for this Toshiba laptop.

---

### Post by mörgæs on 2018-05-08
Myself I would rather do a fresh install than upgrade.

Anyway, good that 18.04 works. If you consider the problem solved please mark the thread so.

---

### Post by Montserrat on 2018-05-10
Well, it's more of a work-around than a solution, but what the heck... I can close the thread.

---

