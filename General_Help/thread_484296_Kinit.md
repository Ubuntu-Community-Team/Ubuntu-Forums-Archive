---
title: "Kinit"
date: 2007-06-25
forum: General Help
---

### Post by celticbhoy on 2007-06-25
A friends pc comes up with the error 
Kinit:No resume image doing normal boot
and then boots into a txt only OS have tried dpkg-reconfigure but no luck how do i fix it

---

### Post by rillip on 2007-06-25
I believe it's telling you the session it's trying to load isn't where it should be.  From the terminal, I'd try 

```
sudo startx
```

and see if it gives you the kdm login screen.  From there you can choose to make a new session from the drop down menu on the left.  If that gives you an error about x already running, if it's not dete a lock file, then delete the lock file it tells you about and try again.  If that doesn't work, try

sudo init 5

This will switch your runlevel (probably 3, which is used as recovery mode) to 5 (this is the default mode).  I wouldn' t be suprised if this gives you the same error, however.  Worst comes to worst, you could always uninstall kde and reinstall it using

```
sudo apt-get remove kde
sudo apt-get install kde

```

This doesn't remove the OS, just the kde gui, then puts it back. You'll probably end up with a few more packages than you did before, but you can clean these up manually through add/remove programs once you're back in (I say to do it like this as you won't neccessarily want to write down every package installed, look it up to find out if you want it, then remove it).

---

### Post by mikealive on 2007-06-25
i have the same exact problem here.  [http://ubuntuforums.org/showthread.php?t=479545](http://ubuntuforums.org/showthread.php?t=479545)

started happening after the last update i did.

---

### Post by celticbhoy on 2007-06-25
Startx worked ok he seems to have removed some or all of KDE as it is running Xfce how can i set this to start on boot up as he is off line for a while

---

### Post by tomrob on 2008-01-17
Just if anyone finds this thread and have the same problem.

I had the same exact problem. After I tried to fix some soundcard issues, the laptop(dell D620), booted directly into this textbased login screen. "kinit:No resume image, .." and so on. Had to use "startx" to start my GUI, but then as runlevel 1 (no login window and no shutdown options in GUI, had to use Ctrl+Alt+BACKSPACE to shutdown).

The fix in my case was easy(after hours searching forums....). It turns out that i had removed a package called 'ubuntu-desktop' in my eager to get the soundplayback working. Installed it again from the synaptic package manager, rebooted, and all is well!

I'm running Ubuntu Gutsy 7.10

---

