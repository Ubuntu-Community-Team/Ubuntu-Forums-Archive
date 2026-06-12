---
title: "Force display mode when using 4k hdmi switch"
date: 2021-02-22
forum: General Help
---

### Post by gwesty on 2021-02-22
Hi All,

I've got a bit of an issue and am hoping someone here can help.

I have an ubuntu 20.04 system that *used to *have an Nvidia GT210 card, DVI and HDMI output. Those outputs go into a 4 x 4 hdmi switch matrix which is 4k capable. The output from the 4x4 goes to two Samsung monitors each running 1920x1080 on a HDMI to DVI cable. That system has been running fine for 6 ish months.

I to get some better performance I upgraded the card to a GT1030 with HDMI and Display Port out and I can not for the life of me get things working.
If I bypass the 4x4 and run HDMI to DVI directly into one of the monitors and DP to DVI to the other then I get normal output, both monitors detected fine.
During reboot both screens display the "HP - Ubuntu" boot splash screen.
I swap the HDMI output to run through the 4x4 and it detects but at 4k (to be expected I guess), I manually drop the resolution to 1920x1080, apply and it works.
During a reboot I notice that the "HP - Ununtu" splash screen does not display on the HDMI output screen
Finishes booting but now the DP (direct from the card) screen appears to be the second display and is not showing the logon screen.
Turning off the 4x4 makes the display refresh and the logon screen appears on the DP monitor... I can then log on, turn the 4x4 back on and the display works as expected.

The same also seems to be true if I leave the HDMI output connected directly but run the DP through the 4x4.

I have unplugged everything else but power, network, keyboard, mouse (there were some hdmi capture usb sticks and webcams connected)

What I am assuming is...
that at some point the card is polling for recommended resolution and the 4x4 matrix is returning 4k, the system is then setting its self to that and won't let go even though I have specifically told X that it should be 1920x1080. Strangely, the previous NVidia card did not seem to have the same issue. The same card in an identical PC but running windows appears to work fine so I can rule out hardware although I did have to tweak the refresh rate to get it working.

Does anyone have any suggestions or ways that I can maybe tell the system to max out at 1920x1080 and not to go higher. I would love to replace the two screens with 4k ones (which I suspect would "fix it") but I don't really have the cash hanging around to do that!

---

### Post by CatKiller on 2021-02-22
> **gwesty said:**
> What I am assuming is...
that at some point the card is polling for recommended resolution and the 4x4 matrix is returning 4k, the system is then setting its self to that and won't let go even though I have specifically told X that it should be 1920x1080.  

The mechanism is called EDID. You can tell X to ignore all or part of the information it gets through EDID. Your computer's only being fed the EDID of your adaptor rather than the EDID of your monitor. 

>  Strangely, the previous NVidia card did not seem to have the same issue.

Your old card was using DVI, which can't go up to 4K (1920×1200 is the maximum) and, from the age of it, your old card was using nouveau which isn't that great at picking up EDID anyway.

---

### Post by gwesty on 2021-02-23
Thanks for the info there CatKiller.

I think at one point I did try and none 4k HDMI cable and that gave different results to the rest of the cables. Didn't realise that DVI maxes out at 1920x1200, I'll bank that info.

I've just had a little google around that "EDID" and found the following page on the Arch Wiki but it looks like it probably applies to my system. Not in the office today so I'll give that a go tomorrow and report back if it works in case anyone else has a similar problem.
[https://wiki.archlinux.org/index.php/kernel_mode_setting#Forcing_modes_and_EDID](https://wiki.archlinux.org/index.php/kernel_mode_setting#Forcing_modes_and_EDID)

---

### Post by gwesty on 2021-02-26
Ok, so a quick update.

I'm getting somewhere but not very fast and not there yet...

I've added several variations of "drm.edid_firmware=edid/your_edid.bin" with it currently set to 1920x1080.bin rather than using the EDID information that I was able to pull from the monitor by connecting it directly.
Still can't get things to work as expected though so I'm beginning to suspect that the matrix switch is the problem. I have another so I've brought that into the office to test with.

---

### Post by CatKiller on 2021-02-26
As an alternative to specifying a binary EDID file, you can set the configuration file with the plain text parts that you're interested in. Details, for example, [here.](http://us.download.nvidia.com/XFree86/Linux-x86_64/460.56/README/xconfigoptions.html) X configuration is kinda crufty because it's *really* old, but you don't need to specify the whole thing any more; you can have snippets of configuration in xorg.conf.d. There will also be a log at /var/log/Xorg.0.log you can look at to see which parts are being used and why particular decisions are being made. It's possible to make the log file more verbose.

Edit: oh, familiarise yourself with editing/deleting text files from the command line and, ideally, how to access files from a live USB, just in case. Many users find it quite off-putting to only boot to a command line (or, worse, a black screen) because they misconfigured things, and it's best to know how to navigate to undo it *before* you find yourself at that point.

---

