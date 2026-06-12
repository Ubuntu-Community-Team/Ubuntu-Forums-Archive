---
title: "Screens and Graphics application won't load/show."
date: 2007-12-18
forum: General Help
---

### Post by Richard.F on 2007-12-18
I press the Screen and Graphics application and then nothing happens. Why won't it load?

---

### Post by Purplecatty on 2007-12-18
You will need to log off and on after you set the screen resolution. OR another option.  Go to "System--Preference--Screen Resolution" and this program should be able to change resolution immedialy after you select it.   Oddly,  two different program, Screen and Graphic (in System--Administrator--Screen and Graphic) and Screen Resolution don't function the same but if you use Screen Resolution and change resolution,  the set Resolution you already chosen will already shown in Screen and Graphic box.  

I find it funny tho. IF you use Screen and Graphic to change resolution, log off and log back on.  But if you reboot the system. It'll switch back to preset resolution which is annoying.  

If you use Screen Resolution,  you will see the radio button to checkmark as "Make default for this computer ("your username"-desktop) only".  This will "lock" the resolution for your username only.  But if you play game or run the apps that use full screen,  close the apps and screen went back to old resolution.  Use Screen Resolution to switch back your resoultion. 

 I haven't figure out how to prevent resolution going back to old level.  I'm still a noob tho.  I even tried edit Xorg.conf file (type in terminal "sudo nautilus" and navigate on Root files (Root drive) to ETC/X11 folder which is easier to edit and save in GUI than typing all commands on Terminal)  and deleting some resolutions so it won't fall back to old one.  I saved it and test it, it still falls back to old resolution. I'm frustrated tho.  I'm still searching through Google. I even left thread in blog and no one have come up to offer "fix it and shutup" solution for me.

I hope it works for you.
CAtty:lolflag:

---

### Post by Richard.F on 2007-12-18
> **Purplecatty said:**
> You will need to log off and on after you set the screen resolution. OR another option.  Go to "System--Preference--Screen Resolution" and this program should be able to change resolution immedialy after you select it.   Oddly,  two different program, Screen and Graphic (in System--Administrator--Screen and Graphic) and Screen Resolution don't function the same but if you use Screen Resolution and change resolution,  the set Resolution you already chosen will already shown in Screen and Graphic box.  

I find it funny tho. IF you use Screen and Graphic to change resolution, log off and log back on.  But if you reboot the system. It'll switch back to preset resolution which is annoying.  

If you use Screen Resolution,  you will see the radio button to checkmark as "Make default for this computer ("your username"-desktop) only".  This will "lock" the resolution for your username only.  But if you play game or run the apps that use full screen,  close the apps and screen went back to old resolution.  Use Screen Resolution to switch back your resoultion. 

 I haven't figure out how to prevent resolution going back to old level.  I'm still a noob tho.  I even tried edit Xorg.conf file (type in terminal "sudo nautilus" and navigate on Root files (Root drive) to ETC/X11 folder which is easier to edit and save in GUI than typing all commands on Terminal)  and deleting some resolutions so it won't fall back to old one.  I saved it and test it, it still falls back to old resolution. I'm frustrated tho.  I'm still searching through Google. I even left thread in blog and no one have come up to offer "fix it and shutup" solution for me.

I hope it works for you.
CAtty:lolflag:

I got my resolution working fine but I can't access the displayconfig-gtk application. I need it to set up dual monitors.

---

### Post by Purplecatty on 2007-12-19
What kind of dual head graphic card you have??  

    I have old ATI Radeon 9000 pro 128mb w/ dual head.  Ubuntu's Screen and Graphic program DID show 2nd monitor setting.  I haven't use it but It'll works. Cuz it show resolution setting on 2nd monitor are adjustable (I did played with it and it did drop down lists of resolutions..

Sometime you might have to download display driver from either Synapic package or Add/Remove to resolve problem.  It may screw up your Xorg unless you delete old display driver for new one. IF you are brave enuf to do it.  That's fine.  Or if you have 2nd hard drive that you don't care to use.  Then install same Ubuntu and play around with it (like stuck knife into it's gut and twist it LOL).  If you figure out right driver and fixed it to get 2nd monitor working,  then switch back to your original hard drive and do what you did on 2nd drive. You might want to make note what you did in case...  This would be my suggestion.  Don't blame me for screw up....

((( I have 3 hard drives with 3 different Linux distros., I swaps around hdd until I found what I wanted.  It's Ubuntu which is the best distro I've use cuz it's easy to configure and fix....  Linux Mint (base on Ubuntu) seem missing several important function that I needed to use like Virtualbox don't run at all after installation...  I've tried OpenSuSE 10.3, nice but didn't like it cuz it's kinda wussy. and it's Adept manger seem flaky....  I've had install and mess with many more Linux distro before Ubuntu.. So that's why I avoided screw ups on first hdd by using 2nd hdd to screw around Ubuntu to find out what it does LOL))) 

Thanks
Catty

---

### Post by gubemton on 2008-03-13
> **Purplecatty said:**
> You will need to log off and on after you set the screen resolution. OR another option.  Go to "System--Preference--Screen Resolution" and this program should be able to change resolution immedialy after you select it.   Oddly,  two different program, Screen and Graphic (in System--Administrator--Screen and Graphic) and Screen Resolution don't function the same but if you use Screen Resolution and change resolution,  the set Resolution you already chosen will already shown in Screen and Graphic box.  

I find it funny tho. IF you use Screen and Graphic to change resolution, log off and log back on.  But if you reboot the system. It'll switch back to preset resolution which is annoying.  

If you use Screen Resolution,  you will see the radio button to checkmark as "Make default for this computer ("your username"-desktop) only".  This will "lock" the resolution for your username only.  But if you play game or run the apps that use full screen,  close the apps and screen went back to old resolution.  Use Screen Resolution to switch back your resoultion. 

 I haven't figure out how to prevent resolution going back to old level.  I'm still a noob tho.  I even tried edit Xorg.conf file (type in terminal "sudo nautilus" and navigate on Root files (Root drive) to ETC/X11 folder which is easier to edit and save in GUI than typing all commands on Terminal)  and deleting some resolutions so it won't fall back to old one.  I saved it and test it, it still falls back to old resolution. I'm frustrated tho.  I'm still searching through Google. I even left thread in blog and no one have come up to offer "fix it and shutup" solution for me.

I hope it works for you.
CAtty:lolflag:

I have the same problems well stated here. Every problem stated is somethig I can completely relate to. What gives? Why is it that distro after distro, I have this same problem!? I tried Linux-Mint and I also have the same issue w/ 2 different types of desktop machine, and my laptop. This is clearly buggy as hell and yet nobody cares!? I'll reboot and then all-of-a-sudden I'm at 800x600. My laptop is 1920x1200. Currently in "SCreen Resolution" all that's offered is up to 1600x1200 though it actually sets it to 1024. SCreens agn Graphics won't load now. And just now when i tried opening it, it killed the x server and i lost all my work. THen the annoying nvidia (GeForce 6800 Go card in this laptop) screen appears from their proprietary drivers, then the login prompt is at a really small resolution (could tell, 640x480?) and the text is set to 1p or something. I just see anti-aliased scribbles of 2x in width. WTF?! Sorry, this is so frustrating right now for me. I'm really trying to give open source stuff a shot but nobody is trying to help me on this issue for months after being polite on other forums etc before. I'm at my wit's end!!

---

