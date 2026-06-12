---
title: "Several minor/embarrassing problems"
date: 2007-08-21
forum: General Help
---

### Post by thatspracticallyforever on 2007-08-21
1) I have a primary folder in my home folder where I keep all of my files, let's call it "whales." In "Places" it lists "Home", "Whales", "Desktop", "Whales" and I want to remove the second "Whales" but obviously can't figure out how to do this; moving the shortcut just copies the entire folder to my desktop.

2) Is there a way to change the name of my home folder without compromising everything else on my PC? For example, if my home folder's name was "goku" and my current login is "kakarot", I would currently want my home folder to be "kakarot."

3) Linux minimizes multiple windows of something to the taskbar in tabs (e.g. there is one main Firefox window and 2-3 other corresponding Firefox windows upon clicking the main one) regardless of program. I find this to take more clicks and be more cumbersome than it normally would in the vast majority of instances. How do I revert to untabbed taskbar windows?

---

### Post by amadeus266 on 2007-08-21
1 & 2, I have no idea. 3- right click on the small bar on the left of the window list and click preferences then "never group windows"

---

### Post by aquavitae on 2007-08-21
1) You should be able to do something like right-click - remove shortcut.  Not sure what but I'd have thought it would be simple like that.  Not at linux atm so I can't check ;)

2) You can change your home folder.  You might be able to do it through system-settings - users, but I'm not sure.  Have a look around - if you don't find anything there you can do it this way:

a) Reboot, and at the grub boot menu select recovery mode.  This is to make sure that the x-server will not start.  If it did it would be trying to use all sorts of resource files in your home directory when you move it.

b) At the login, give the username as 'root'(without quotes) and give your user password when it prompts for password (Note that it won't show anything as you type your password.)  I'm not certain of the way ubuntu handles the root user, so it might not accept that.  If it doesn't, just log in to your normal user.

c) Type the following (if you logged in as root, don't type the 'sudo' part), replacing *home-folder* with the name of your new home folder, and *username* with your user name ```

sudo usermod -d /home/*home-folder* -m *username*

```

d) Reboot by typing ```
sudo reboot
```

Hope this helps.

---

### Post by boiiinnnnnnnnnnnnnnnnggg on 2007-08-21
This is the topic poster. I can't fix 1) by right clicking. amadeus's solution to 3) worked, and I'll try your solution to 2) later today.

---

### Post by kellemes on 2007-08-21
> **aquavitae said:**
> 1) You should be able to do something like right-click - remove shortcut.  Not sure what but I'd have thought it would be simple like that.  Not at linux atm so I can't check ;)

2) You can change your home folder.  You might be able to do it through system-settings - users, but I'm not sure.  Have a look around - if you don't find anything there you can do it this way:

a) Reboot, and at the grub boot menu select recovery mode.  This is to make sure that the x-server will not start.  If it did it would be trying to use all sorts of resource files in your home directory when you move it.

b) At the login, give the username as 'root'(without quotes) and give your user password when it prompts for password (Note that it won't show anything as you type your password.)  I'm not certain of the way ubuntu handles the root user, so it might not accept that.  If it doesn't, just log in to your normal user.

c) Type the following (if you logged in as root, don't type the 'sudo' part), replacing *home-folder* with the name of your new home folder, and *username* with your user name ```

sudo usermod -d /home/*home-folder* -m *username*

```

d) Reboot by typing ```
sudo reboot
```

Hope this helps.

Doesn't this give trouble with app.settings hardpointing to the homedirectory?

---

### Post by boiiinnnnnnnnnnnnnnnnggg on 2007-08-22
I tried renaming my home directory several months ago and many files did indeed hardpoint to the home directory. I'm wary to try this for that reason. 

How do I access the grub boot menu?

---

### Post by dfreer on 2007-08-22
You could also simply move the folder using the above method, and then create a symbolic link back to the old folder if you find some applications are using absolute paths. Of course, you'll end up with two folders in your /home... 

The grub boot menu is the very first thing you'll see after BIOS does it's POST test. If you only have linux installed, it should be hidden, with a short message that says something about GRUB and press a key to enter the menu. It'll probably only appear for 2-3 secs so be on the lookout for it.

---

### Post by aquavitae on 2007-08-22
I'd be surprised if app settings were hardpointing to your home.  Usually they point to ~/.  However as dfreer says, you could create symlinks as necessary.  > I tried renaming my home directory several months ago and many files did indeed hardpoint to the home directory.  Did you use the method I suggested, or did you just try to rename it.  If you just renamed it, then you would have problems because as far as the system is concerned your home folder hasn't changed, its just disappeared.  You need to tell the system you're changing it (using usermod) and then immediately logout (or reboot) so that the change takes effect.

---

