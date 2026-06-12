---
title: "running an alias at startup/bootup"
date: 2024-04-16
forum: General Help
---

### Post by jadaja on 2024-04-16
is there a way to run an alias on a single user system? i run a google search and the closest i found was a similar question on here several years ago for a multi-user system and the answer involved editing the /etc/rc.local file and i don't have that. this is the article that i am referring to...[https://ubuntuforums.org/showthread.php?t=1795905](https://ubuntuforums.org/showthread.php?t=1795905).

at 1st i thought i would be of use to me but i found out that i don't have said file. if anyone can help me it would be greatly appreciated. i'm using jammy on a hp pavilion g7 16 gb ram 640 gb hdd i7 dual core.

---

### Post by #&amp;thj^% on 2024-04-16
It is unclear to me what you want??

I use a ".bash_aliases" will that not work you?

More detail is needed to give a straight suggestion. Like what alias you want to use ie:
```
alias l='ls -CF'
alias la='ls -A'
alias ll='ls -alF'
alias ls='ls --color=auto'
alias sl="ls"
alias lt='ls --human-readable --size -1 -S --classify'
alias df="df -Th"
alias left='ls -t -1'
alias count='find . -type f | wc -l'
alias mnt="mount | awk -F' ' '{ printf \"%s\t%s\n\",\$1,\$3; }' | column -t | egrep ^/dev/ | sort"
alias mntd="lsblk -e 7 -o name,size,type,fstype,mountpoint"
alias gh='history | grep'
alias cpv='rsync -ah --info=progress2'
alias ec4="sudo '/home/me/ExtremeCooling4Linux-v0.3-x86_64.AppImage' change-state"
alias st="sudo smartctl -a -t  long /dev/sdb2" 
alias grubmen="cat /boot/grub/grub.cfg | grep menuentry"
alias dp1="xrandr --output DP-2 --off"
alias dp2="xrandr --output DP-2 --auto"
alias bet="'/home/me/balenaEtcher-1.9.0-x64.AppImage' --disable-gpu-sandbox" 
```

That's just a small amount of alias's I use.

EDIT: For a startup I use something like this
```
# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi
```

Or and not what you said you wanted:
 it can be added to /etc/profile, which will affect all users upon login.

---

### Post by TheFu on 2024-04-16
No Linux system is "single user".  All Unix-based systems are multi-user, regardless of what you may believe.  There are probably 20, perhaps 50 users on your system now. They do things for us, even if they aren't connected to any human.  My desktop which is used by 1 human, has 62 accounts on it.  Multi-user, Yep.

Aliases aren't available until after a user has logged in.  Doesn't usually matter if they login with a GUI session or over a remote ssh session. The aliases are available.  However, if the alias tries to run a GUI program over an ssh session without an appropriately configured X11-Forward setup, it will crash.  It isn't possible to run a GUI program in a non-GUI environment.

Also, be certain that you understand the difference between at boot and at login.  Almost always, when people say they want something to happen _at boot_, they don't understand the difficulties.  Doing it a user login is pretty easy, however.  There's almost always a "startup applications" GUI settings for every DE in Linux.  Use to run something at login GUI session start.  It would be bad to have it happen at every login, since remote connections without a GUI are extremely common in all Unix-like operating systems.

Anyway, if you can spell out exactly, which programs you expect to use to do your google search, perhaps we can make suggestions for how to accomplish the goal?  

It is not possible to run any GUI program at boot, before a user login with an X/Session or Wayland/Session are setup and accepting events on the event loop for the GUI.

The clearer you are, the better the answers will be.

---

### Post by him610 on 2024-04-17
++> I use a ".bash_aliases"
Yes, I also use .bash_aliases. It has been modified for my own personally defined aliases, and distributed to each of my five systems.

Toward the tail of *.bashrc*, you will find this...
```
# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

```

---

### Post by TheFu on 2024-04-18
aliases don't happen until after a user's login.  Not at boot.

Boot, full-system startup, login, GUI-session startup are all distinctly different, in that order.  bash aliases don't become relevant until after "login".  People get these different steps confused.  If you want/need an alias to happen sooner, then that alias will need to be included in the bash script that runs at the time, but if that's the situation, I wouldn't bother with any alias, just use the command with all the desired options in the script.

---

### Post by Holger_Gehrke on 2024-04-18
Also aliases are not expanded in non-interactive shells, so you can't use them in scripts. If you need alias-like functionality inside a script you should use a function. Functions are a lot more powerful than aliases and I tend to define quite a few of them in ~/.bashrc and use them instead of stand-alone scripts.

Holger

---

### Post by vanadium on 2024-04-18
If the idea of the question is to define an alias that is in effect for all users of the system, then this can be done by adding an .sh file that contains the command to set the alias in the directory '/etc/profile.d'. Also system wide functions can be defined that way.

---

### Post by jadaja on 2024-04-18
to be more clear i want the alias to run after login. i'm the only person that uses the computer that's why i initially said single user. i didn't think about the 'other' virtual users. i appreciate the correction on that. i forget that ubuntu-restricted-extras doesn't like to install properly unless i use gdebi so i have an alias for root version of nautilus so i can easily get rid of the lock files in the apt and dpkg folders under /var/lib and i want to run that when i login.

---

### Post by TheFu on 2024-04-18
Odd, I don't have left over lock files after patching, er .... ever.  Rather than address the symptom, why not fix the root cause?

Also, why would you want to use a GUI file manager to delete files that have a clear pattern?  You could easily setup a task to run at boot/reboot that deletes lock files from /var/lib - or whatever the actual directory is, but I've never needed to do that in 30+ yrs of running Linux.  

Something is wrong with your system.

---

### Post by jadaja on 2024-04-19
it's the microsoft web fonts to be exact that give me the problem each time unless i use gdebi to install ubuntu-restricted-extras and i forget that every time i have to do a reinstall on this system that was originally built in 2012. i did end up getting a new hdd for it recently.

---

### Post by dragonfly41 on 2024-04-20
I don't pretend to understand the reasons for the font lockups but when I read these threads .. and learn much therefrom .. I ask myself what would I do?
That is, are there &#8220;any out of the box&#8221; approaches.   This is my thinking when I read feature requests in various app repos.
For the explained reason (setting aside the question why are the lockups there in the first place - re: @TheFu observation) surely it is a matter of a cron or other script to remove the blocks immediately after login (not before booting).
But I like the easy route of using GUI in my docking bar so I would install Stacer 
[https://oguzhaninan.github.io/Stacer-Web/](https://oguzhaninan.github.io/Stacer-Web/)
The second icon down in dashboard is Startup Apps. Certainly include Stacer to startup immediately. But then add to Startups list a script or simple GUI to tidy up any stuff (which as has been observed should not be there in the first place). The startup script can be configured  in multiple ways (bash, python .. whatever). A GUI utility tool I much favour is Actiona and after writing the tidyup script and testing it the script is run in Stacer by command: ```
actexec MyTidyUpActions.ascr
```
I startup a dozen or so apps in this way. But everyone to their own approach.
I know that this can be done in CLI *sans* Stacer.

[P.S] Here is a circuitous thought. You can even startup an Actiona script which "drives" the Stacer GUI.

---

### Post by him610 on 2024-04-20
> microsoft web fonts to be exact that give me the problem each time
If this causes your issues, then you might consider eliminating the cause.

---

