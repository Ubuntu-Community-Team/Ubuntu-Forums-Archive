---
title: "[SOLVED] Screen resolution mess!"
date: 2007-11-24
forum: General Help
---

### Post by valleyman7 on 2007-11-24
I messed up my screen resolution so bad that I am not able to make any changes. Is there a restore feature for Ubuntu 7.10?, Or a way to access the settings as with windows by starting in safe mode?. Or do I need to format and re-install. My graphic card is the Nvidia GoForce Go 6800. I have  the Nvidia Linux drivers installed and I was trying to set up to use my TV for a second monitor to watch movies.    I was careless and made the wrong settings.:confused:

---

### Post by skymera on 2007-11-24
try

sudo dpkg-reconfigure --phigh xserver-xorg

---

### Post by valleyman7 on 2007-11-25
I thought I had posted a question last night but I don't see it so I guess I will try this again. I cannot get to terminal as my resolution is messed up so I can't run any commands It looks like if there is no way to go back and restore I am sol. I never did a back up or an image as I am still trying to learn. If you have any suggestions I would appreciate them. :mad: at myself.

---

### Post by 81wtbvi02 on 2007-11-28
Do you see a kernel menu when you boot, with an entry like this:

Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)

If so, choosing that should get you to a command prompt, where you can try skymera's solution.

Good luck!

---

### Post by valleyman7 on 2007-11-29
I don't recall having any options other than logging options. I have never paid attention although it seems like there are none. When I boot to Ubuntu I think it goes right to a log in screen. I will check and see. I don't have dual booting. I swapped my laptop hard drives and installed Ubuntu so now Ubuntu resides on an external drive. So when I want to boot to Ubuntu I select boot to my USB enclosure. I will post back when I check to see if that is an option. Thanks for all the help.

---

### Post by valleyman7 on 2007-12-01
I am able to get to a menu by hitting escape when I first boot, but I didn't print out the instructions so I could try and configure my video settings. So I now have printed the information and will try again. I will hopefully be able to post some positive progress soon. :)

---

### Post by valleyman7 on 2007-12-01
Well I guess I did it now. I was able to get to the menu and once there I wasn't really sure of what I should do. I had several options for Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) So I decided to go to the earliest entry and choose it. After awhile I was at I guess was a command prompt. Well I entered several things like my password, username and nothing worked. I didn't print out the instructions that I was given so I didn't have a clue what I was supposed to type in on the cmd line. I did type exit just as a guess. Well I guess it was WRONG! now when I try and boot to the USB drive for Ubuntu all I get is Disk Error and hit any key to continue which just boots to XP. So I will wait a few days before I format and install Ubuntu again. I was hoping to be able to save this OS as I had a real hard time getting some non Linux programs to work, and I don't recall what I did before. So I will wait awhile to see if anyone has any suggestions. TIA:confused:

---

### Post by valleyman7 on 2007-12-02
:(Gave up and formated the drive. I tried to install to the USB port and I believe it was having a problem as it seemed to be stopped at 15% for about 20 minutes. Maybe I need to see if Ubuntu will install to a USB drive direct. I think that was the reason I swapped drives and installed the OS on the drive and then booted to the USB drive. So back to the drawing board. I would like to thank all for their help. I will be back as I am not ready to give up yet. :confused::confused:

---

