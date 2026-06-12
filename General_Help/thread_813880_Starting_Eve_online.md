---
title: "Starting Eve online"
date: 2008-05-31
forum: General Help
---

### Post by oscar2296 on 2008-05-31
Hi, I am having problems running eve-online on my ubuntu laptop. The official linux cedega version does not start at all, it crashes after the splash screen. So I thought I'd try the windows version in wine. 

I get it up running, but when i get to the login screen, I cant scroll down the window that says: "Scroll down to continue." 
Without being able to scroll down, I can't login. Any suggestions?

---

### Post by shifty_powers on 2008-05-31
what version are you trying to run?

---

### Post by shifty_powers on 2008-05-31
also see

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=9971](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9971)

and look through the bugs ;)

---

### Post by oscar2296 on 2008-05-31
The version of Eve is 4.12, I think. 4.12.something. 
Version of wine is 0.9.59

I did not find any useful help on the linked webpage.. :/

---

### Post by shifty_powers on 2008-05-31
well, first of all, you can upgrade wine, it is a couple of versions out of date. In fact 1.0rc1 is now available.

and:

> If it doesn't work you might want to start with a new ~/.wine directory.

- run "wine winecfg" to setup/configure your wine install (mainly sound driver)
- you can copy the Eve folder into ~/.wine/drive_c/ or install from scratch. (try without the cache folder first)
- copy arial*.ttf to ~/.wine/drive_c/windows/fonts/ (install ms corefonts package and then search for arial*.ttf on your disk)
- install the d3d9x_35.dll by running the RedistD3DXOnly.exe in the bin dir

If Eve crashes/hangs after the character selection you need to add "voiceenabled=0" to ~/.wine/drive_c/windows/profiles/username/Local Settings/Application Data/CCP/EVE/settings/prefs.ini. This is needed if you have a voice enabled account or try to test on Singularity when voice is enabled there.

You can try disabling sound in either prefs.ini or via the sound driver in winecfg

You should set OffscreenRenderingMode to fbo. Run "wine regedit" to edit the keys, which are listed on the wiki.

 

Also disable shadows ingame.

Try adding '87.237.39.200 localhost' to your /etc/hosts if you get random crashes.

and

> Hi pilot,


You may copy arial.ttf to /$HOME/.wine/drive_c/windows/Fonts

The font can be downloaded from web.archive.org/web/20000420210719/http://www.microsoft.com/typography/downloads/arial32.exe

1) $ wine arial32.exe

Thats all =)...

Fly safe

from that link may help ;)

---

### Post by ex.hav0k on 2008-06-27
what graphics card are you using?

---

