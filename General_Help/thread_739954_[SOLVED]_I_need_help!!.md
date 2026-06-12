---
title: "[SOLVED] I need help!!"
date: 2008-03-30
forum: General Help
---

### Post by gilloz on 2008-03-30
In the process of removing a gcj web browser plugin, something happened in that when I now restart my computer, it takes me directly to my terminal screen.  I don't know how to get back to my Desktop.  I tried to go to the Recovery Mode, but I still end up at a full Terminal screen.  Any help would really be appreciated.

---

### Post by pointone on 2008-03-30
At the terminal screen, login and run the following command:

```
sudo /etc/init.d/gdm restart
```

Does the GUI start? If not, post any error messages that appear.

---

### Post by gilloz on 2008-03-30
Thank you pointone for your response.  I entered the line you gave me and it came back asking me for my password, so I entered it and I was right back with my initial prompt  gilloz@gilloz-desktop:~$   I typed in "startx", without the quotes,  and it came back  /etc/x11/x is not executable.  I also tried starting in the Recovery Mode at the beginning of the boot sequence.  It went through some checks and configurations, I guess and then stopped at my login terminal screen.  I am just totally lost.  It all happened after I tried to uninstall a Java Web Browser plugin.  During the process, the computer locked up.  I waited a while and had to depress the Reset button on my tower.  Thats when it started going into my Terminal login instead of my Desktop.  Oh, and NO, my GUI did not start.

---

### Post by pointone on 2008-03-30
Post the outputs of: 

```
ls /etc/X11 -l
```

... and: 

```
ls /usr/bin/X* -l
```

---

### Post by Sidewinder1 on 2008-03-30
I know that it's after the fact but it's never a good idea to do a hard (with the power button) reset unless all other methods have failed. I know, I've done it myself with bad results. Have a look here; won't help with your current problem but may prevent future problems. Also search these forums for REISUB for more info.   [http://ubuntuforums.org/showthread.php?t=683141](http://ubuntuforums.org/showthread.php?t=683141)

---

### Post by gilloz on 2008-03-30
Point one: depending on whether I use the number ONE or the lower case letter L at each end will give me "file not found".  One of them, not sure now, gave me a list of items in Green and a few in Blue.  I don't know the command to only have it list one page at a time.  The whole list comes up and only shows the end.  How do I make it give me a page at a time in Terminal?  This is really a big mess.

---

### Post by pointone on 2008-03-30
Yes, sorry... I'll try to make it simpler.

The result that matters most is from "ls /usr/bin/X* -l".

That's "capital X" (important), "asterisk" and "dash ell" at the end, as in lion.

On my machine, three files are listed. What I'm interested in are the permissions on these three files. The result should look something like:

```
[color=red]-rwsr-sr-x[/color] 1 root root 7.3K 2007-10-09 14:53 [color=red]/usr/bin/X[/color]
[color=red]lrwxrwxrwx[/color] 1 root root    1 2008-01-05 17:27 [color=red]/usr/bin/X11 -> .[/color]
[color=red]-rwxr-xr-x[/color] 1 root root 1.7M 2008-01-18 18:19 [color=red]/usr/bin/Xorg[/color]
```

Could you take note of the parts I've highlighted in red and post them here?

What might make the entire process easier for you is booting from the live CD. This way you'll have the familiar GUI environment, and be able to access your installed system.

Also, try running the following commands:

```
sudo apt-get update
sudo apt-get -f install
```

---

### Post by gilloz on 2008-03-30
Pointone:  I really really appreciate you staying with me to solve my problem.  I have good news.  The problem is solved.  While waiting for your response, I went to ubuntu wiki and some other guy was having an identical problem.  They suggested him to try the following:  in Terminal type " sudo aptitude update", then after that was done, type "sudo aptitude install ubuntu-desktop".  I did both of those and it went on for about 20 minutes.  When it was done I did a Ctrl+Alt+Delete and it came up again to the full screen terminal prompt, but it kept recycling about 3 times, like blank screen, then the prompt, then blank screen and the prompt, etc. then my GUI came up to the Login Page.  My desktop was back, but the resolution had to be adjusted.  Everything else appears to be intacted.  So there you have it.  Again, I really appreciate you taking the time to help me out.  I think I will power down and give this computer a rest.  I have been going at it since 8 am PST.  I need to eat.  Have a good one Pointone and thanks.

Added info:  I think I know what I did to begin with.  In the process of removing some Java Plugins, I noticed that in one file where I marked it as to remove, it listed a bunch of additional files that would be removed and one of them was Ubuntu-Desktop.  I'm pretty sure that was my whole problem.  I wasn't watching what I was doing.  Live and learn.  see ya.

---

