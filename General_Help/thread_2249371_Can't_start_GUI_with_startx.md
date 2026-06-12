---
title: "Can't start GUI with startx"
date: 2014-10-21
forum: General Help
---

### Post by andreadixon825 on 2014-10-21
Hi, I was just messaging around with plmouth :mad: and It worked and all but now when I start the computer up my new Plymouth works and then it takes me to command prop not gui and I typed in startx and the screen goes black and dose nothing for a long time, is there away I can go and change the settings back to normal? I really do not want to reinstall xubuntu all over aging. Thanks

update: I got the default plmouth back but still cant start gui with startx just a black screen?

---

### Post by ajgreeny on 2014-10-21
Try **sudo apt-get install xubuntu-desktop** which may help get back to your previous situation.

---

### Post by andreadixon825 on 2014-10-21
Hi, thanks for your reply, I just tryed that and it just says I have the new version installed? wood remove it work and then install it or will that delete everything. This is very sad :mad:

---

### Post by grahammechanical on 2014-10-21
Before you remove Xubuntu desktop even to re-install it you might want to install an alternative desktop. One that does not use a lot of code but one that can get you to a desktop and a terminal. In the past I installed fvwm-crystal as a backup for those occasions when I blew up the desktop.

Regards.

---

### Post by andreadixon825 on 2014-10-21
Hi, I got another desktop installed, but how do I make it start gui when computer goes on, what I mean is that it still brings me to command prop, and I want it to boot with out me having to type in startx every time, I hop that makes cents :)

---

### Post by ajgreeny on 2014-10-22
> **andreadixon825 said:**
> Hi, I got another desktop installed, but how do I make it start gui when computer goes on, what I mean is that it still brings me to command prop, and I want it to boot with out me having to type in startx every time, I hop that makes cents :)
At the login screen you should get the option to use another Desktop which in the Xubuntu login is top left, I think.  See if that helps.

---

### Post by steeldriver on 2014-10-22
If your system is booting straight to a CLI, that suggests you either don't have a display manager (lightdm / lxdm / gdm) installed, or it is not correctly configured. What is the output of

```

cat /etc/X11/default-display-manager

```

---

