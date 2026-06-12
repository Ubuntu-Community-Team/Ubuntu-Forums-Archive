---
title: "Launching a shell script with a menu interface from GUI"
date: 2014-03-17
forum: General Help
---

### Post by travissparks1307 on 2014-03-17
Here's the deal, I've been using mupen64plus for awhile now. It plays my games just fine, I got my controller working just fine, the only hassle is having to launch it from a terminal every time I wanna play a game. So, never afraid to get my hands dirty, I decided to simplify my life by making a simple BASH shell script with a menu interface so all I'd have to do is launch my script, choose my game from the menu and off I go! The script works just fine... when I launch it from the terminal. I made a shortcut in /usr/share/applications complete with icon, so all I'd have to do is click the icon, choose, yada yada. Well, it's not working out that way. It used to be there was an option for running programs in the terminal, or you could just edit *.desktop and set Terminal=True. This doesn't seem to be the case anymore. The shell script is located in /usr/games (same as the mupen64plus binary) it's set to be executable, Nautilus default behavior (for my user, AND root) is to launch executable text files instead of opening in gedit. Nothing I try is working. I've even tried setting the shortcut's command to gnome-open myscript, gnome-terminal myscript, bash myscript and still no luck. When I use gnome-open, it opens it in gedit. I'm at a loss, and I'm frustrated. I'm using Ubuntu 12.04 with Unity

---

### Post by efflandt on 2014-03-17
What is the actual command you are trying to run and does it contain parameters or anything that requires shell interpretation (which might not be properly interpreted in a launcher)? That can be difficult to determine when a terminal window opens and immediately closes. Simply launching a script by name with no path or parameters, that is in your ~/bin (and therefore, automatically in your $PATH) should be a no brainer. But parameters or metacharacters that you might think would be automatically interpreted might not be in a desktop launcher.

For example for my minecraft launcher I use **sh -c** with the command in single quotes, but I forget if I needed that due to parameters or only to interpret the ~ as my home directory in the path:```
[Desktop Entry]
Version=1.0
Type=Application
Terminal=true
Icon=/home/efflandt/Pictures/Icons/minecraft.png
Name=Minecraft-direct
Exec=sh -c 'java -jar ~/Downloads/Minecraft.jar'
Name[en_US]=Minecraft
```

---

### Post by deadflowr on 2014-03-17
If using the above mentioned method, to expand on that, you can add quicklists as well.
For me I do it like this
```
[Dewsktop Entry]
Name=Whatever
Icon=Something
Type=Application
Exec=Something
Actions=game1;game2;

[Desktop Action game1]
Name=Game 1
Exec=mupen64plus path-to-game-1

[Desktop Action game2]
Name=Game 2
Exec=mupen64plus path-to-game-2
```

Then save it in /home/user/.local/share/applications.
Find it in the dash and add it to the launcher
Right click to use the quicklist function.

You can also make individual launchers if you like.

The benefit of the quicklist function is you can set differing configuration settings for the various games if one or two need to have a certain setting that others don't.
Case in point, I have ocarina of time with quicklist entries for both windowed mode and fullscreen.

---

### Post by travissparks1307 on 2014-03-17
I got it working! I feel really stupid. The mistake I made in this case, was rather than manually creating a *.desktop file, I stupidly duplicated an already existing entry in /usr/share/applications and edited it by right-clicking and going to Properties. So starting from scratch, I went to my Home directory, manually created a *.desktop file using efflandt's example, made it executable, and BAM! It was such an obvious mistake on my part, I feel like an idiot!:oops: Thank you all for your help! For informational purposes I've included the [shortcut]("http://ubuntuone.com/2gWQ9kskMiSNAjbtCl5kaf")  the [script]("http://ubuntuone.com/7X2EtzUtKoy5LNSijezqjD") and a screenshot of the final [product]("http://ubuntuone.com/6g48Nn82O9PaJAZLhHSE9O")  Now that it's working, I'm going to expand on the idea as deadflowr suggests and work on a quicklist. I'll let you know how it goes!

---

