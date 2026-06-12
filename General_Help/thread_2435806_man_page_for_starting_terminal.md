---
title: "man page for starting terminal"
date: 2020-01-26
forum: General Help
---

### Post by DanPerecky on 2020-01-26
I am using Ubuntu 18.04.2 and would like to learn more about terminal and different options for it when starting.

I am trying to open terminal with more columns / rows.

Is it gnome-terminal?  or just terminal?

Thanks for your help in advance...

---

### Post by GhX6GZMB on 2020-01-26
I'm not certain about what you mean.
The terminal is normally started with Ctrl-Alt-T.

---

### Post by deadflowr on 2020-01-26
It's man gnome-terminal.
But to set a custom size open preferences in gnome terminal and set in the Text section in Profile sub section.

Preferences should be a menu option. (Should show with a right click)

---

### Post by DanPerecky on 2020-01-26
Oh yeah...  Thanks... I found what you were talking about: In Edit Profile | Checking on: Use custom default terminal size...

Thanks a Lot..

BTW... These do not work....
Tried:
prompt:~$ man gnome-terminal
No manual entry for gnome-terminal

prompt:~$ man Gnome-Terminal
No manual entry for Gnome-Terminal

prompt:~$ man GNOME-TERMINAL
No manual entry for GNOME-TERMINAL

---

### Post by yetimon_64 on 2020-01-26
> Is it gnome-terminal?  or just terminal?
"gnome-terminal" is correct. 

> **DanPerecky said:**
> ...
BTW... These do not work....
Tried:
prompt:~$ man gnome-terminal
No manual entry for gnome-terminal
...
On ubuntu mate 18.04 with gnome terminal installed here that command works.

Check that gnome terminal is actually installed on your system with ...
```
apt-cache policy gnome-terminal
```

My installation...
```
yetiman:~ $  apt-cache policy gnome-terminal
gnome-terminal:
  **Installed: 3.28.2-1ubuntu1~18.04.1**
  Candidate: 3.28.2-1ubuntu1~18.04.1 ...
```

---

### Post by TheFu on 2020-01-26
"terminal" is like saying "car"

I want to learn more about car.
There are many different cars.  There are many different terminals.  Each has slightly different features, but they all have 4 wheels and usually have a steering wheel, and engine. 

I'd guess there are at least 10 popular terminal programs. I'm not a fan of the Gnome variant, which seems bloated to me.  **lxterm** or **aterm** seem reasonable for capabilities and bloat.  Most of the time, I use a pure **xterm**, but it doesn't support utf8, which could be an issue for some sites/people.  xterm's don't have a menubar, so you'd need to use the different mouse click methods and modifier keys to see the different menus.  OTOH, xterm's honor all the expect .Xresource settings like font choices, sizes, using a font-server, secure terminal to prevent copy/paste by other X11 clients, etc.

Regardless, find the terminal program that works for your needs. It is a personal decision, but don't feel like you HAVE to use gnome-terminal. You don't.

