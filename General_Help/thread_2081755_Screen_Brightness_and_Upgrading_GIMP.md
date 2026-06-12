---
title: "Screen Brightness and Upgrading GIMP"
date: 2012-11-07
forum: General Help
---

### Post by Spaceman9 on 2012-11-07
I'm running Ubuntu 12.04 LTS in Windows 7 on an HP laptop. I can't keep the brightness for the screen where I set it. When I reboot the screen is very dark again. What do I have to do to keep the brightness where I set it?

I'm running GIMP 2.8 in Windows 7 but Ubuntu 12.04 LTS only seems to have GIMP 2.6. Do I have to install Ubuntu 12.10 to get GIMP 2.8 for Ubuntu?

Thanks for any help.

---

### Post by ibjsb4 on 2012-11-07
For GIMP

[http://www.ubuntugeek.com/how-to-install-gimp-2-8-2-in-ubuntu-12-04-precise.html](http://www.ubuntugeek.com/how-to-install-gimp-2-8-2-in-ubuntu-12-04-precise.html)

---

### Post by dannyboy79 on 2012-11-07
for screen brightness, try these solutions
[http://askubuntu.com/questions/3841/desktop-doesnt-remember-brightness-settings-after-a-reboot/68143#68143](http://askubuntu.com/questions/3841/desktop-doesnt-remember-brightness-settings-after-a-reboot/68143#68143)

---

### Post by Spaceman9 on 2012-11-07
> **ibjsb4 said:**
> For GIMP

[http://www.ubuntugeek.com/how-to-install-gimp-2-8-2-in-ubuntu-12-04-precise.html](http://www.ubuntugeek.com/how-to-install-gimp-2-8-2-in-ubuntu-12-04-precise.html)

Thanks for the help. Should I uninstall GIMP 2.6 first? I don't want two copies of GIMP in Ubuntu.

---

### Post by Spaceman9 on 2012-11-07
> **dannyboy79 said:**
> for screen brightness, try these solutions
[http://askubuntu.com/questions/3841/desktop-doesnt-remember-brightness-settings-after-a-reboot/68143#68143](http://askubuntu.com/questions/3841/desktop-doesnt-remember-brightness-settings-after-a-reboot/68143#68143)

Thanks I'll try that.

---

### Post by holycow131415 on 2012-11-07
> **Spaceman9 said:**
> Thanks for the help. Should I uninstall GIMP 2.6 first? I don't want two copies of GIMP in Ubuntu.


Leave it installed. When you add the repo, the update command will upgrade your current gimp installation.

---

### Post by ibjsb4 on 2012-11-07
> **Spaceman9 said:**
> Thanks for the help. Should I uninstall GIMP 2.6 first? I don't want two copies of GIMP in Ubuntu.

I prefer to completely uninstall first to make sure no configuration files are carried forward.

sudo apt-get remove --purge gimp

And just to make sure nothing is leftover I open nautilus (go to filesystem) and search gimp and remove anything else.  In terminal:

gksudo nautilus

---

### Post by Spaceman9 on 2012-12-21
Thanks for the help everyone. I got GIMP 2.8 installed but I haven't had time to deal with the brightness problem yet. 

I'm having a spot of bother getting sound out of tuxguitar. I'll post that in a different thread.

---

