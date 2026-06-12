---
title: "Xorg/XFree86 and Samsung SyncMaster"
date: 2004-12-01
forum: General Help
---

### Post by mork73 on 2004-12-01
Hi all, I've just put together a brand new AMD Athlon 64 system and am trying to get Ubuntu working on it, but I've come to a dead halt with trying to get Xorg or XFree86 working.

The mainboard is a Gigabyte GA-K8VM800M which uses the Via K8M800 chipset for the video, so I'm currently using the Vesa driver for Xorg or XFree86.

The problem I'm having is that when X starts, it produces garbage on the screen, and retries. After the third retry, it drops back to the console.

At this stage, the screen mode is screwed up so I can actually only see the first line of the console at the top of the screen, everything below either remains blank or has various ASCII characters.

If I reboot to recovery mode, then I can get a console and view the log files and try to run dpkg-reconfigure xserver-xfree86 (or xorg).

I can't copy the errors to the list as I have to get onto the forums at work and my PC is at home. As I can't get in to X, I haven't gotten as far as configuring email/Internet etc. yet.

Anyway, the log indicates that it can't find a suitable VESA mode to run my Samsung SyncMaster monitor, but I have had the monitor working previously on a different system with XFree86 and Debian Sarge.

I know for a fact it will run 1280x1024@60Hz with 15 bit colour. I have tried many different combinations down to 640x480@60Hz with 8 bit colour, but no go.

If I use the VGA driver instead of VESA, it comes up as something like 320x200 resolution and is unuseable.

Does anyone know a way I can force either XFree86 or Xorg to use 1280x1024@60Hz? I have Xorg on it currently.

Initially I installed the AMD64 version of Warty, then read somewhere during a Google search (back at work again after the first failure) that Xorg 6.8.1 has a Via driver, so I upgraded to Hoary and installed Xorg, but there's no Via driver and I get the same result with the VESA driver.

Any help would be very greatly appreciated.

Pete

---

### Post by HiddenWolf on 2004-12-01
Sorry for the short reply, but i'm not at home right now.

You'd have to run xfree86config, or whatever they renamed it to for xorg, and select the proper resolution/refresh/horizontal and vertical sync ranges.

After that, it should work mostly, and you can edit the config file by hand for minor adjustments.
At least, that's the way I usually do it.

---

### Post by mork73 on 2004-12-01
Thanks HiddenWolf, a short reply is better than no reply  :-)

Anyway, when I get home this afternoon I'll see if I can find the Xorg equivalent and see what happens with that.

If not, I might even go back to XFree86 to see if it will work there.

Pete

---

### Post by daniels on 2004-12-02
Um, even better, just edit /etc/X11/xorg.conf and remove the HorizSync and VertRefresh lines.  Installations done from today onwards (maybe yesterday if the CD generation was quick enough) won't print these troublesome lines out.

---

### Post by mork73 on 2004-12-02
Thanks again for your help HiddenWolf and Daniel, but no joy I'm afraid.

Tonight, after trying xorgcfg and xorgconfig to no avail, I renamed the /etc/X11/xorg.conf file and created a fresh one from scratch, with the same results.

The actual error message is "(EE) VESA(0): No matching modes", followed by unloading some modules, then "(EE) Screen(s) found, but none have a usable configuration".

I'm still a bit unsure if this is actually the display adaptor or the monitor that is causing the issue.

Just above this error, it registers the monitor's name as "SyncMaster", and a serial number, however it then says it's searching for matching VESA mode(s), but the next line is blank.

The next line after that is a report of the available video memory, which is correct (32768K).

Interestingly enough, a bit above this section, it reports the supported modes as 720x400@70Hz, 640x480@60Hz, and 640x480@75Hz.

It then reports future supported modes, which of course include 1280x1024@60Hz, which is what I want... doesn't bode well I think!

Sorry, but I still can't post the log file unfortunately.

One thing to note is that at work today I installed i386 Ubuntu on a VMWare machine, and Xorg lists a Via driver, but here at home with AMD64, I still do not get the option of a Via driver, but I do get a VMWare driver option, which I didn't have originally.

This changed after I purged xserver-xorg, cleared the apt cache, updated, and reinstalled xserver-xorg.

Running dpkg-reconfigure -plow xserver-xorg doesn't seem to make a difference either.

I'm starting to consider going back to Debian Sarge at the moment, except that there's no guarantee it will work there either...

Any further tips on this at all?

Cheers,

Pete

---

### Post by mork73 on 2004-12-02
Sorry, two other things I haven't mentioned...

Firstly, after the purge and reinstall tonight, the Horizontal and Vertical refresh lines are not there at all.

Secondly, trying 640x480@60Hz does not work, even though it is one of the supposedly supported modes...

Isn't it a bit ironic that the text at the bottom of /var/log/Xorg.0.log says to refer to /var/log/Xorg.0.log for further information?

Pete

---

