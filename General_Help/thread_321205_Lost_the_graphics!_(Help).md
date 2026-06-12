---
title: "Lost the graphics! (Help)"
date: 2006-12-18
forum: General Help
---

### Post by alex.de on 2006-12-18
Hi, I'm a beginner to Linux. Last night, I tryed to install some video drivers for Ubuntu (6.06). I replaced the xorg.conf file with a new one. I rebooted Linux and the next thing I know, all the graphics are gone. I'm left with the terminal and that's it.

I would like to know if there's a way to restore the file back or download the original file so I can replace.

Thanks for your help.

---

### Post by ajgreeny on 2006-12-18
There is probably a backup of the original file.  Have a look for it in /etc/X11/xorg.conf~ (or xorg.backup or xorg.conf~~) and then replace the new one with the appropriate old one and see where you get.  If you only have a terminal you will need to do everything using the cli.  After logging in type *cd /etc/X11* and then type *ls -a* which will tell you all the files in /etc/X11.  Look for an appropriate backup file and then rename that back to xorg.conf by typing *mv xorg.conf xorg.conf~~~* or whatever else you want, then rename your first backup file back to xorg.conf in the same way.   As you are already in folder X11, you do not need the full pathway to the files, just the file names.  Just make sure you make a note of all the different xorg files you have and what they are.

Alternatively in a terminal you can also do:-
*sudo dpkg-reconfigure xserver-xorg*

Accept all the defaults until you get to the video driver and change that back to whatever it was before.  When you have finished *Ctrl+Alt+backspace* to restart x and all may be back to where you were.

---

### Post by alex.de on 2006-12-18
Alright, I tryed fixing it with the 2 solutions you gave me.

I tryed:

```
sudo dpkg-reconfigure xserver-xorg
```

and it showed me the window to reconfigure my video settings. When they ask me what depth of color do I want to use, I choose 24 and it gives me this error:

> xserver-xorg postinst warning: overwriting possibly-customized configuration file; backup in /etc/X11/xorg.conf.20061218190315

Now it brings me back to the terminal without any graphical changes, even after I rebooted. Then I typed in the terminal:

```
cd /etc/X11
mv xorg.conf xorgbackup.conf
mv xorg.conf20061218190738 xorg.conf
```

And nothing appears. I tryed rebooting but it's still the same.


Thanks for your help. Any else I can try?

---

### Post by alex.de on 2006-12-18
Well, I reinstalled Ubuntu. I'll now what to do next time ;)

---

### Post by ajgreeny on 2006-12-19
Hi axel.de.
Just for future reference, when you execute a command such as mv to move or rename a file, or cp to copy a file as, for example, a backup, as you did, you will only get anything showing as a response if there is a problem, and then it will be an error message of some sort, probably telling you what to do to put things right.  No response, as in your case, means that everything went OK just as you wanted.

Sorry you ended up reinstalling, btu at least that is one lesson you will now remember.  By the way, I reinstalled a couple of times after my first attempt with linux and ubuntu.  Now generally, I find a way to sort things out using the command line which is not really as fearfull as many believe.

Good luck with your second attempt, and be warned, video drivers, especially ati drivers such as fglrx, can be pretty difficult to get running.  I've never got fglrx to work on my system of dapper, though it did on breezy.  I have an ati 9200 card and find it runs well with the ati default driver that was installed by the system at time of installing ubuntu.  It gives me direct rendering without a problem and as I'm not a gamer it is more than fast enough for me.  I get about 850 fps on glxgears withthw window showing and up to 8000+ fps when the glxgears window is minimised or covered by something, and 70 fps when glxgears window is maximised, more than enough for most uses, except graphic hungry games.

---

