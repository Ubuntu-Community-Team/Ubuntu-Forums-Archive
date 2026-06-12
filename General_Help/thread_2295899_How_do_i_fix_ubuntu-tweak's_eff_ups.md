---
title: "How do i fix ubuntu-tweak's eff ups???"
date: 2015-09-22
forum: General Help
---

### Post by CWZ on 2015-09-22
I was trying to change my login screen on **Ubuntu 14.04** a clean install. I did a search and found "***Ubuntu-tweak***". IT WORKED!...**BUT**,  it changed my background too (SO I THOUGHT) after some fiddling around  it turns out that what appears to be the problem is that the login  screen img that Ubuntu-tweak changed is just not letting go of the  background after login. for example i tried to just use another tool "***gnome-tweak***" (I think) to force the login screen to give way to my background **BUT**  it listed my background img as the correct img AND in Ubuntu-tweak if i  click the set login to background  img button it changes the login  screen to my background, so the background(desktop) is still the img its  supposed to be but the login img is overlaying its self to the desktop  and i cant seem to stop it, brake it, or even reason with it. It refuses  to compromise in any way. ***can somebody pls help me?***

---

### Post by speartip on 2015-09-22
Not a 100% but I think the login screen is controlled by lightdm. So maybe something like:
sudo dpkg-reconfigure lightdm
In a terminal might restore it to default.

---

### Post by CWZ on 2015-09-23
I think you are most correct on that lightdm controls the login it has for a few iterations now. **HOWEVER** i gave it a shot and it did not solve the problem. The issue seems to be more like i have a blue coffee cup on the table  then i used "***Ubuntu-tweak***" to change the color of the table and for some unknown reason it has placed the table on top of my coffee cup. It changed the color to what i wanted **BUT**. A most intriguing predicament since I would like to take a drink and all. I am in need of either a striate fix **OR** a better under standing of exactly what "***Ubuntu-tweak***" did or should have done **OR** really even just a fresh perspective or 2. **EITHER-WAY **thank you speartip.

---

### Post by mc4man on 2015-09-23
try - 
login > System settings > Appearance > change your desktop background to any of the wallpaers shown. If it changes then change back to whatever it is you want for your **Desktop** background

If you wish to know what ubuntu-tweak did (poorly) then [read here]("http://ubuntuhandbook.org/index.php/2014/04/ubuntu-14-04-change-login-screen-background-remove-the-white-dots/")

If you wish to undo all possible ubuntu-tweak changes then you need to reset your dconf user file back to default, if you wish to undo just the lightdm changes then above link shows what you need to reverse.

---

### Post by CWZ on 2015-09-24
**t**
First thanks for the reply mc4man. 

I  tried the System settings right away. In the screen for the preview it  shows the correct back ground.(EVEN THO ITS THE LOGIN BG THAT IS ON THE  SCREEN ASS IF IT WAS BEING PLACED ON TOP OF THE BACKGROUND)

As  for the "Ubuntu hand book" that you link me to dose not work i included  the terminal out put at the bottom of this post. The hand book is actual  the 1st thing tried butt when it failed I moved on and found the tweak  tool.(Yes my stem is fully up to date)

Now the dconf user file i  assume you are referring to "/run/user/1000/dconf" since its the only  one that comes up in the search. but it is un readable AND i have no  back up of this file so were/how do I restart this file? 
[B]



me@mine:~$ sudo -i
root@mine:~# xhost +SI:localuser:lightdm
localuser:lightdm being added to access control list
root@mine:~# su lightdm -s /bin/bash
lightdm@mine:/root$ deconf-editor
No command 'deconf-editor' found, did you mean:
 Command 'dconf-editor' from package 'dconf-editor' (universe)
deconf-editor: command not found
lightdm@mine:/root$ dconf-editor
No protocol specified

** (dconf-editor:15955): WARNING **: Could not open X display
No protocol specified

(dconf-editor:15955): Gdk-ERROR **: error: XDG_RUNTIME_DIR not set in the environment.

Trace/breakpoint trap (core dumped)
lightdm@mine:/root$ [/B]

---

### Post by mc4man on 2015-09-24
Well by system settings > appearance I meant actually change to another background from the ones shown in Wallpapers, it should immediately  change your Desktop background. 

Anyway the dconf/user file is in ~/.config but it's a binary & deleting or renaming it while in a user session isn't productive as it'll be restored from memory on log out or restart. (you could delete it or rename then hold down power button for a hard shutdown but no need.

To reset all gsettings back to defaults for **you** - 
reboot, at login screen go ctrl+alt+F3
login as you (your username ; your password
Then - 
```
mv .config/dconf/user .config/dconf/user.bak
```
```
sudo reboot
```

Once you log back in change the background of your Desktop to something else to see if it changes, then back to what ever background you wish for your Desktop.

As far as the greeter screen background, - if you disabled 'draw-user-backgrounds' & changed the default for 'background' for **user lightdm **then you'll need to restore those dconf settings back to their respective defaults as per method in the link.
(the button on far right in dconf-editor for each key restores default for that key

---

### Post by Frogs Hair on 2015-09-24
This may be related.  [http://ubuntuforums.org/showthread.php?t=2262862](http://ubuntuforums.org/showthread.php?t=2262862)

---

### Post by CWZ on 2015-09-25
MC4MAN :: I ment that i had tried to change the back ground by actually trying to change it. But either way your config reset worked so;
[B][I][U][FONT=comic sans ms][SIZE=4][COLOR=#ff0000]
T[/COLOR][COLOR=#ffff00][/COLOR][COLOR=#ff0000]HANK YOU.

[/COLOR][/SIZE][/FONT][/U][/I][/B]*_[FONT=comic sans ms][SIZE=4][COLOR=#ff0000][/COLOR][/SIZE][/FONT]_*_[FONT=comic sans ms][SIZE=4][COLOR=#ff0000][/COLOR][/SIZE][/FONT]_[FONT=comic sans ms][SIZE=4][COLOR=#ff0000][FONT=arial][/FONT][/COLOR][FONT=arial][SIZE=2]FROGS HAIR:: Thank you for the reply but problem was solved by mc4man I never even got to read the thread. Either way thank you too.[/SIZE][/FONT][/SIZE][/FONT]*_[FONT=comic sans ms][SIZE=4][COLOR=#ff0000][/COLOR][/SIZE][/FONT]_*_[FONT=comic sans ms][SIZE=4][COLOR=#ff0000][FONT=arial][/FONT][/COLOR][FONT=arial][/FONT][/SIZE][/FONT]_[FONT=comic sans ms][SIZE=4][FONT=arial][/FONT][/SIZE][/FONT]

---