If you want to learn more about the CLI/shell interface, here's a free, no-hassle book: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)
If you want to learn more about bash shell, the shell you are most likely using, besides a quick review of the bash manpage, check out [https://github.com/jlevy/the-art-of-command-line](https://github.com/jlevy/the-art-of-command-line) 

People new to Unix systems often have little idea how powerful their shell is.

If you want to automate stuff, learning a tiny bit of bash programming is highly useful. Search for 
"Beginning Bash Scripting Guide" && "Advanced Bash Scripting Guide"
A 5 line script is probably my average length in bash. Little, simple, needs.

---

### Post by DanPerecky on 2020-01-27
> **yetimon_64 said:**
> "gnome-terminal" is correct. 


On ubuntu mate 18.04 with gnome terminal installed here that command works.

Check that gnome terminal is actually installed on your system with ...
```
apt-cache policy gnome-terminal
```

My installation...
```
yetiman:~ $  apt-cache policy gnome-terminal
gnome-terminal:
  **Installed: 3.28.2-1ubuntu1~18.04.1**
  Candidate: 3.28.2-1ubuntu1~18.04.1 ...
```

I go to the menu bar at the top, and click on MATE Terminal.

When I issue the command, this is the results:
> s855-ubuntu@s855ubuntu-VB:~$ apt-cache policy gnome-terminal
gnome-terminal:
Installed: (none)
Candidate: 3.28.2-1ubuntu1~18.04.1
Version table:
3.28.2-1ubuntu1~18.04.1 500
500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/main amd64 Packages
3.28.1-1ubuntu1 500
500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/main amd64 Packages

So how do I know what version terminal I'm even running?

---

### Post by DanPerecky on 2020-01-27
TheFu

Thank you for the links....

---

### Post by CelticWarrior on 2020-01-27
> **DanPerecky said:**
> So how do I know what version terminal I'm even running?

You're actually running 'mate-terminal', the default in Ubuntu-MATE. Replace all the commands above for the proper name to confirm version.

---

### Post by TheFu on 2020-01-27
> **DanPerecky said:**
> I go to the menu bar at the top, and click on MATE Terminal.

When I issue the command, this is the results:


So how do I know what version terminal I'm even running?

Check the process table. That's the table maintained by the OS of all running processes.
You can do that anyway you like.  I'm old and have an alias - psg - which stands for ps-grep.  
```
alias psg='ps -eaf | grep $*'
```
Use it like this:
```
$ psg term
tf        3755  3593  0 Jan26 ?        00:00:00 xterm -class UXTerm -title uxterm -u8 -sb -geometry 80x25+770+340 -u8 -fs 16 -fa Monospace -sb -fg green -bg black
tf       23020     1  0 08:29 pts/1    00:00:00 xterm -class UXTerm -title uxterm -u8 -sb -geometry 80x25+0+0 -u8 -fs 16 -fa Monospace -sb -fg green -bg black -e ssh -X hadar
tf       23021     1  0 08:29 pts/1    00:00:00 xterm -class UXTerm -title uxterm -u8 -sb -geometry 80x25+760+355 -u8 -fs 16 -fa Monospace -sb -fg green -bg black -e ssh -X romulus
tf       23022     1  0 08:29 pts/1    00:00:00 xterm -class UXTerm -title uxterm -u8 -sb -geometry 80x25+760+0 -u8 -fs 16 -fa Monospace -sb -fg green -bg black -e ssh -X lubuntu
tf       23023     1  0 08:29 pts/1    00:00:00 xterm -class UXTerm -title uxterm -u8 -sb -geometry 80x25+830+60 -u8 -fs 16 -fa Monospace -sb -fg green -bg black -e ssh -X istar
tf       23936  3956  0 08:31 pts/1    00:00:00 grep term
```
There are newer (relatively) tools for searching the process table.  pgrep is one. There are others.  I have a few other "terms" running, but the process name doesn't have 'term' in it. They are rxvt-unicode processes. Sometimes I need utf8 support too.

I suspect that PDF book will have a chapter on this stuff.

---

### Post by yetimon_64 on 2020-01-27
> **DanPerecky said:**
> ...
s855-ubuntu@s855ubuntu-VB:~$ apt-cache policy gnome-terminal
gnome-terminal:
  **Installed: (none)...**
So how do I know what version terminal I'm even running?

You don't have gnome terminal installed at all according to that output.

From your first post ...
> I am using Ubuntu 18.04.2
... however gnome-terminal is standard for stock ubuntu installs. Which has me thinking you may have actually used an ubuntu-mate iso to install a "flavor" of Ubuntu not the main Ubuntu distro. The various flavors use different desktop environments and vary quite widely in applications used but all use the same base "core" ubuntu packages.

If you want to use gnome-terminal it is easy to install with ...
```
sudo apt install gnome-terminal
```

Unless you have a specific need for gnome terminal mate terminal is, in my opinion, a better option. The gnome devs have changed too much in the newer gnome terminal version for my needs. I use terminal profiles and profile names to create custom terminals for various specialized usage. Removal of my ability to control the terminal names stopped me in my tracks so most of my current terminal usage is now with mate terminal. Either are good though for most users.

**Edit:** On re-reading this  I just noted your original issue...
> I am trying to open terminal with more columns / rows.
In the next screenshot there are 4 very different mate terminals open, 2 with their preferences window open to show the size settings in use. The default profile has the size settings greyed out/unticked (standard) the large xmms2 terminal is set to a much larger size (like you are inquiring about). The other 2 are resized the same as the xmms2 terminal profile and have their window decorations stripped along with their placement and other aspects controlled with the devilspie2 daemon I use on this install. Profiles may be of use for you if you want to keep the default settings on one profile and have other profiles set up differently sized as well. There is also a "--geometry" switch you can use if you are not interested in setting up profiles.
[ATTACH=CONFIG]284910[/ATTACH][URL="https://drive.google.com/file/d/1UJslgH1IjflnpJCs3AkV4XALD2tS_Esh/view?usp=sharing"][COLOR=#0000ff]
Full Resolution on google drive
[/COLOR][/URL]
Regards, yeti.

---

### Post by DanPerecky on 2020-01-27
> **CelticWarrior said:**
> You're actually running 'mate-terminal', the default in Ubuntu-MATE. Replace all the commands above for the proper name to confirm version.

Right....    
```
man mate-terminal
``` 
works.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Thank You everybody for the info.....

---

### Post by DanPerecky on 2020-01-27
> **yetimon_64 said:**
> You don't have gnome terminal installed at all according to that output.

From your first post ...

... however gnome-terminal is standard for stock ubuntu installs. Which has me thinking you may have actually used an ubuntu-mate iso to install a "flavor" of Ubuntu not the main Ubuntu distro. The various flavors use different desktop environments and vary quite widely in applications used but all use the same base "core" ubuntu packages.

If you want to use gnome-terminal it is easy to install with ...
```
sudo apt install gnome-terminal
```

Unless you have a specific need for gnome terminal mate terminal is, in my opinion, a better option. The gnome devs have changed too much in the newer gnome terminal version for my needs. I use terminal profiles and profile names to create custom terminals for various specialized usage. Removal of my ability to control the terminal names stopped me in my tracks so most of my current terminal usage is now with mate terminal. Either are good though for most users.

**Edit:** On re-reading this  I just noted your original issue...

In the next screenshot there are 4 very different mate terminals open, 2 with their preferences window open to show the size settings in use. The default profile has the size settings greyed out/unticked (standard) the large xmms2 terminal is set to a much larger size (like you are inquiring about). The other 2 are resized the same as the xmms2 terminal profile and have their window decorations stripped along with their placement and other aspects controlled with the devilspie2 daemon I use on this install. Profiles may be of use for you if you want to keep the default settings on one profile and have other profiles set up differently sized as well. There is also a "--geometry" switch you can use if you are not interested in setting up profiles.
[ATTACH=CONFIG]284910[/ATTACH][URL="https://drive.google.com/file/d/1UJslgH1IjflnpJCs3AkV4XALD2tS_Esh/view?usp=sharing"][COLOR=#0000ff]
Full Resolution on google drive
[/COLOR][/URL]
Regards, yeti.

Yes... sorry. I am using ubuntu mate....

I like the --geometry switch... That was what I was looking for - to have a bigger window when needed... Which will be available to start from the top Panel strip.

---

