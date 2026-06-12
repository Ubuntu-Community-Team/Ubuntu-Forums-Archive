---
title: "Having trouble with beryl"
date: 2007-02-22
forum: General Help
---

### Post by HarrisonHopkins on 2007-02-22
Ok, I tried to install Beryl using the script at [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL_and_ATI](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL_and_ATI)

Unsurprisingly, it didn't work. So I uninstalled beryl and everything, but now when I do "fglrxinfo" it tells me I am back with mesa. So I have tried reinstalling xorg-driver-fglrx following the original instructions I did before to get it working, but I am still stuck with mesa. How can I fix the stupid crap that beryl did?

---

### Post by teaker1s on 2007-02-22
beta software:( 
secondly
```
sudo dpkg-reconfigure xserver-xorg 
```

---

### Post by HarrisonHopkins on 2007-02-22
And then what?

---

### Post by Maestro23 on 2007-02-22
> **HarrisonHopkins said:**
> And then what?

Install the driver for you card with whatever method you used before.

And stay away from BETA software.;)

---

### Post by igknighted on 2007-02-22
1st - if you install beta software, expect stuff like this to happen

2nd - It sounds like something is wrong with the kernel module.  Your fglrx driver's 2d part is working fine, but the fglrx kernel module is likely what failed.  Unless you have XGL working but not Beryl, in which case your driver is fine, just beryl isn't working right.  When you say "beryl didnt work" thats very vague... what didnt work?  What error messages did you get?  How did you go about uninstalling it?  What session are you logging into, the XGL session now or the standard gnome?

---

### Post by HarrisonHopkins on 2007-02-22
Just redid the driver installation and guess what? I'm stuck with fugly low resolution, and still mesa.

Beryl just didn't work. No error messages, it would just refuse to switch into the Beryl window manager. Uninstalled it by "sudo apt-get remove 'beryl*'"

---

### Post by igknighted on 2007-02-22
> **HarrisonHopkins said:**
> Just redid the driver installation and guess what? I'm stuck with fugly low resolution, and still mesa.

Beryl just didn't work. No error messages, it would just refuse to switch into the Beryl window manager. Uninstalled it by "sudo apt-get remove 'beryl*'"

Did you try running "beryl-manager" from the terminal?  There's got to be some output from that...  any, moot point now.  Use the xserver-reconfigure command from above, but choose radeon as your driver, then also set your monitor res and refresh manually (check your manual for specs).  You will have to choose advanced for this.  Then remove the fglrx drivers via synaptic/apt.  Finally, when this is done, run this command: "sudo modprobe -r fglrx".  Now, restart X (ctrl+alt+backspc) and try reinstalling the fglrx drivers via apt or synaptic.

---

### Post by HarrisonHopkins on 2007-02-22
There is no radeon option in the reconfigure thing. There is however ati. Should I use that? This is a laptop. Aren't LCD screens refresh always 60?

---

### Post by igknighted on 2007-02-22
> **HarrisonHopkins said:**
> There is no radeon option in the reconfigure thing. There is however ati. Should I use that? This is a laptop. Aren't LCD screens refresh always 60?

that /should/ work, otherwise if you get a blacked out screen whien you restart X, restart into recovery mode and try the vesa driver.

---

### Post by aidanr on 2007-02-22
you got a clear warning on the top of the page :-({|=

---

### Post by igknighted on 2007-02-22
> **HarrisonHopkins said:**
> There is no radeon option in the reconfigure thing. There is however ati. Should I use that? This is a laptop. Aren't LCD screens refresh always 60?

I dont know about laptops, if you don't know the refresh rates (horiz and vert) then try to let it autodetect.  My screen is a 17" desktop lcd, and the refresh rates are 30-79Khz horiz, and 56-75 Hz vert.  Ubuntu can't detect them right, so I always have to manually set that.  If you haven't had issues before dont worry about it.

---

### Post by HarrisonHopkins on 2007-02-22
Well, I tried again. Still mesa.... I've got the right resolution back however.... Still can't play my game though. Any other ideas?

---

### Post by igknighted on 2007-02-22
silly question... are you loging into an XGL session, or did you change it back?

---

### Post by HarrisonHopkins on 2007-02-22
Regular Gnome session.

---

### Post by igknighted on 2007-02-22
What is the result of "sudo modprobe -l fglrx"?

---

### Post by HarrisonHopkins on 2007-02-22
/lib/modules/2.6.17-11-generic/volatile/fglrx.ko

---

### Post by igknighted on 2007-02-22
what is the result of "cat /etc/default/linux-restricted-modules-common"?

---

### Post by HarrisonHopkins on 2007-02-22
The only uncommented line is DISABLED_MODULES=""

---

### Post by igknighted on 2007-02-22
Ok, open that file in an editor and put "fglrx" in those quotes.  Then restart and see if it works.

---

### Post by HarrisonHopkins on 2007-02-22
Still mesa if you meant to CTRL-ALT-BACKSPACE

---

### Post by igknighted on 2007-02-22
> **HarrisonHopkins said:**
> Still mesa if you meant to restart xserver

nope, the whole system

---

### Post by HarrisonHopkins on 2007-02-22
Mesa seriously needs to stop stalking me. It's still there. D:

---

### Post by igknighted on 2007-02-22
Hmm, well, I really don't know what to tell you now.  If you don't have important data on there I'd almost say go for a reinstall to start fresh... anybody else got anything to add?

---

### Post by HarrisonHopkins on 2007-02-22
Meh, that's what I've been thinking since the beginning. Only thing is that it takes so long to get this laptop set up for wireless...

I'll do it if no one says anything else once I get out the shower.

---

### Post by aidanr on 2007-02-22
sudo mv /etc/X11/xorg.conf.backup.beryl-script /etc/X11/xorg.conf
sudo rm /usr/share/xsessions/xgl.desktop
sudo rm /etc/xdg/autostart/beryl-manager.desktop
sudo rm /usr/share/applications/beryl-manager.desktop
sudo rm /usr/bin/startxgl.sh
sudo aptitude remove xserver-xgl beryl emerald emerald-themes

as far as i can see, that should be enough to reverse what the script did

---

### Post by HarrisonHopkins on 2007-02-22
> **aidanr said:**
> sudo mv /etc/X11/xorg.conf.backup.beryl-script /etc/X11/xorg.conf
sudo rm /usr/share/xsessions/xgl.desktop
sudo rm /etc/xdg/autostart/beryl-manager.desktop
sudo rm /usr/share/applications/beryl-manager.desktop
sudo rm /usr/bin/startxgl.sh
sudo aptitude remove xserver-xgl beryl emerald emerald-themes

as far as i can see, that should be enough to reverse what the script did

I'm tired of messing with it... I'm going to reinstall Ubuntu, do all the updates, and then just start over... It isn't worth all of this.

---

### Post by HarrisonHopkins on 2007-02-22
After reinstall, it works fine. Thank you all for trying to help.

---

