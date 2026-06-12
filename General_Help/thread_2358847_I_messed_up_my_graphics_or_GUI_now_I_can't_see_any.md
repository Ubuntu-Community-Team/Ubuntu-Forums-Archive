---
title: "I messed up my graphics or GUI now I can't see anything - How do I reinstall them?"
date: 2017-04-18
forum: General Help
---

### Post by PopsTheSailor on 2017-04-18
I'm at work and my laptop is at home so this is all from memory. Hopefully I have it all right
What I have
Ubuntu 16.04 - Mate
Acer Laptop using GeForce 940M dedicated graphics 

What I did
I was trying to fix the issue with no sound from my laptop speakers so I uninstalled all the Alsa stuff. Then I reinstalled it but I was on the phone, not paying attention (I know!) and there was an option to select either my graphics or my GUI. I must have chose the wrong one. Now when I boot up, I get to Grub. If I select the normal boot process my screen goes blank. I've gone into Grub recovery and tried every option. The only thing that lets me get any further is to drop to the command line where I can login with my ID / PW but I don't know what to do next to reset my graphics or GUI environment.

---

### Post by dragonfly41 on 2017-04-18
Perhaps try booting up with alternative (earlier) kernel from Grub then if it gets you to a working state you can research further.

---

### Post by vasa1 on 2017-04-18
You could also consider a re-install in case you have the Live USB handy. Choosing the option to retain your home folder should preserve all your personal stuff.

---

### Post by HermanAB on 2017-04-18
If you have sshd running, then you can connect from another machine over ethernet

---

### Post by PopsTheSailor on 2017-04-18
I'm sorry I should have mentioned that I tried starting with an earlier version. I only have 1 other available. Unfortunately it does the same thing. I like the option of reinstalling, although I don't ever recall seeing that option but I probably just haven't looked closely enough. Do I first select the "Do Something Else" option or is it on the same screen with the "Do Something Else" option? I'll look around.

Oh, and I don't have an SSDHD either so unfortunately, I can't go that route either.

---

### Post by PopsTheSailor on 2017-04-18
OK so I can't reinstall because I think my home drive is encrypted and the only directions I can use look like it will cause me problems. In other research, I see that I can try this fix below. The problem is that I don't have a com folder off the root where it is supposed to be located. dconf is already installed, or at least that is what apt tells me. Any ideas?


[LIST]
[*]Ctrl + Alt + T (open terminal)
[*]sudo apt-get install dconf-editor (install dconf editor)
[*]dconf-editor (open dconf-editor)
[*]open path com -> ubuntu -> user-interface
[*]change or reset the scale-factor to eg. 10 or 20 (depends on your system)
[/LIST]

---

### Post by dragonfly41 on 2017-04-18
You might get some clues on what commands you ran to arrive at your present state by going to command line (Ctrl+Alt+T) and running
```
history
```
Also to restore your graphics (desktop?) perhaps the tips here [https://itsfoss.com/how-to-fix-no-unity-no-launcher-no-dash-in-ubuntu-12-10-quick-tip/](https://itsfoss.com/how-to-fix-no-unity-no-launcher-no-dash-in-ubuntu-12-10-quick-tip/)
might help.

---

### Post by PopsTheSailor on 2017-04-19
Well that's a handy little command regardless of my issue.

OK so that definitely helps show me what I did. The last thing was that I reinstalled the Alsa sound and utilities with the following:

sudo apt-get install linux-sound-base alsa-base-utils gdm ubuntu-desktop

I think it is the last part of the command that caused me all this trouble. There are a couple of possibilities.

1. the gdm ubuntu-desktop part of the command may not be the right desktop for my install. I'm on Ubuntu-mate 16.04
2. When I run the command I do remember it asking me something about the gui, if I'm not mistaken. Could have selected the wrong option. 

Before I rerun the above command, I need to know if gdm ubuntu-desktop is the right desktop environment for me. Does anyone know or is there a way to find out from the CLI? Since I drop to the command line from the grub menu, I don't think I ever start the desktop.

---

### Post by dragonfly41 on 2017-04-20
Please note that I have no experience with desktops other than my plain old ubuntu ..  However if I were in your position I would try reversing my tracks, going back through command history.

i.e. command to uninstall/purge gdm ubuntu-desktop

Then look around and follow advice in various web articles for re-installing Mate desktop

[http://tipsonubuntu.com/2017/03/15/install-mate-desktop-1-18-in-ubuntu-16-04/](http://tipsonubuntu.com/2017/03/15/install-mate-desktop-1-18-in-ubuntu-16-04/)

But this is a guess not based on any personal experience.

...

Some more discussion on gdm found here ..

[https://askubuntu.com/questions/766071/install-gnome-shell-on-ubuntu-16-04](https://askubuntu.com/questions/766071/install-gnome-shell-on-ubuntu-16-04)

---

### Post by PopsTheSailor on 2017-04-20
I installed over the old version and got my ID back and all my files but things are still all mucked up. Wifi doesn't detect anything, missing some folders, etc. I just decided to do a fresh install and move my files. Not worth the time or trouble trying to continue troubleshooting. Sad that I was stupid enough to follow some commands rather blindly and cause myself such grief. I also found other posts during my research where people did the same thing. Anyway, I'm back up with a fresh install.

I don't want to mark this thread as solved because what I did really didn't solve the initial problem so I guess I'll just leave it open. I don't know how to close a thread.

---

