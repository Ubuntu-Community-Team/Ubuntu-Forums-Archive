---
title: "mac-style menu removed my main panel and i need help getting it"
date: 2008-05-20
forum: General Help
---

### Post by dazift on 2008-05-20
this is the last ditch effort before i uninstall xubuntu completely so i am in need of help. last night i tryed to install mac-style menu and everything seamed to be going ok and the instructions said to reboot and i did, xubuntu took a long time to shutdown and when is started again i could not find my panels. i tryed going into terminal using ALT-F2 and typing metacity --replace and it said metacity was no longer installed so i tryed to reinstall it and it said it had globalmenu (mac-style menu) as a dependency so i was forced to delete that pkg and reinstall metacity. everything went ok when i tryed to install metacity the second time. so i typed metacity --replace and matacity started running and shut down compiz but i still cant find the panel, any ideas?

---

### Post by bobjenkins on 2008-05-20
I am a noob so this answer probably won't suffice.

Could you make a new panel and add all the stuff the original had? I don't know how to do it but you might:) 
Also another noob response, could it possibly be overscan issues? (the bars are on off edges of screen
Sorry I don't know much about linux, Goodluck though

after doing a bit of searching I found this 

> I've had a similar problem with the new 8.04. I did not have either the top panel or bottom panel in Xfce4 after a bad Firefox crash (don't know why).

I did however have the floppy drive, trash, home & file system icons on the desktop. If you have this, go into the File System/usr/bin and find xfce4-panel and simply double click on it. It will run without the aid of the terminal screen - hence no terminal screen to close and kill the panels. Make sure to change your logoff settings to save the current settings on exit. It worked for me and I hope it works for you.
If you dont have any icons on desktop and you can get to the terminal type nautilus to open a window (just found that out today:)

---

### Post by morgengenuss on 2008-05-21
just to be clear: the title of your thread suggests that you use xfce while the rest of the thread seems to refer to gnome. what's up with that?

---

