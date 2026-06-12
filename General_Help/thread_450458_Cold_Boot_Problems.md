---
title: "Cold Boot Problems"
date: 2007-05-21
forum: General Help
---

### Post by Vonagio on 2007-05-21
I am having problems starting my Feisty install from a cold boot (i.e. from the system being off/not restarting). If i let grub do its stuff, Ubuntu will appear to load correctly until i get to Gnome then the display will cut out leaving the backlight on. The machine is an EiSystem/PC World/Gateway 4412 with an Intel 82845G [Brookdale] integrated GPU.

The failure to load Gnome makes me think my xorg.conf isn't right, I have reconfigure it using i810 (the initial install used vesa but didn't allow a resolution more than 800x600, the monitor is 1024x76. However, I'm a little unsure if this is the problem because I can get into Gnome (and subsequently log on and use the computer) by selecting the default kernel in grub on a cold boot. Restarting will load correctly with no selection from me (I assume it runs the same startup when restarting, that's why it will load correctly).

I have thought about needing to change the startup settings (something like boot.ini in Windows), or maybe installing the 845G driver (I don't know how to do this...). Or is there something else i should do?


Thanks for any help, Von

Edit: Maybe there is something i can change in grub...I don't understand the commands it shows when i edit it...

---

### Post by Vonagio on 2007-05-23
Bump, I'm still struggling with this. Reinstalling the OS doesn't make any difference, the CDs I've tried are error free. Edgy works fine on the same machine, it must be the Feisty install.


Von

---

### Post by lassegs on 2007-05-23
Im not really sure about youre problem, but i would like to help.

Here is the link to the Grub documentation:
[http://www.gnu.org/software/grub/manual/html_node/](http://www.gnu.org/software/grub/manual/html_node/)
Grub can be configured by changing /boot/grub.conf

You never tried cold booting it with the VESA driver did you? Just try, to find out if its a videodriver problem.

Also, have a look at /var/log/Xorg.0.log and do a 
sudo dmesg
If these things show you anything suspicious, please post them here.

---

### Post by Vonagio on 2007-05-29
VESA drivers make no difference, the Xorg log doesn't show much of interest... Does this mean that it CANNOT be a video driver problem? I hope this is the case as at least I have narrowed it down a bit.

I'll try doing something with grub, but I really don't know what I'm doing!


Von

---

### Post by Vonagio on 2007-05-29
Installing Dapper/Edgy gets rid of this error, I'm trying to manually update it to Feisty and hopefully this will stop the problems...

Does updating Dapper to Feisty have any negative effect rather than clean installing feisty?


Von

---

### Post by Vonagio on 2007-05-29
Dapper has no problem cold booting, I'm in the middle of upgrading it to Edgy, hopefully the booting will still be ok. Then I intend to upgrade that to Feisty, fingers crossed it wont mess up the system!

I do really like the changes from 6 to 7, they seem to make it all just 'nicer' and it seems to be more of a finished product. I wouldn't like to be stuck with 6.10 now.....


Von

---

### Post by Vonagio on 2007-05-29
At last, I have a fully functional Feisty install that will boot correctly! I have no idea what the problem was, it must have been in the 7.04 install. Now all I've got to do is sort out my WEP wifi, but that's a story for another thread.

Fix for anyone else with a problem like this: Clean install 6.10/6.06 and update to Feisty using ```
gksu "update-manager -c"
```

---

### Post by LiamTreacy on 2007-07-17
Hello. First post here.

I have this exact problem with the 7.04 installation. I have the same video card as the OP here.

The XServer fails only on a cold boot if Grub is allowed to choose the default. Manually choosing a kernel option on cold boot works, and a restart has no problems whatever. I have no other means of installing XUbuntu, so if anybody has a suggestion on how I might fix this, please let me know.

---

### Post by LiamTreacy on 2007-07-20
Alright. I just reconfigured X again, this time answering 'yes' to the framebuffer question, just to do something different. Since then I have not had this problem, and I cannot get the XServer to fail under any circumstances. It seems to be alright now.

---

### Post by LiamTreacy on 2007-09-16
I think I figured out why this was heppening. The Grub boot process has to be delayed. I'd reduced the timeout on Grub from 5 seconds to 3. For some reason this caused the startup of the XServer to hang every time. Increasing the timeout to 5 seconds fixed the problem. That's why delaying Grub by pressing Escape and messing around with the options before booting also worked. That also served as a sufficient delay.

---

