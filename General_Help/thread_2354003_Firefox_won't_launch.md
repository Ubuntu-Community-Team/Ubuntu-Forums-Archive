---
title: "Firefox won't launch"
date: 2017-02-27
forum: General Help
---

### Post by TimB48 on 2017-02-27
I have just installed Lubuntu on an old PC with an AMD processor. Lubuntu itself seems to run fine but I cannot get firefox to launch. Crash Reporter launches with the following details.  
Add-ons: ubufox%40ubuntu.com:3.2,%7B972ce4c6-7e08-4474-a285-3208198ce6fd%7D:51.0.1,aushelper%40mozilla.org:1.0,webcompat%40mozilla.org:1.0,e10srollout%40mozilla.org:1.7,firefox%40getpocket.com:1.0.5,langpack-en-GB%40firefox.mozilla.org:51.0.1,langpack-en-ZA%40firefox.mozilla.org:51.0.1
AddonsShouldHaveBlockedE10s: 0
BuildID: 20170201175624
I have installed chromium but that will not launch either and with no error message. I suspect it is probably down to the age of the pc but anyone else had the same problem?

---

### Post by ajgreeny on 2017-02-27
TRy running firefox with command ```
firefox --safe-mode
``` to see if that runs OK.

If so, it is probably an add-on that is causing your problem, so as it is mentioned in your error remove the **xul-ext-ubufox** package with ```
sudo apt-get remove xul-ext-ubufox
```
It is an add-on specifically for the FF used in Ubuntu, but is not required, nor in my experience very useful, though others may disagree with me on that final thought.

---

### Post by TimB48 on 2017-02-28
Firefox would nor run in safe mode. I was able to remove **xul-ext-ubufox **but firefox would still not run and produced the following error.

Add-ons: %7B972ce4c6-7e08-4474-a285-3208198ce6fd%7D:51.0.1,aushelper%40mozilla.org:1.0,webcompat%40mozilla.org:1.0,e10srollout%40mozilla.org:1.7,firefox%40getpocket.com:1.0.5,langpack-en-GB%40firefox.mozilla.org:51.0.1,langpack-en-ZA%40firefox.mozilla.org:51.0.1
AddonsShouldHaveBlockedE10s: 0
BuildID: 20170201175624
ContentSandboxCapabilities: 117

---

### Post by ajgreeny on 2017-02-28
I am not sure where to go from here apart from trying to run FF after renaming the hidden **.mozilla** folder in your home as **.mozilla-backup**.

It may be some configuration problem in your current profile that is your main problem and the rename will give you a clean profile.

---

### Post by vasa1 on 2017-02-28
It may also be worth checking if the hardware meets the minimum specs: See the GNU/Linux section in [https://www.mozilla.org/en-US/firefox/51.0.1/system-requirements/](https://www.mozilla.org/en-US/firefox/51.0.1/system-requirements/)```
GNU/Linux

Software Requirements

Please note that GNU/Linux distributors may provide packages for your distribution which have different requirements.

Firefox will not run at all without the following libraries or packages:
GTK+ 3.4 or higher
GLib 2.22 or higher
Pango 1.14 or higher
X.Org 1.0 or higher (1.7 or higher is recommended)
libstdc++ 4.6.1 or higher
For optimal functionality, we recommend the following libraries or packages:
NetworkManager 0.7 or higher
DBus 1.0 or higher
GNOME 2.16 or higher
```

The same could apply to chromium-browser:```
To use Chrome on Linux, you'll need:

64-bit Ubuntu 14.04+, Debian 8+, openSUSE 13.1+, or Fedora Linux 21+
An Intel Pentium 4 processor or later that's SSE2 capable 

```Source: [https://support.google.com/chrome/answer/95346?co=GENIE.Platform%3DDesktop&hl=en](https://support.google.com/chrome/answer/95346?co=GENIE.Platform%3DDesktop&hl=en)

---

### Post by $yl9pAR%t on 2017-02-28
I suppose lack of SSE2 is your problem. You can check CPU flags in terminal:

```
inxi -f
```

---

### Post by TimB48 on 2017-02-28
Ran inxi and it reported only single core processor, so chrome definitely won't run and probably the same for firefox. I have achieved want I wanted to without using a browser, I only wanted to check 2 HDD's from my NAS on something running linux. I couldn't check them run checks whilst still in the NAS, so I took them out and put them in a USB caddy and checked them out with GSmartControl. Thanks for your assistance and advice.

---

