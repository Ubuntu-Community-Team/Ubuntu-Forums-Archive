---
title: "ubuntu closes session randomly"
date: 2015-11-19
forum: General Help
---

### Post by Tiago_Boberg on 2015-11-19
Hello, I recently installed Ubuntu 14.04 LTS. Clean install, plus 3rd party installs. I have already finished updating everything. My problem ocurres randomly and without a obvious pattern. My session will be closed abruptly, the screen will go black then purple and finally will show the login screen. When i enter, all the work i had open previously would be closed as if coming back from rebooting. I'm quite at a lost. I have a very similar problem as referred in this post, but its not caused by moving the window [URL="http://askubuntu.com/questions/617379/my-gnome-session-crashes-how-to-find-out-why-and-solve-the-problem"]http://askubuntu.com/questions/617379/my-gnome-session-crashes-how-to-find-out-why-and-solve-the-problem

[/URL]
Computer specs:
Lenovo G570
Intel Pentium CPU B960 @ 2.20GHz x 2
Intel Sandybridge Mobile x86/MMX/SSE2
32 Bit
310,7 GB

---

### Post by tgalati4 on 2015-11-19
Could be a graphics problem that is crashing the X-server.  Check your log files.  Open a terminal.

```
more /var/log/Xorg.0.log
more ~/.xession-errors
```

Spacebar to page forward.  "q" to quit.

Only post the errors, not the entire log file.

---

### Post by Tiago_Boberg on 2015-11-19
Well I did what you told me, checked the logs, and I only can find a few warnings, but no Errors
i found this
```
Nov 19 13:01:39 yankee-Lenovo-G570 NetworkManager[741]: <warn> error requesting auth for org.freedesktop.NetworkManager.enable-disable-wimax: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.265': no such name
Nov 19 13:01:39 yankee-Lenovo-G570 NetworkManager[741]: <warn> error requesting auth for org.freedesktop.NetworkManager.network-control: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.265': no such name
Nov 19 13:01:39 yankee-Lenovo-G570 NetworkManager[741]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.protected: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.265': no such name
Nov 19 13:01:39 yankee-Lenovo-G570 NetworkManager[741]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.open: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.265': no such name
Nov 19 13:01:39 yankee-Lenovo-G570 NetworkManager[741]: <warn> error requesting auth for org.freedesktop.NetworkManager.settings.modify.system: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.265': no such name
Nov 19 13:01:39 yankee-Lenovo-G570 NetworkManager[741]: <warn> error requesting auth for org.freedesktop.NetworkManager.settings.modify.own: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.265': no such name
Nov 19 13:01:39 yankee-Lenovo-G570 NetworkManager[741]: <warn> error requesting auth for org.freedesktop.NetworkManager.settings.modify.hostname: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.265': no such name
```

Any other suggestions? I’m not very savy with the terminal. thanks!

---

### Post by tgalati4 on 2015-11-19
I don't recognize those errors, and they don't seem related to graphics anyways.  Intel integrated graphics tend to use shared RAM as video RAM.  Sometimes you can set how much RAM is devoted to graphics in BIOS.  Try increasing it.

I've seen similar problems with ATI graphics chips and the problem was delamination of the graphics chip from the motherboard due to excessive heat and poor soldering.  Perhaps there is a bad batch of these Lenovo's out there.  

Does it lockup under Windows?

---

### Post by bovender on 2015-11-20
I wonder if this is similar to [http://ubuntuforums.org/showthread.php?t=2301373](http://ubuntuforums.org/showthread.php?t=2301373)

---

### Post by Tiago_Boberg on 2015-11-21
I checked the BIOS settings but there were no settings referring to limiting or setting a value to the graphics, ram, memory. It was nearly impossible to play video games in windows. Thats my main reason for changing to Ubuntu.

Now when I try to send the report, It tells me that Xorg crashed and that it doesnt have enough memory, is there a easy way to limit this? or to make it work more smoothly?

---

### Post by meltingpot2015 on 2016-01-03
> **Tiago_Boberg said:**
> I checked the BIOS settings but there were no settings referring to limiting or setting a value to the graphics, ram, memory. It was nearly impossible to play video games in windows. Thats my main reason for changing to Ubuntu.

Now when I try to send the report, It tells me that Xorg crashed and that it doesnt have enough memory, is there a easy way to limit this? or to make it work more smoothly?

I have the same problem. syslog has the following errors:

NetworkManager[1048]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.open: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.27': no such name

This is very similar to (exactly the same?) as the error you are getting. TO be fair, this error message may be a red-herring.

I didn't know that it was just closing the xession (logging me off). I was thinking my notebook was performing a reboot. It always happened when I was away from it. I would come back to work and it was at the x-login screen.

By the way, which graphics driver are you using??. I switched to the xorg driver and since then I have this problem. Might switch back to the propriety driver and see how that goes.

The propriety driver did give me some issues, e.g. moving windows seem to take ages, scrolling down a directory on PCManFM used to take ages refreshing the screen. that's the reason I switched to the xorg driver. See my post at [http://ubuntuforums.org/showthread.php?t=2298437&p=13380248#post13380248](http://ubuntuforums.org/showthread.php?t=2298437&p=13380248#post13380248)

Anyway, will keep you posted on how switching to the propriety graphics driver goes. Mine is an ATI Radeon graphics driver. Here is part of the output from ```
sudo lshw -c video
```

product: Kabini [Radeon HD 8400]
vendor: Advanced Micro Devices, Inc. [AMD/ATI]

---

