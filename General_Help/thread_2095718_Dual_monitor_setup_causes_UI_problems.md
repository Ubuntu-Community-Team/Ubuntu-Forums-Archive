---
title: "Dual monitor setup causes UI problems"
date: 2012-12-17
forum: General Help
---

### Post by crantok on 2012-12-17
Hi,

I've just moved from Ubuntu 10.04LTS to Xubuntu 12.04LTS.

I have tried using both arandr and then xrandr to set up dual monitors for my widescreen laptop and attached 4:3 CRT. While the screen regions are set up to be fully (or nearly fully) overlapping everything works, although this isn't very useful for me.

As soon as I extend the desktop so that the screens do not overlap, I get some UI errors. These include:
 - Most windows are darker. They look greyed out.
 - Right click menus are greyed out and can be unreadable.
 - Window Z-order behaviour changes: My terminal (which is not greyed out) is always on top, regardless of focus.

I've found two threads that mention this same issue.
    [[xubuntu] Gray shade overlay in dual screen setup]("http://ubuntuforums.org/showthread.php?t=2035276") 
includes a screen shot that looks pretty much like what I'm seeing. The problem wasn't solved.
    [[xubuntu] Issue with dual monitors and xrandr]("http://ubuntuforums.org/showthread.php?t=1793278")
was solved for the OP by setting both screen resolutions to be identical. Unfortunately this hasn't worked for me.

My laptop is a Dell Inspiron 640M. lspci says this about my graphics card:
```
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
```

---

### Post by crantok on 2012-12-18
Has anyone had the same problem and managed to solve it? I'd be really grateful for any information.

---

### Post by crantok on 2012-12-19
I guess if no one has replied by now then this is not a common problem. Still, it's tempting to bump it 2 more times after this, just so I can change the OS listed in my profile.

I would be interested to hear whether many Xubuntu users are dual monitor users. I'm so used to working this way that it didn't occur to me until just now that this might not be a common setup.

---

### Post by dannyboy79 on 2012-12-19
have you checked this out?
[http://www.webupd8.org/2012/11/how-to-use-multiple-monitors-in-xubuntu.html](http://www.webupd8.org/2012/11/how-to-use-multiple-monitors-in-xubuntu.html)

---

### Post by crantok on 2012-12-19
Thanks for the tip. I'd not tried the first method (adding dev PPA). I just tried it now but apt-get would not upgrade all packages. I got this message:

```
The following packages have been kept back:
  exo-utils libexo-1-0 libthunarx-2-0 thunar thunar-data xfce4-settings
```

I tried forcing those packages to upgrade in Synaptic Package Manager. Synaptic gave me a list of packages that it would uninstall as a result, including xfdesktop4 and xubuntu-desktop. I was worried I would lose my desktop so I stopped there.

---

### Post by crantok on 2012-12-19
Actually, apt-get explains it pretty well:

```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 exo-utils : Depends: libxfce4ui-1-0 (>= 4.9.0) but 4.8.1-1 is to be installed
             Depends: libxfce4util6 (>= 4.9.0) but it is not installable
 libexo-1-0 : Depends: libxfce4ui-1-0 (>= 4.9.0) but 4.8.1-1 is to be installed
              Depends: libxfce4util6 (>= 4.9.0) but it is not installable
 libthunarx-2-0 : Depends: libxfce4ui-1-0 (>= 4.9.0) but 4.8.1-1 is to be installed
                  Depends: libxfce4util6 (>= 4.9.0) but it is not installable
 thunar : Depends: libxfce4ui-1-0 (>= 4.9.0) but 4.8.1-1 is to be installed
          Depends: libxfce4util6 (>= 4.9.0) but it is not installable
          Recommends: xfce4-panel (>= 4.9.2) but 4.8.6-2ubuntu2 is to be installed
 xfce4-settings : Depends: libxfce4ui-1-0 (>= 4.9.0) but 4.8.1-1 is to be installed
                  Depends: libxfce4util6 (>= 4.9.0) but it is not installable
                  Depends: libgarcon-common (>= 0.2.0) but 0.1.11-0ubuntu1 is to be installed
E: Unable to correct problems, you have held broken packages.
```

---

### Post by dannyboy79 on 2012-12-19
im sorry, i am not sure how to solve dependency issues. it looks like a mess. adding the ppa per that webpage seemed like an easy solution but as you found out, it doesn't appear to be. not sure how to help?

---

### Post by crantok on 2012-12-19
It does look a bit of a mess. I appreciate you posting the link anyway. Thanks for trying.

I normally stick with LTS editions but, as Ubuntu 10.04 is near end-of-life, I think I'll try Xubuntu 12.10 and see if my dual monitor setup works better on that.

---

### Post by crantok on 2012-12-21
Upgraded to 12.10 and tried adding the PPA from [#4]("http://ubuntuforums.org/showpost.php?p=12412281&postcount=4") again to get dual monitor support. Adding the PPA and upgrading was successful under 12.10.

Unfortunately, although control of dual monitor setup is now available through Xubuntu's display settings, this hasn't solved the UI problems. I'll post a bug report about this. In the meantime I'd be grateful for any OS recommendations I've tried the last few Ubuntu releases but didn't get on with the GUI,

---

### Post by dannyboy79 on 2012-12-21
i am really enjoying Xubuntu 12.04. Nice clean interface without Unity. You can still install some Ubuntu apps if you desire like gedit etc etc.

---

### Post by crantok on 2012-12-21
Unfortunately, I really want dual monitor support. I work with a laptop and plug it in to a monitor at home and another in the office. I've had dual monitor support for years in Ubuntu 10.04 and don't want to go back to a single monitor, so Xubuntu's not cutting it for me at the moment.

---

### Post by dannyboy79 on 2012-12-21
> **crantok said:**
> Unfortunately, I really want dual monitor support. I work with a laptop and plug it in to a monitor at home and another in the office. I've had dual monitor support for years in Ubuntu 10.04 and don't want to go back to a single monitor, so Xubuntu's not cutting it for me at the moment.
so you had no problems with ubuntu 10.04? i wonder what intel driver 10.04 used and why there's regression with 12.04 xubuntu and dual display setups. SOrry, I can't help you out.

---

### Post by crantok on 2013-04-17
I just installed Ubuntu 12.04 LTS on the same system that was giving me multi-monitor UI problems with Xubuntu. Ubuntu informs me that there is a hardware limit in 3D mode that stops my total desktop from being wider than 2048 pixels. If Xubuntu is using any 3D functionality (which seems unlikely given its low-spec purpose) then that might explain the UI problems. If anyone else has the same problem then it might be worth running Ubuntu from a USB drive and seeing if Ubuntu gives the same helpful error message that it gave me. If Xubuntu is using some 3D functionality then I would like to know how to turn that off.

---

