---
title: "Executing bash command on login"
date: 2019-11-14
forum: General Help
---

### Post by zigbigadoorlue2 on 2019-11-14
Long story short: I want to make my desktop grayscale so computer is less addictive. Many potential paths were explored (like edditing x11.conf yikes!) but the only one that has worked is using compiz color filters. Unfortunately said filters seem to only be activated by a hot key combination and do not seem to be able to be made permanent. Soooooo I figured the hacky workaround, given my mad newb skills, would be to simulate the key presses using [COLOR=#242729][FONT=Consolas]xdotool during login by putting this [/FONT][/COLOR]In /home/user/.profile:[COLOR=#242729][FONT=Consolas]
[/FONT][/COLOR]```

# make black and white upon login

#!/bin/bash
xdotool key ctrl+alt+shift+d
``` 

But I've never written a script before and don't really know the formatting (took me the longest time to figure out to add the shebang line). I don't know if this command is being activated but things don't turn grey until I press the keys manually or type "xdotool key ctrl+alt+shift+d" into the terminal.  I'm using xed as my text editor and none of the text I entered in my "script" is changing color like the other bits of code further up.

Thanks for helping me with this crude solution!

L

---

### Post by Skaperen on 2019-11-14
on Xubuntu you can set your background to any color you want, among the colors your display hardware can digitize in the mode it is in.

1. right click on the background
2. select "Desktop Settings" about 2 or 3 rows up from the bottom
3. look for "Color:" on the left, probably under "Folder"
4. click the menu just to the right and select "Solid Color"
5. click the box just to the right of that menu
6. choose your color or try typing "#cccccc" in the "Color name:" box
7. click OK
8. click close

did i understand what you wanted?  you don't need a crude solution of an autostart script to do this?

---

### Post by TheFu on 2019-11-14
```
#!/bin/bash
```
needs to be the 1st line of the script.  Line #1, not line 4 or 10 or 2.   Line #1.
Bash is the interpreter. If a different language is used, like python, perl, awk, whatever, then the first line would be changed to refer to which ever of those is needed.

Also, whenever calling any program from a script, it is a best practice to use the full path to the program.
```
which xdotool 
```
says that is /usr/bin/xdotool

```
#!/bin/bash
/usr/bin/xdotool ........   
```

It is probably best NOT to put GUI control programs into the ~/.bashrc.  There are login methods that do not use any GUI which could be broken.  A broken init file can really ruin a day.  Keep GUI stuff in GUI init files.

---

### Post by zigbigadoorlue2 on 2019-11-14
Yeah, that would just turn my background white. I am trying to make everything on my monitor grayscale particularly things in the internet browser.

---

### Post by zigbigadoorlue2 on 2019-11-14
Here is my .profile file:
```
# ~/.profile: executed by the command interpreter for login shells.# This file is not read by bash(1), if ~/.bash_profile or ~/.bash_login
# exists.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.


# the default umask is set in /etc/profile; for setting the umask
# for ssh logins, install and configure the libpam-umask package.
#umask 022


# if running bash
if [ -n "$BASH_VERSION" ]; then
    # include .bashrc if it exists
    if [ -f "$HOME/.bashrc" ]; then
    . "$HOME/.bashrc"
    fi
fi


# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi


# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/.local/bin" ] ; then
    PATH="$HOME/.local/bin:$PATH"
fi


# make black and white upon login


#!/bin/bash
[COLOR=#000000][FONT=&quot]/usr/bin/xdotool[/FONT][/COLOR] key ctrl+alt+shift+d



```

So... would I put "#!/bin/bash" at the top of this file? Would that make all that "if fi" stuff that was already in the file no longer work?

> [COLOR=#000000]It is probably best NOT to put GUI control programs into the ~/.bashrc. There are login methods that do not use any GUI which could be broken. A broken init file can really ruin a day. Keep GUI stuff in GUI init files.[/COLOR]

Do yo mean that putting this script into .profile is a bad idea? Where would a better place to put it be? I just need those keys presses to be auto simulated at some point*. 

Thanks so much for your help!
L

*I also tried using cron by putting ```
@reboot xdotool key ctrl+alt+shift+d
``` in "crontabs -e". This did not work I'm guessing because it simulated those key presses before compiz was ready to receive them.

---

### Post by Holger_Gehrke on 2019-11-14
If you are using XUbuntu, then the right place to start your 'xdotool' would be in 'Session and Startup' which should be in the settings menu. On the tab "Application Autostart" you'll find a table of the autostarted programs and a button labelled 'Add' below that. In the dialog that opens enter a name (any name) for the application, give a description and enter your command in the third field.

And here's one more reason .profile is a bad idea: it only gets executed when an **interactive** **login** shell is started, so nothing would happen; if you boot into a graphical environment there's no interactive shell involved and if you open a terminal it's not a login shell ...

Holger

---

### Post by TheFu on 2019-11-14
Things that touch GUI stuff shouldn't be in a crontab or in .bashrc.
You should remove those extra lines from the ~/.bashrc.
The #!/bin/bash line, if needed, always goes on line #1.  ALWAYS!  I won't explain why it isn't needed in the ~/.bashrc. For that, get a beginning Unix/Linux book which explains the login process.  
[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) is one, but all of them should cover it.  That's why I wrote:
> needs to be the 1st line of the script. Line #1, not line 4 or 10 or 2. Line #1.
Just not in this, specific, situation.  If you put those commands into a separate file, then you would need to follow that rule, 99% of the time.  For when the exceptions are ... look at the built-in "source" command in most shells.

The GUI controls need to wait until there is a GUI session running controlled by the logged in userid.  Not all logins use a GUI.  Most of my logins do not use any GUI. I have 8 running now, no GUI.

There are 20+ different GUI session controllers and each will have a different way to run startup GUI things.  The DE or window manager will have that documented.  "Ubuntu Desktop Guide" will explain that for the Gnome3 DE and is easily found using google.  If you use openbox, GUI startup commands go into ~/.config/openbox/autostart

If you use X11 (not Wayland), then use **xsetroot** to make the root window whatever color you want. I have no idea how to do it for Wayland nor whether any DE ignores the commands from xsetroot.  It works with fvwm, which is the WM I use. I'm weird.

And every time we put a command into a file to be run we need to use the full path to the command. Don't trust the PATH. There are many times when the PATH is reset or altered for security reasons.  sudo and cron will. It is a simple thing, even if it is a pain.  Just do it to avoid lots of stupid, little, problems BEFORE they happen and you waist hours, days, trying to figure it out.  I've wasted way too much time by not using the full path in scripts. WAY TOO MUCH TIME.

---

### Post by zigbigadoorlue2 on 2019-11-14
Hey, thanks for the help! I removed the command from .profile and added it to session and startup like you suggested. It does not activate the gray scale. I wonder if it is timing. When I physically press the keys they won't work until after a certain point in the login process which is after the desktop has mostly loaded. I wonder if the key presses are being simulated too soon before compiz can properly handle them. The only solution I can think of is if there was a way to delay the execution somehow. Any thoughts?

---

### Post by zigbigadoorlue2 on 2019-11-14
Hmm, I think you might have the same confusion as the person who made the first reply. xsetroot seems to change the background. I want to make everything on my computer gray scale. particularly things displayed in the internet browser like images, youtube videos, gifs, etc.

---

### Post by TheFu on 2019-11-14
The xdotool command above does NOTHING on my system, hence my confusion.
Which OS?
Which DE?
Which WM?

---

### Post by zigbigadoorlue2 on 2019-11-14
Yeah I had to install it with apt so I'm guessing it doesn't come stock with your flavor either. From the MAN:
>   xdotool lets you programatically (or manually) simulate keyboard input and mouse activity, move and resize windows, etc. It does this using X11's XTEST extension and other Xlib functions.

OS: Linux/ubuntu
DE: Xfce
WM: acording to wikipedia xfce uses Xfwm

---

### Post by zigbigadoorlue2 on 2019-11-16
Ok, so I figured it out. For anyone finding this post, timing does matter but you also need to launch a shell before the command will work. Here is the final code:


sh -c "sleep 3; /usr/bin/xdotool key ctrl+alt+shift+d"


For anyone trying to make their monitor grayscale here is the full process using xfce:



[LIST]
[*]0) Install xdotool: sudo apt-get install xdotool
1) Click Main Menu > Settings > Desktop Settings. Change window manager to Compiz.
2) Click Main Menu > Settings > Compiz settings
3) Click the check box next to Color Filters and then click Color Filters
4) In Filter Files delete all the filters except grayscale.
5) Optional (I think): change the key combanation for Toggling Screen Filter to ctrl+alt+shift+d instead of super+d as super opens the Main Menu.
6) Click Main Menu > Settings > Session and Startup > Application Autostart > Add
7) Enter the fallowing:
Name ```
xdotool 
```
Description```
 make everything gray 
```
Command```
sh -c "sleep 3; /usr/bin/xdotool key ctrl+alt+shift+d"
```
[/LIST]



You may need to make sleep longer if your computer is slower than mine (unlikely). Using sleep 1 and 2 did not work for me. Sleep 3 was the minimum for my slow computer.
Thanks everyone for your help!


Luna

---

