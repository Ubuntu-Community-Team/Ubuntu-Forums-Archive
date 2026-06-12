---
title: "display problems upon startup"
date: 2005-10-23
forum: General Help
---

### Post by toastedcheese on 2005-10-23
I dual boot Hoary and Windows XP. Yesterday, Firefox spontaneously closed on me. When I tried to reopen it, nothing happened, and when I tried to open Galeon instead, there was also no response. Rather than investigate, I decide to restart the computer. The reboot went fine until I got to the opening Nvidia screen, which flickered slowly off and on about a half-dozen times. Then I got this message: 

"The display server has been shut down about 6 times in the last 90 seconds, it is likely that something bad is going on. I will wait for 2 minutes before trying again on display."

I waited the extra two minutes, but the same thing happened once more. The computer is working fine in Windows, so it can't be a hardware problem. Any ideas? (Note that, although I've been running Linux for a couple years, I'm still a newbie to some extent, and I've only had Ubuntu for about two months.)

---

### Post by Xian on 2005-10-24
I would first eliminate any possibility that the video driver has a role in this issue. When the login fails just clear the errors until you get to a command prompt. From there edit your xorg.conf file by using nano. Goto the "Device" section and change the line for the driver from nvidia to vesa (or nv). Then reboot.

Here is the file edit command:

```
$ sudo nano -w /etc/X11/xorg.conf
```

---

### Post by toastedcheese on 2005-10-24
I changed it to vesa; it's still doing the same thing, just with a blank screen instead of the Nvidia logo.

---

### Post by Xian on 2005-10-24
Okay, good. At least you know it isn't the video driver. You'll now need to do some further investigation. The best place to start is by reviewing the Xorg log file. Open the log and scroll through to try and find some errors that would indicate what may have gone wrong.

```
$ nano -w /var/log/Xorg.0.log
```

---

### Post by toastedcheese on 2005-10-24
The person I consulted before trying the forums looked over that file and didn't see anything wrong. When I look over it myself, these are the only things that look vaguely problematic:

(note, this is a copy of the file that I made before changing the video driver, if it makes a difference)

```

(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "BENQ FP581s"
(**) |   |-->Device "NVIDIA Corporation NV18 [GeForce4 MX - nForce GPU]"
(**) |-->Input Device "Generic Keyboard"

```
The monitor listed is the one I was using during installation, not the one I have now. It must have been like this the whole time, though, so I can't imagine it makes a difference.

```
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
```
This looks like the most likely problem; I googled it and it seems to correspond with monitor problems. But it's still just a warning.

```

(WW) NVIDIA(0): Multiple displays connected, but only one display allowed;
(WW) NVIDIA(0):      using first display
```
Dunno why it's telling me this, but considering I only have one monitor, it doesn't seem like a big deal.

---

