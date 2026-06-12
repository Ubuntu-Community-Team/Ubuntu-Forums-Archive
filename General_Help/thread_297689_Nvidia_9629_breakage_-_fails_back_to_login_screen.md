---
title: "Nvidia 9629 breakage - fails back to login screen"
date: 2006-11-11
forum: General Help
---

### Post by smeager on 2006-11-11
I recently tried to install the latest Nvidia Driver 9629 and everything went fine (even the pretty new splash screen). I had happy Nvidia goodness.

I thought everything was good to go but then I tried to play Quake4. Big mistake. Upon launching the game the system fails and loads back to the login screen. This happens with any 3d game I try to play (UT04, Fizzball, Flatout via Cedega, etc... while trying to play in fullscreen mode). Everything else works fine though.

I didn't have this problem with the 9625 and 9626 beta drivers (everything ran fine). Since I like playing my games (during work breaks ;) ) I ended up reverting back to the 9626 beta.

Is it a problem with the official 9629 driver? If not and its a user problem, can you explain to me how to fix it?


Current Hardware Setup:
Dell Inspiron 9300
1 GB RAM
80 GB HD 
Nvidia Geforce Go 6800 w/ 256MB 
Pentium M 1.8

Thank for any help.

---

### Post by digby on 2006-11-11
I had a similar issue w/ 9629.  Any 3d accelerated app that I tried to run would segfault.  I too fixed it by reverting to the beta driver.

I've heard this is a bug with legacy cards (I have a Ti4800), but I wouldn't expect that your 6800 would fall in that category.  If you ever feel like experimenting, reinstall 9629 and see if glxinfo crashes.

---

### Post by PriceChild on 2006-11-11
Seen as you were happy using the beta 96**, you may like to follow a guide in my sig for the beta 97** drivers... Couldn't hurt. Just make sure you have 9625 around to reinstall from the cli if something goes wrong :)

---

### Post by smeager on 2006-11-11
Well I re-installed 9629 and ran glxinfo and it didn't crash. It seems to only crash when I try to run 3D accerlerated apps. Oh well. 

I'll try Price's 97** driver how-to to see if anything happens. If not I'll just revert back to 9626 and be happy with that.

Thanks for the help.

---

### Post by soze on 2006-11-13
9629 is broken for sure.

Same problem here on my 6600 GT (w/ TwinView)

Reverted to 1.0-9625, all is well.

---

### Post by mock_alien on 2006-11-19
Hi!

i actually managed to get **Doom3** working with the new driver.
the problem is that i can't remenber what i did to fix it.

Any way, i downloaded the sh file nvidia (i'm using (amd64) and followed the instructions. (driver installed ok)

then as i wanted to use beryl. i followed this one:

[http://www.ubuntuforums.org/showthread.php?t=263851&highlight=beryl](http://www.ubuntuforums.org/showthread.php?t=263851&highlight=beryl) 

any way, to my surprise doom3 started. AS i now want quake4 to start the same way i need help to figure out what i did.

One thing i can remember is that i change the resolution to the same as the desktop (1600x1200)  PRIOR upgrading the driver.

(i also tried to change the quake4 config file to force it to start in windowed mode, but i get a script error instead - maybe i didn't installed quake4 properly) but i haven't got it working yet...

> anyway *UNCONFIRMED* change the resolution of the fullscreen games to the same as the Desktop BEFORE upgrading the nvidiadriver.

would be cool if it would work...

---

### Post by MrMela on 2006-11-19
[1.0-9629 crashes X when trying to play games]("http://www.nvnews.net/vbulletin/showthread.php?t=80676")

Conclusion... 9629 not working with DFP, 9742 not working with Wine and OpenGL, and last working driver for me is 9625.

Hope this helps someone... ;)

---

### Post by mock_alien on 2006-11-19
HOW it works

example

quake4 +set r_fullscreen 0

(the same goes for doom3)

(then a windowed version start-> you can play OR you can select another resolution in fullscreen) (i choose the same resolution as my desktop)
and Behold! it WORKS! I've tried it ,the only thing i say was some corruption on the menus.

so 9629 Works, althou not perfect but until its fixed use this workaround in the meantime.
(Nvidia says that it will be fixed in the next release)

now, how do i make enemy teritory windowed?

---

