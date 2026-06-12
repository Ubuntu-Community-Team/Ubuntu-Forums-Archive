---
title: "Aptitude Errors"
date: 2006-11-09
forum: General Help
---

### Post by Scheater5 on 2006-11-09
Running ```
aptitude upgrade
``` yields this same error message everytime 
```
X Error: BadDevice, invalid or uninitialized input device 155
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

```

Should I be worried?  It never seems to have an effect.

---

### Post by Sef on 2006-11-09
Sudo is needed before aptitude.  Do an update before the upgrade.

```
sudo aptitude update
```

```
sudo aptitude upgrade
```

---

### Post by Scheater5 on 2006-11-09
Yea, I just left out sudo - which, speaking of which, that kinda seems to be par-for-the-course on message boards, so I just "did as the Romans."  Is that bad etiquette? 
But, anyway, if I had left out sudo, I would never have even gotten to the error messages, because it would just reject the request.  Running aptitude is successful, actually I get the same message anytime I run aptitude, and no matter what it still (at least seems) successful.

---

### Post by dannyboy79 on 2006-11-09
i don't think that;s a aptitude error since it states X error. i may be telling you that your X server is trying to open something and it's failing, also, the previous person is correct. since update and upgrade are admin things, you have to run them with root privalages and that's done by adding sudo in front of the command, then enter your password when it asks for one. i would look into that error as maybe an X error, what does your Xorg log show, if anything weird. i could be wrong, but it does say X error

---

### Post by Scheater5 on 2006-11-09
An X server error?  Seems reasonable enough - I had kind of suspected as much.  And I'm familiar with root privileges.  As I said, I just left it out (as well as the update, which I also do prior to running upgrade) because I'd come to assume this was customary.  At this point I'm beginning to this this was incorrect.
Anyway, back to the task at hand.  When you say Xorg log are you just talking about finding anything "weird" in Xorg, or is there a command to see an Xorg log?

---

### Post by Sef on 2006-11-09
> Yea, I just left out sudo - which, speaking of which, that kinda seems to be par-for-the-course on message boards, so I just "did as the Romans." Is that bad etiquette?

It's better for it to be put in because some people may not realize that sudo should be included.

---

### Post by dannyboy79 on 2006-11-09
if you are using ubuntu, then there is a log viewer under system i think, or maybe it's under accessories, I forget, but there is a log viewer within the pull downs somewhere, then click open, then navigate to /var/log/ then look for xorg or Xorg and open it, see if there is anything that is telling you about an error?

---

### Post by Scheater5 on 2006-11-10
I probably should have specified that I use Kubuntu, but no worries, I found the file itself.  I'm afraid most of it goes a bit over my head (although I can figure out what most of it means, it's quite a bit of information to go over bit by bit when you don't entirely understand it to begin with).  

I did manage to find these error messages 

> (WW) Warning, couldn't open module v4l
(II) UnloadModule: "v4l"
(EE) Failed to load module "v4l" (module does not exist, 0)
> 
(II) fglrx(0): Composite extension enabled, disabling direct rendering
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

> 
(WW) fglrx(0): Failed to set up write-combining range (0xd3000000,0xfe0000)
(WW) fglrx(0): Failed to set up write-combining range (0xd2000000,0x1fe0000)
(WW) fglrx(0): Failed to set up write-combining range (0xd0000000,0x3fe0000) 

> Could not init font path element /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType, removing from list!
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!

However, no mention of a "device 155"

---

