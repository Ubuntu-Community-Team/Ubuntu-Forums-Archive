---
title: "Integrated VIA S3 KM400 and Desktop Effects"
date: 2008-05-09
forum: General Help
---

### Post by Aleksandar_M on 2008-05-09
Hello,

I have ubuntu, so I am interested for compiz fusion. Can I enable it ? Did anyone try it on this video card? UnichromeVIA driver or Openchrome driver is better?

---

### Post by Metaleks on 2008-05-24
I don't think you can run Desktop Effects on that video card.  Sorry! :(

[Here](http://ubuntuforums.org/showthread.php?t=445128") is a similar thread.  To summarize, it would seem that the VGA adapter doesn't support per-pixel shading, which is needed for Desktop Effects.

(ps, on a completely unrelated note: we share the same name Aleksandar!  Even the first letter of your last name, lol.)

---

### Post by Forlong on 2008-05-24
You won't be able to get Compiz to work on a via chip atm -- in fact, the openchrome driver might kill your X server if you try -- but via announced they will be going open source with their drivers, so you might be able to use it in the future.

---

### Post by klange on 2008-05-24
> **Metaleks said:**
> [Here](http://ubuntuforums.org/showthread.php?t=445128") is a similar thread.  To summarize, it would seem that the VGA adapter doesn't support per-pixel shading, which is needed for Desktop Effects.

Per-pixel shading is not needed. None of the drivers out there for the various VIA chipsets properly support GLX_TEXTURE_FROM_PIXMAP, and so will not work. Hopefully this will get added in to VIA's own drivers...

---

### Post by Metaleks on 2008-05-24
> **WindowsSucks said:**
> Per-pixel shading is no one needed.
My apologies for misinterpreting the thread I linked to.

---

### Post by ShodanjoDM on 2008-05-24
You still can get beautiful effects like transparency and drop shadows with VIA cards, although without 3D effects. Just install:

```
sudo aptitude install xcompmgr
```

after that:

```
man xcompmgr
```

for the settings.

---

### Post by Forlong on 2008-05-25
xcompmgr is pretty much obsolete since Hardy.
Just run this command in a terminal to enable the compositing manager integrated in GNOME:
```
gconftool-2 -s -t bool /apps/metacity/general/compositing_manager true
```

---

### Post by techgs on 2008-05-25
ITS NOT TRUE.  YOU CAN ENABLE DESKTOP EFFECTS WITHOUT ANY ISSUE.  ONLY THING YOUR REQUIRE SOME MANUAL TWEAKING.

CURRENTLY I AM USING 3D EFFECT WITH A SMALL GLITCH THAT MY CURSOR IS ONE BOX AND AM NOT ABLE TO CHANGE IT.  THE CURSOR IS ACTUALLY A SMALL BOX CONSISTING IMAGE OF MY CURRENT DESKTOP.

I AM USING UBUNTU 8.04 + 512 MB RAM [SHARED 64 MB FOR VGA ]

DRIVER IS VIA CX700 and CN700 Linux Graphics Drivers For Ubuntu8.04 LTS 

          Version 5.73.21.83-40692  Release, 30th April 2008

Installation and Uninstallation
===============================
1. How to Install/Uninstall the via Linux Driver 

   1.1 to uncompress the via driver package

         tar zxvf ./via-unichrome.83.40692.tar.gz

   1.2 to install the driver

         cd   ./via-unichrome.83.40692

         sudo ./vinstall

   1.3 to uninstall the driver

         cd   ./via-unichrome.83.40692
         sudo ./unvinstall

2. How to enable 3D desktop effects / Compiz after VIA driver has been installed

   2.1 edit the compiz script file

         sudo vi /usr/bin/compiz

   2.2 find the line

         WHITELIST="nvidia intel ati radeon i810"

   2.3 add “via” to the list to make it

         WHITELIST="nvidia intel ati radeon i810 via"

   Save the file.
Restart the system.

Even the cursor disappers do not get fainted. [ For silly reason it disappers - reason unable to find. ]  Infact you will find that even if you do not see the cursor, still you can access Menu and enable the desktop effect System--->Preference --->Appearance  -- in the last tab [ Visual Effect ]you enable the maximum effect.

Voilla...

The you can do Advanced desktop effect setting from Setting-->Preference.

In fact i am running awn and every thing I tried and it worked beutifully  including 3d cube.  I never imagined.

Good luck....:guitar:

---

### Post by Forlong on 2008-05-26
That's great to hear, techgs!

Could you do me a favour and post your output of this: [http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)
I would really appreciate it. Thanks in advance.

---

