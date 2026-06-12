---
title: "Open in folder and run command as root"
date: 2019-01-27
forum: General Help
---

### Post by desiwah on 2019-01-27
I couldn't find anything like this, so I'm posting to ask how to do this.
I want to start my game from Application menu because this game I can only start by opening terminal in game directory and then ./freeso.command

With help of alacarte I successfully added the game in Application menu, BUT it doesn't start terminal first and then the Game. Why I need it?
If I just exit the game, game is still going ot be opened and eating resources. I saw it in system monitor. Basically I need a command that is going to open terminal, cd directory and then run the ./ command.

How can I do that and then add it to the Application menu?

I need a step by step and full command after full command because I+m not any kind of expert.

Thank You! :)

---

### Post by sisco311 on 2019-01-27
Hi, desiwah,

and welcome to the forums!

```
gnome-terminal -e "sh -c 'cd path/to/dir && ./freeso.command"
```will do what you want but I don't think you need a terminal to run the game so ```
sh -c 'cd path/to/dir && ./freeso.command'
``` should do the trick as well.

I'm not familiar with alacarte but I just checked it and it has an option to run the command in a terminal if that is really necessary. 

You can also modify the desktop file created by alacarte to reach your goals. The file is located in ~/.local/share/applications/

In order to run the game in a terminal you will have to add the line:
```
Terminal=true
```
and to set the working directory you will have to add:```
Path=/path/to/dir
```to the .desktop file.

HTH

---

### Post by Dennis N on 2019-01-27
Possibly in the .desktop file for the game, you could add a PATH= line for the game directory, and then no longer need to use terminal to change to game directory to start it. It will start from menu entry.

Example:
```
[Desktop Entry]
Version=1.0
Type=Application
Name=Machinarium
Icon=/home/dmn/games/Machinarium/menu-icon-3a.png
Exec=/home/dmn/games/Machinarium/Machinarium
[COLOR="#FF0000"]Path=/home/dmn/games/Machinarium[/COLOR]
NoDisplay=false
Categories=GTK;Game;
StartupNotify=false
Terminal=false

```
Before I did that, I had to start this game from the terminal by cd first to the game directory, then start it. My old script that changed directory and started game:
```
#!/bin/bash
#play Machinarium
cd /home/dmn/games/Machinarium
./Machinarium

```
 No longer needed when using PATH=

---

### Post by desiwah on 2019-01-27
Any change I made to .desktop file made alacarte unable to get the file making it removed from Application menu and alacarte app itself. Only thing that worked was

#!/bin/bash
#play Machinarium
cd /home/dmn/games/Machinarium
./Machinarium

but it is not what I need. When I do terminal=true it doesn't do anything and won't even start the game. With the script above I can start it, but processes are still there after I close the game and that is the reason why it must be started from terminal. Usually after I close the terminal window, game also ends from system monitor.
I thought there is some command that will open the terminal do the commands inside and then the game starts. It can be inside script also and then I can try link it somehow to the .desktop file and launch from App menu.

Also thank you for your welcome :D

---

### Post by Impavidus on 2019-01-28
Telling you what's going on behind the scenes might help.

What you call "closing the game" is actually closing the window of the game. Any application can have as many windows as it likes (including none at all, for most terminal-based applications) and it can open and close windows whenever it likes – or rather, ask the window manager to open or close windows. For GUI applications there's the guideline that after closing the final window, the application should terminate within seconds. It seems this doesn't work for your game. Maybe it has a bug causing an infinite loop in its cleanup routine. When you close the terminal, it sends a signal to the game (the SIGHUP signal), which causes termination of the game. You could also hit ctrl-c or use **killall name_of_your_game** for the same effect. Of course, for most applications this is considered a dirty way to stop them.

BTW, your thread title says "run command as root". You don't mention root in your question. What do you mean? In any case, don't run games as root.

---

### Post by desiwah on 2019-01-28
Yes. I thought I have to run it as root because on first run I got  error, but after that was fine. Game is actually for Windows, but it is a  "tweak" to run it and it must be started that way. Even in the  instructions it says that the game will be closed completely after  closing the terminal not just the window game. Game works normaly, I  just need to start it from App menu through terminal. I thought I can  make it much easier...

---

### Post by desiwah on 2019-01-28
Oh yeah, I did it! I used ```
tilix -e sh -c 'cd ~/.installs/FreeSO/client-665 && ./freeso.command'
``` as a command and it works!
Is there any way to add something to that command when I exit the game window, terminal exits also?

Thank you sisco311 for commands! I didn't quite understand how to use it because I was convinced it is more complicated.

---

### Post by Impavidus on 2019-01-29
> **desiwah said:**
> 
Is there any way to add something to that command when I exit the game window, terminal exits also?

If you can find out how to ask the window manager whether the window is open, it should be possible, but I'm not too familiar with interacting with window managers. The trick would be to write a wrapper script around your game. First start the game in the background, then have the script wait a few seconds to give the game an opportunity to open a window. Then repeatedly poll whether the window is open, when it's not, kill the game and exit the script. You don't actually need a terminal if you do it that way.

---

