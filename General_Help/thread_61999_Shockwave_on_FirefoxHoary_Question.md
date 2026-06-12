---
title: "Shockwave on Firefox/Hoary Question"
date: 2005-09-03
forum: General Help
---

### Post by Joey French on 2005-09-03
I need shockwave in order to do homework for classes. I know, it's stupid, but I have to access online stuff from home. So, I installed firefox for Windows under Wine, and then installed the Shockwave plugin, worked like a charm. Only problem is, I can't call it up when I need it, cause I don't know the command. Nor was there an icon added anywhere that i can click. Please, can someone tell me the shell command for firefox under wine would be, or how to add an icon for this application? I will have to use this rather arduous fix for the foreseeable future. I would use smeg to add a wine tab to the menu bar, but I don't know what to add...

Thanks!
Joey

---

### Post by sethmahoney on 2005-09-03
Try:

wine "/home/YOUR USER NAME/.wine/drive_c/Program Files/Mozilla Firefox/firefox.exe"

---

### Post by Joey French on 2005-09-03
Cannot find? 

How about a lib I can add to the menu bar?

---

### Post by sethmahoney on 2005-09-03
That should work.  Did you replace "YOUR USER NAME" with your user name?

---

### Post by Joey French on 2005-09-03
yes. I don't know if the path pointed to my wine directory.

---

### Post by Joey French on 2005-09-03
Okay, so I have toyed with it, and navigated to the folder with the firefox.exe in it, and the path is /home/joey/.wine/fake_windows/Program Files/Mozilla Firefox/Windows Firefox.exe, but when I try to run it, I get this:

joey@homebox:~$ home/joey/.wine/fake_windows/Program Files/Mozilla Firefox/Windows Firefox.exe
bash: home/joey/.wine/fake_windows/Program: No such file or directory
joey@homebox:~$

Am I on the right track, or am I doing something completely wrong?

---

### Post by az on 2005-09-03
[QUOTE=Joey French]Okay, so I have toyed with it, and navigated to the folder with the firefox.exe in it, and the path is /home/joey/.wine/fake_windows/Program Files/Mozilla Firefox/Windows Firefox.exe, but when I try to run it, I get this:

joey@homebox:~$ home/joey/.wine/fake_windows/Program Files/Mozilla Firefox/Windows Firefox.exe
bash: home/joey/.wine/fake_windows/Program: No such file or directory
joey@homebox:~$

Am I on the right track, or am I doing something completely wrong?[/QUOTE]


Linux filesystems do not handle spaces.  Use quotes:

wine "/home/joey/.wine/fake_windows/Program Files/Mozilla Firefox/Windows/Firefox.exe"

---

### Post by Joey French on 2005-09-03
Okay! Got it. Now to only be able to add a launch icon, and i will be set.

Thanks for the help!

---

### Post by sethmahoney on 2005-09-07
If you're adding a desktop icon, right-click on the desktop and click "Create Launcher".  It should be easy from there.  Adding a panel icon or a start menu icon should work similarly.

---

