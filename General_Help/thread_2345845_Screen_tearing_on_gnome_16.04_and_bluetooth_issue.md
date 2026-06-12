---
title: "Screen tearing on gnome 16.04 and bluetooth issue"
date: 2016-12-08
forum: General Help
---

### Post by boatcat on 2016-12-08
Hi, 

I've recently switched from windows and am still trying to iron out a few kinks with my system.  

1. I have a Lenova yoga 2 13 with an integrated intel graphics chip and am having some problems with screen tearing both online and on vlc/mpv.

2. When I initially installed gnome bluetooth was working perfectly and I was able to connect and play audio through an external speaker. However, I think some updates may have thrown a spanner in the works. I can still connect to the speaker via bluetooth but it does not appear as an output option under the sound settings. 

Let me know what other info you need. 

Thanks,

---

### Post by #&amp;thj^% on 2016-12-08
Some got rid off the Screen Tearing by disabling **"smooth scrolling"** option in the Settings. Unfortunately, the same procedure doesn't seem to help in chromium and other Browsers.
So try that first.

And Others have used a more Advanced method by creating or editing the file at **"/usr/share/X11/xorg.conf.d/20-intel.conf"** as root with the following:
```
sudo -H gedit X11/xorg.conf.d/20-intel.conf
```
Adding the following or amending the one there..."If one is present"

```
Section "Device"
    Identifier "Intel Graphics"
    Driver "intel"
    Option "AccelMethod" "sna"
    Option "TearFree" "true"
    Option "DRI" "3"
EndSection
```
Save and Close gedit.
A reboot will be needed for this to take effect.
From some of the discussions, the "AccelMethod" should by default be sna,** but apparently not explicitly setting it as such could cause X to crash.** sna is definitely faster than downgrading it to uxa.
"TearFree" helps prevent tearing in video rendering
"DRI" is a method on how the driver renders things.
Also have a look at this for more information if needed: [https://ubuntuforums.org/showthread.php?t=2293066](https://ubuntuforums.org/showthread.php?t=2293066)

Your Bluetooth problem would probably be best and less confusing here in this thread... to post another thread.

---

### Post by boatcat on 2016-12-08
> **1fallen said:**
> 

And Others have used a more Advanced method by creating or editing the file at **"/usr/share/X11/xorg.conf.d/20-intel.conf"** as root with the following:
```
sudo -H gedit X11/xorg.conf.d/20-intel.conf
```
Adding the following or amending the one there..."If one is present"

```
Section "Device"
    Identifier "Intel Graphics"
    Driver "intel"
    Option "AccelMethod" "sna"
    Option "TearFree" "true"
    Option "DRI" "3"
EndSection
```
Save and Close gedit.
A reboot will be needed for this to take effect.
From some of the discussions, the "AccelMethod" should by default be sna,** but apparently not explicitly setting it as such could cause X to crash.** sna is definitely faster than downgrading it to uxa.
"TearFree" helps prevent tearing in video rendering
"DRI" is a method on how the driver renders things.
Also have a look at this for more information if needed: [https://ubuntuforums.org/showthread.php?t=2293066](https://ubuntuforums.org/showthread.php?t=2293066)

Your Bluetooth problem would probably be best and less confusing here in this thread... to post another thread.



I tried this and I think it's done the trick. Will watch a film this evening to test it out a bit more.  You've been massively helpful again.

---

### Post by boatcat on 2016-12-13
Hmmm, it seems the tearing is still an issue and is particularly bad with vlc. Is there anything else I can do?

---

