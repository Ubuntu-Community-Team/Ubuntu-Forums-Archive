---
title: "Serious Malfunctions-Caused by Widescreen?"
date: 2007-12-25
forum: General Help
---

### Post by dph948 on 2007-12-25
So, it seems that there are a number of people with issues getting widescreen monitors to work in Ubuntu.  I feel this deserves its own thread since the consequences of my installation attempt have been unusually severe. My apologies for long windedness, but this way I won't miss anything that could be of value.

For most of my time using Ubuntu (about 3 months, though I still don't do much command line stuff), the computer has been significantly superior to its Windows-running neighbor (my sibling's), even though the Windows comp. is significantly stronger in hardware terms.

However, we both received Acer AL1716W widescreen monitors.  His went in without a hitch.  At first, mine said "Input not compatible."  Eventually, I managed to get some responsiveness.  The screen would function normally until the ubuntu logo and orange loading bar appeared.  Once it was finished loading the message reappeared.

-Further research has lead me to conclude that the initial error message was due to my graphics card (I assume a 16MB ATI Rage 128 Ultra), was not compatible with the screen sizes, and Ubuntu was not at fault at all.

Alternating between old and new monitors, I tried adjusting my resolution to 1440*900, and got the new screen to show the desktop.  However, it was frozen.  I reset the resolution to 1024*768 with the old monitor, and restarted, planning to reattach the new monitor.

However, when I did restart the computer, all I got was a blast of the fan, two angry beeps, and a monitor that was stuck in powersave mode (screen off, orange power light).  This occurred with both monitors.

After several tries, and at my wits end, I tried inserting the LiveCD, if only so I could access the ability to reset screen sizes.

The (old) monitor immediately emerged from power save mode, and went beserk.  The screen began flashing a multicolored, flickering, changing display (mainly lots of lines, though sometimes a more blockish arrangement, largely orange and green, though black, white, and red were also common).

I am completely lost and confused, scarcely more than a Linux newbie and now I have a psychedelic screen of death.

The main questions I need answers to are:
1) How do I restore basic functionality?
2) Once functionality is restored, is there a workaround to the monitor-graphics card issue (this is by far the secondary priority)


Thank you for your help (and Merry Christmas to those who celebrate),

dph948
Puzzled Newbie

EDIT: Changed most likely graphics card

---

### Post by TidusBlade on 2007-12-26
If you want to restore basic functionality, you probably have to reset your resolution to something your graphics card can handle. So start up in safe mode or in terminal mode.
So firstly, at the GRUB screen press CTRL + ALT + F, and login, probably under root. 
Firstly type "sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup" to back it up just in case.
Then type "sudo nano /etc/X11/xorg.conf" which will open up your Xorg config (Graphics configuration) file in Nano, the terminal text editor. And look for this (this is how mine looks like):
```
Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation G70 [GeForce 7600 GS]"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        SubSection "Display"
                Depth   24
                Virtual 1280    1024
                Modes           "1280x1024@60"  "1280x960@60"   "1024x768@60"  $
        EndSubSection
EndSection

```
And now change it to something your screen can handle. 
Depth would be how many colors, like 16 would be like ~65K colors and 24 would be ~16M colors. Virtual is just your resolution at boot I guess and modes is probably resolution + Refresh rate. So maybe add your prefrence there?

As for your second priority, your graphics card looks abit old so I dont think it will support your preferred resolution, unfortunetly, that means having to get another ones, or hopefully someone else knows something.
Hope it helps :)

---

### Post by dph948 on 2007-12-26
Thank you for that information.  However, I cannot get to the GRUB loading screen.

When powering up as I normally would, the computer immediately gives three short beeps, puts the monitor into powersave mode, and beeps twice.

When inserting the LiveCD, I get the aforementioned crazy display of colors.

Also, this is on Gutsy (I failed to mention that earlier)

---

