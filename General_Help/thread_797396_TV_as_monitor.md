---
title: "TV as monitor"
date: 2008-05-17
forum: General Help
---

### Post by Griffi09 on 2008-05-17
So i'm trying to pull away from windows, but on my entertainment PC i'm having some difficulties.  I use xp and an ati radeon HD 2400 card.  This has an HDMI output that goes to my 44in LG as the only monitor.


So i run ubuntu 8 desktop cd, in safe graffics mode usuing the vga on the card, i can get another monitor to display the desktop.  But nothing on the 44in.  From what i've seen so far i think i need to alter the xorg.conf file, but how?  Anyone with any experience trying to do a similar conf?


Thanks

---

### Post by yoda2031 on 2008-05-17
I managed to get a 32" HDTV to display up to 1024x768 with a standard monitor cable.  Further than this, my HD experience is limited.

That said, I'm going to try to help anyway.

If it's xorg.conf you need to edit, you'll need a Screen section first of all for your TV.  It should look something like this:
```

Section "Screen"
        Identifier      "My 44 Inch Beast"
        Device          "ati radeon HD 2400 (fglrx)"
        Monitor         "IDKWGH"             # I don't know what goes here
        Defaultdepth    24                   # again, TV-specific
        SubSection "Display"
                Modes           "1024x768"      "800x600"       "640x480"
# change the resolutions to your desired resolution on the screen
        EndSubSection
EndSection

```

Please don't take this as read, though, I'm not an expert so you should wait for someone else to post really.  I just know that the above section is the part of xorg.conf that defines what your monitor is capable of (afaik...).

---

