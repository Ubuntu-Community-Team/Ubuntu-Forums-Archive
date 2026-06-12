---
title: "Installing some applications via Ubuntu Software leads to a crash"
date: 2018-12-21
forum: General Help
---

### Post by 12q1 on 2018-12-21
Hi guys,

Firstly I should say I'm quite new to ubuntu/linux so please bear with me. 

I am encountering a strange issue on my desktop when installing certain applications via Ubuntu Software such as Atom, Visual Studio, Slack. They seem to install fine but when opening those apps my computer suddenly goes into a black screen for a minute and then sends me back to the login page. After logging in again all my windows/apps that I had opened are closed so I assume this is some kind of crash.

Oddly this doesn't happen for every application. I am able to install other applications from Ubuntu Software without a problem. It seems to happen mostly on text editor / text based programs but that is just my own speculation.

For now I am able to 'fix' this problem by manually downloading the .deb files from the respective websites of those applications.

I also have Ubuntu installed on 2 laptops but I do not encounter problems with Ubuntu Software on those machines. Only my desktop.

I've searched for a solution but came up empty handed. I would appreciate if someone could shed some light on this for me. 

Thank you.

---

### Post by ajgreeny on 2018-12-21
Are those crashing apps installed as snap packages?

If you're not sure have a look at the output of command ```
snap list
```
Snap packages seem occasionally to be causing problems so it may be that you need to use the alternative third party .deb packages only, though be aware that there is no specific Ubuntu or Canonical security checking of these, so do take care, and install third party packages only from sources that you fully trust.

---

### Post by 12q1 on 2018-12-22
> **ajgreeny said:**
> Are those crashing apps installed as snap packages?

If you're not sure have a look at the output of command ```
snap list
```
Snap packages seem occasionally to be causing problems so it may be that you need to use the alternative third party .deb packages only, though be aware that there is no specific Ubuntu or Canonical security checking of these, so do take care, and install third party packages only from sources that you fully trust.

Not anymore, the output from snap list is as follows:
```
Name                  Version         Rev   Tracking  Publisher     Notes
core                  16-2.36.3       6130  stable    canonical&#10003;    core
discord               0.0.5           82    stable    snapcrafters  -
gnome-3-26-1604       3.26.0          74    stable/…  canonical&#10003;    -
gnome-calculator      3.30.1          260   stable/…  canonical&#10003;    -
gnome-characters      3.30.0          139   stable/…  canonical&#10003;    -
gnome-logs            3.30.0          45    stable/…  canonical&#10003;    -
gnome-system-monitor  3.30.0          57    stable/…  canonical&#10003;    -
gtk-common-themes     0.1-4-g88bc1b2  818   stable/…  canonical&#10003;    -
vlc                   3.0.4           555   stable    videolan&#10003;     -

```

I uninstalled the snap versions and manually downloaded the .deb files. I guess it is some hardware or configuration problem specific to this machine because it works on other devices.

---

