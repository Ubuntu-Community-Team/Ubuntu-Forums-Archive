---
title: "no display at all"
date: 2016-01-09
forum: General Help
---

### Post by wyndlass on 2016-01-09
recently i made a mistake with /etc/default/grub, on the line that includes "splash quiet" or the other way around, i put video=VGA-1:d instead of video=LVDS-1:d. that wouldn't have been a problem if my screen hadn't broke. i tried to edit /etc/default/grub blind but couldn't do it. i didn't try to use my computer for a few days then i came up with the idea to delete /etc/default/grub and use update-grub. that gave me my external display back. i edited the /etc/default/grub~ to have instaead video=LVDS-1:d video=VGA-1:e, cp grub~ grub, update-grub, then rebooted. i still can't see the grub menu but i have the external display and vivid no longer registers the broken internal screen. if any of you have this problem of no display, of course( unless you know what you did wrong like i figured out i did), check your cables first. if they are all nice, snug, and fully seated then try, in a ctrl-alt-f1-f6 terminal after the system fully boots( doing so in the login screen is fine) you'll have to login in the terminal then sudo rm /etc/defaul/grub, update-grub, and reboot. that's what i did to get my external display back. i hope this helps someone that's having this problem. i do realize that this only works with a limited number of situations but i do know that it works.

---

### Post by QIII on 2016-01-09
Hello!

Your post is difficult to read.  It might be best to edit it and create paragraphs.

I did not see what you are using as a graphics adapter and what release of Ubuntu you are using.  Could you share that information with us?

---

### Post by wyndlass on 2016-01-10
sorry i'm used to facebook's no paragraph unless you cut and paste posting. my laptop/netbook is a samsung np-nc10 atom n270 cpu intel 945GME x86/MMX/SSE2 gpu using vivid. i keep forgetting that i can paragraph here since i can't in fb w/o cut and paste. 

this should work( knock on wood) for most versions of grub and ubuntu.

---

