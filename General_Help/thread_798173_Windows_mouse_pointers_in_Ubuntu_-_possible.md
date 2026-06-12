---
title: "Windows mouse pointers in Ubuntu - possible?"
date: 2008-05-17
forum: General Help
---

### Post by Thanh-BKK on 2008-05-17
Hi :)

I have a set of Windows mouse pointers that i used under XP and Vista, they are themed and animated and i like them very much.

Is it possible to use these in Ubuntu (Hardy 8.04 here)? 

The files are .cur files, when i try to open one in Ubuntu it tells me that "there's no application installed for this file type", so i guess i need to convert them somehow... .how?

Please help me out... i really love those :)

With kind regards......

Thanh

---

### Post by mmb1 on 2008-05-18
There's a package available in Synaptic, called "icoutils", that you may want to take a look at.  It can convert these files to a format Ubuntu can work with.  I'm not sure how to set them up as your pointer though, that's up to you.

---

### Post by Thanh-BKK on 2008-05-18
Hello :)

Thank you for your reply. I have downloaded and installed that, however i can't find it anywhere? It's not showing up in "Applications" or "Administration" or "Preferences", and neither in the right-click menus. 

Trying to open one of the ".cur" files with the command "icotool" (as described in Synaptic) does nothing at all, and trying to run either command (icotool, wrestool, extresso) only yields a complaint "missing argument". Trying it with "sudo" or "gksudo" again does nothing at all.

Do i need something else to get this program working?

Appreciate any help - thanks in advance :)

Your Thanh

---

### Post by mmb1 on 2008-05-18
See if this works, the package shouldn't show up in your applications, it should be installed by default, I think.  Try to use your pointer files by going to system-preferences-appearance-install.  Find your files and click open.  Then, under the appearance main window press, customize, go to the pointers tab, and see if yours are there.

If this doesn't work, please tell me so we can work this out.

Good Luck!

---

### Post by Thanh-BKK on 2008-05-18
Hello :)

Unfortunately that doesn't work out either - if i select "install" via that way, it will only accept a "theme file" which i don't have to begin with.

However by now i managed to convert my ".cur" and ".ani" files into ".png" ones, so i have the "building blocks" to actually make it a theme file. 

I just have to find out how :)

With kind regards....

your Thanh

(PS i converted those using a Windows app..... i know, i know, but it works in Wine..... i couldn't figure out any other way, and Gimp also doesn't like .cur and .ani files....)

---

### Post by mmb1 on 2008-05-18
Glad to hear you're making progress, and I'm no Windows hater, do what you must to get the job done.  :)

---

