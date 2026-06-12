---
title: "Beryl will not start..."
date: 2006-10-21
forum: General Help
---

### Post by krazed nun on 2006-10-21
When ever i try to start beryl through the terminal (since it wont start on its own) i get this:

```
cow@bleek~$beryl
XGL Present
beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display localhost:1.0
```

i have ATI mobility radeon 9200 and beryl worked for the first few tries, but then it died. please help.:(

---

### Post by StreetSmart on 2006-10-21
I know alot of people having this problem. I am as well. I have not found any kind of fix for this. I can get beryl to start by clicking beryl icon and reloading the windows manager. Beryl stops after a while tho.

---

### Post by cmost on 2006-10-21
Are you guys using AIGLX with Beryl, or XGL?  I would suggest you use XGL as the accelerated X server.  From what i've been reading, AIGLX with ATI (especially the latest driver) is still quite buggy by many accounts.  Try to setup Beryl with XGL and see if you have better luck!  Cheers!

---

### Post by krazed nun on 2006-10-21
i think i am using XGL, i dont really know. is it possible to switch from XGL to aiglx or vice versa without losing anything important? anyways, wut is this 
"GLX_EXT_texture_from_pixmap" thing?

---

### Post by cmost on 2006-10-21
"GLX_EXT_texture_from_pixmap" is required if you're trying to run Beryl on AIGLX.  Since the current stable nVidia and ATI drivers lack GLX_EXT_texture_from_pixmap, XGL is preferred for users of these cards as GLX_EXT_texture_from_pixmap values are taken from MESA instead of the native card drivers.  The newest beta driver for nVidia cards does, at last, support GLX_EXT_texture_from_pixmap, however, the latest ATI driver does not.  Video cards that have open source drivers, such as SiS, Intel and others already support GLX_EXT_texture_from_pixmap and are therefore well supported when Compiz/Beryl is used with AIGLX.  If you upgraded to Edgy Eft, it's possible you switched over to AIGLX inadvertently, as Edgy comes with a version of X.org that has AIGLX built-in and enabled by default.  While you may still have XGL installed, the upgrade may have overwritten custom config files that tell the system to use XGL accelerated X server.  I am not personally using Edgy, so I cann't speak to whether or not this can happen.  I wish you luck!

---

