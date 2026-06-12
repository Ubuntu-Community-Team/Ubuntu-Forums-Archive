---
title: "Beryl isn't working"
date: 2006-12-03
forum: General Help
---

### Post by Vasant56 on 2006-12-03
Hi, following these instructions, I just set up Beryl.

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Xgl.2FBeryl_.28ATI.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Xgl.2FBeryl_.28ATI.29)

But when I login to the XGL session everything is all funky. Windows open slowly, and things just don't seem to work right. I'm running a Thinkpad T42 with a Radeon 9600 mobility.

I followed the ATI Graphics installation, and my output matched their when I confirmed it. I also had 3D Accerlation available. I followed the other instructions exactly, the only thing that seemed weird is that when I made a startup script, the stuff I added was the only stuff in the startup file (is that okay). Is there anything else I can check to see why this is all funky?

Thanks

---

### Post by Vasant56 on 2006-12-03
Hey guys, any help would be greatly appreciated =)

---

### Post by toolunious on 2006-12-04
Hi,

I had the same problem (ATI Radeon 9600 Pro) with XGL. Do you have 3D direct-render in your XGL session? 

Some things you would like to check:
-Is there DRI section in your xorg.conf
    *Composite disabled
-used the right start-up programs for your session?(beryl-manager, beryl-xgl and xmodmap /usr/share/xmodmap/xmodmap.us)

Good luck,
Martijn

---

### Post by bg1256 on 2006-12-04
Try posting in the HowTo on these forums.

---

