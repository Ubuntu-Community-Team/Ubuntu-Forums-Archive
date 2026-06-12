---
title: "Gnome Shell ext Locked up computer in Ubuntu 17.10.1"
date: 2018-02-02
forum: General Help
---

### Post by irv on 2018-02-02
I upgraded to 17.10.1 today and when I was installing my Gnome shell Ext. and everything was going great until I came to Easy Screencast. It locked up and I had no choice but to power off. Not I can not get back to the desktop.
I can login and when it starts to load the desktop it just locks up. Is there a way to uninstall the Shell ext.? I Booted into recovery mode and got to a prompt and did a:
```
apt remove chrome-gnome-shell
```
and it told me it removed it. I then tried to reboot again and it still locks up when loading the desktop.
Outside of doing a complete install of the OS, is there something else I can try?

---

### Post by deadflowr on 2018-02-02
Are you installing the ext from gnome extension's web page or from the gnome-shell-extensions collections you can install from apt/the software store?

The former should be as easy as removing the extensions folder from ~/.local/share/gnome-shell/extensions and doing a restart (or maybe a logout login)

The latter might require you to switch to a console and try removing through apt command.

the chrome-gnome-shell package just allows you to install extensions directly from the web pages through the browser, instead of having to manually download the extension and manually install it yourself.
So it's removal won't help, or is at best non-consequential.

---

### Post by irv on 2018-02-03
From the gnome extension web page. [https://extensions.gnome.org/]("https://extensions.gnome.org/")
I had time, so I just did a reinstall and I wrote a script file to reinstall all my programs. It was a fresh install on a SSD on my little 11" Dell so it when fast.
I have always installed ext for gnome from the web. Is it better to do it from the software store?

---

### Post by irv on 2018-02-03
Is anyone else having trouble with EasyScreenCast in version 17.10.1 locking up? I was going to try it again but I will wait to hear from others. It works in 17.04 and 16.04.

---

### Post by Frogs Hair on 2018-02-03
Listed compatibility goes up to Gnome 3.22 and could be the problem.

---

### Post by irv on 2018-02-03
I have been using Unity up until the last version 17.04. I switch Gnome in that version so when I went to 17.10.1 and when I go to 18.04 in April I will be using Gnome. I have already tried 18.04 Alpha and I like it.
Not sure what version of Gnome I am using. Hey Frogs Hair, Where do I find the version number? I don't see it in the tweak tools.

---

### Post by Frogs Hair on 2018-02-03
> [COLOR=#000000]Where do I find the version number?[/COLOR] The extension page as a drop-down menu with supported versions though I see 17.10 uses 3.26 . See details window in settings for Gnome version. 

Edit: corrected Gnome version for 17.10 release.

---

### Post by irv on 2018-02-06
> **deadflowr said:**
> Are you installing the ext from gnome extension's web page or from the gnome-shell-extensions collections you can install from apt/the software store?

The former should be as easy as removing the extensions folder from ~/.local/share/gnome-shell/extensions and doing a restart (or maybe a logout login)

The latter might require you to switch to a console and try removing through apt command.

the chrome-gnome-shell package just allows you to install extensions directly from the web pages through the browser, instead of having to manually download the extension and manually install it yourself.
So it's removal won't help, or is at best non-consequential.

I tried to delete from a shell prompt in recovery mode but they are all read only. and it will not let me change the right. I tried chmod command.

---

### Post by irv on 2018-02-06
I got it. I booted with a live USB and change it there. I am going to mark solved.

---

### Post by monkeybrain20122 on 2018-02-06
Kind of similar to [https://ubuntuforums.org/showthread.php?t=2375743](https://ubuntuforums.org/showthread.php?t=2375743)

But it affected only wayland and I was able to delete the easyscreencast addon from xorg.

---

### Post by irv on 2018-02-07
For the Record, monkeybrain20122 that link you posted is the same problem. These threads are the same problem.
I have the same problem on two laptops and it is the EasyScreenCast that is causing the lockup. Looks like I have to go back to using RecordmyDesktop until it gets fixed.

---

### Post by irv on 2018-02-07
This problem is Wayland. It is really some programs and apps that don't play right with Wayland. The three that I use that have issues are the EasyScreenCast, UNbootin, and gparted. I had to switch back to Xorg to get them to work. Here is a good how to switch back and fourth. 
[https://itsfoss.com/switch-xorg-wayland/]("https://itsfoss.com/switch-xorg-wayland/")

---

### Post by irv on 2018-02-08
Just so everyone knows, This ext will not work with Wayland, you have to use Xorg. So far I found this one and UNbootin, and gparted that need Xorg to work. There most likely will be more.

EDIT: forget this post see the one above. I forgot I posted already. I am getting forgetful. Age you know.

---

