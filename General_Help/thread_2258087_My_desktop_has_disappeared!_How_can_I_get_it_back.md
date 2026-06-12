---
title: "My desktop has disappeared! How can I get it back?"
date: 2014-12-24
forum: General Help
---

### Post by rdh61 on 2014-12-24
Hi,

I use Lubuntu 14.04 LTS. I was using the computer this morning. It worked. I didn't do any updates. I turned it off. I turned it on this afternoon. I log in. I get the blue Lubuntu 14.04 wallpaper, but I can't see my files or the menu bar. Right click produces nothing. Control + Alt + T doesn't give me a terminal. Guest account is the same. I am writing this on dual boot Windows XP. How can I get my desktop back?

Many thanks and Merry Christmas!

---

### Post by phidia on 2014-12-24
You can try booting in recovery mode see [this]("http://askubuntu.com/questions/150367/how-do-i-boot-into-recovery-mode"). It sounds like your DE desktop environment isn't starting.     [This site]("http://wiki.lxde.org/en/Ubuntu") could be helpful too.

---

### Post by Kurt_Alan on 2014-12-24
@phidia and @ The Ubuntu gods

I just returned from Xubuntu 14.10 to 14.04 for the sake of stability, since my problems with 14.04 were beginning to add up.  Now my desktop also disappears in the "stable" LTS version! What the hell? This has never happened to me.  So I am now following this up.  I have a new install. I'd rather spend extra time fixing the problem than re-installing at this time so that I can learn how to fix the problem in case it happens again!

BTW, for anyone following the Dropbox indicator fail saga, this critical aspect of Dropbox, which is necessary to access the menu preferences and powerful options such as "selective sync," fails equally on Xubuntu a14.04 and 14.10.  I received a response from my trouble ticket to dropbox.com that their engineers are aware of the problem and are working on a fix.So the problem is at their end and in their Linux implementation.

This is not a rant. Just a AAAAAAAArrrrrrgh! Merry Christmas to all . . .

---

### Post by Holger_Gehrke on 2014-12-24
Try going into one of the virtual Terminals (Ctrl-Alt-F1 ... Ctrl-Alt-F6, Ctrl-Alt-F7 returns to X). You can log in there and should get a shell. You can now look in the various log-files to find out what went wrong. I'd try ~/xsession-errors first, then the files in /var/log/ .

---

### Post by mdflickner on 2014-12-27
I see a similar problem. 14.04 was running fine with classic desktop on VMWare Player hosted on Windows 7 .  I accepted the update yesterday and now I have just my background image.   Logging in with cntl-alt-f1 I see .xsession errors below. 

  Xlib: extension "GLX missing on display ":0".
  openConnection: connect: No such file or directory. 
  cannot connect to brltty at :0
  Script for ibus started at run_im.
  Script for auto started at run_im. 
  Script for default started at run_im.  
  init: at-spi2-registryd main processing ended, respawning
  init: at-spi2-registryd main processing ended, respawning
...

From the console 'sudo service lightdm restart' gives me the login windows where I can chose 

GNOME, 
GNOME Classic, 
GNOME Flashback( Compiz )  
GNOME Flashback (Metacity) 
Ubuntu (Default) 

It accepts my password but none of the options give me a working desktop - just my background image. 
I can manually run xterm and it appears with no controls or decorations ( no window manager running).  

For reference - magic keystrokes to chase this problem are:
  cntl-alt-f1       console
  cntl-alt-f7       X-window system
  cntl-alt           cursor deselect console window

---

### Post by rdh61 on 2014-12-30
Thanks for the replies. Simple problem, simple solution... I had no space left on my hard drive so the desktop could not load. Got rid of some stuff and now it's back to normal. I'm marking the thread "solved".

---

