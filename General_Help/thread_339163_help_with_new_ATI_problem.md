---
title: "help with new ATI problem"
date: 2007-01-15
forum: General Help
---

### Post by darkenedday on 2007-01-15
I have recently come across an ATI Radeon 9250 (256 mb DDR memory, 3D acceleration etc.) in most regard this card OWNS my old Nvidia geforce MX/MX 2 (32mb) I installed it once and it worked beautifuly on PClinuxOS, this is when I was running my old 700mhz AMD duron processor, I then upgraded the processor to a 1200 mhz AMD athlon thunderbird, runs great, all but the video card, when i tried to boot back into pclinuxOS it would get to the first boot splash (the one with just the logo and the load bar, i think thats the uspash?) and then the screen would go blank, so i figured maybe I had to reinstall, but I put in any range of live cd's and non of them had any better results. ](*,) so i figured it must be my video card, I took it out and replaced it with my old nvidia, could you imagine? it started right up, so, assuming if there's any distro I could use to solve this problem I figured it would be Kubuntu (not a big fan of gnome) with the help of these wonderful forums, I would love to get this card working now that my PC doesn't suck quite as much, and I doubt AIGLX + Beryl/Compiz would slow down at all as compared to the old hardware that would take days to load anything with 3d Accel. if anyone has any ideas on what i should do please let me know. . . Should i install the ATI drivers with the nvidia card in and shutdown then reboot with the ATI radeon and hope for the best? I'm lost please help 

THANKS!

---

### Post by peabody on 2007-01-15
How good are you with the command line?  If you turn off the GDM service, it'll dump you directly to a command prompt without X launching on boot.  Provided you have the ATI drivers and the instructions and dependencies for installing them you should be good to go.

[Edit: admmitidly, if you can't get to a command prompt, you might be sunk, the only thing I can recommend at that point is to do what you suggest, which is to install the display driver while using another video card, shutdown, install the card, boot up].

There's two things you can do from here.  One is a dpkg-reconfigure xserver-xorg to change your X setup to something that doesn't make the card barf.  The other thing you can try is the proprietary drivers.  You'll probably have much better luck with the proprietary drivers.  I had a Radeon 9000 that would freeze anytime opengl was used (LiveCD or install) unless the proprietary drivers were installed.

Once you've made your changes, just run "startx" and hope for the best.

---

