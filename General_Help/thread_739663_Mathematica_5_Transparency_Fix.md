---
title: "Mathematica 5 Transparency Fix"
date: 2008-03-29
forum: General Help
---

### Post by howardjd on 2008-03-29
Just trying to offer some help regarding text transparencies in Mathematica 5.

There were several UF members who described this issue on irrelevant threads.
  **This post does not pertain to locale/XKeysymDB-related problems!
     {effective-solution ([here]("http://ubuntuforums.org/showpost.php?p=496021&postcount=2"))}

I assume Mathematica was correctly installed and the GUI loads with transparent text. The Splash-Screen, notebook sheets, toolkit, and preference window each exhibit this pervasive effect. I believe my solution can be helpful to Ubuntu users running Compiz-style graphical layers. Several users proposed disabling Beryl or Compiz while running Mathematica. I find this to be excessive as the software appears fine when configured for a standard color map.

FYI: UF member ravenon posted a quick fix by passing the -defaultvisual parameter while launching Mathematica, {([here]("http://ubuntuforums.org/showthread.php?t=710418"))}

***
**My Solution** (one-step)
_Simply_, uncomment **standardColormap: RGB_DEFAULT_MAP* in the *XMathematica* config file. >> See below for instructions.
  (see, that's not nearly as painful as halting beryl/compiz ;D.)
***

**Quick how-to:**
_Less simply_, this requires root file permissions and the file is buried in folders.

  `Find XMathematica, it's general location is given in the following form:
   <YourMathematicaFolder>/SystemFiles/FrontEnd/SystemResources/X/XMathematica.
      Default Mathematica path is similar to- /usr/local/Wolfram/Mathematica/5.1

  `Open XMathematica for editing:
     run: $ sudo gedit XMathematica

  `Find "!*standardColormap: RGB_DEFAULT_MAP"
      (searching for ": RGB" finds the right line.)

  `Uncomment "!*standardColormap: RGB_DEFAULT_MAP"
      (remove the "!".)

Save, exit then load Mathematica!


**Important note: I am currently running Slackware 12.0 with composite-enabled nVidia graphics drivers, however ran into this problem on my Ubuntu systems in the past. I aspire to spare someone an avoidable headache, so let me know if this helps or if this post requires any revision.

---

