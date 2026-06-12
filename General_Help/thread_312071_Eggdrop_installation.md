---
title: "Eggdrop installation"
date: 2006-12-03
forum: General Help
---

### Post by Dr Small on 2006-12-03
Hello.
This time around, it's not a command line problem, but more of a installation problem.
I ran the command to download eggdrop (an IRC Bot):
```
sudo apt-get install eggdrop
```

But once it installs, I don't know how to run it, or even find it.
Anyone that could possible download it and help me out of how to run it, I would greatly appreciate.

Dr Small

---

### Post by Dr Small on 2006-12-03
..:: Bump ::..

I would really like to get some help on this and figure it out.
I've been away for 40 Minutes, and there hasn't been anyone viewing this besides MY first view!

Dr Small

---

### Post by aysiu on 2006-12-03
I don't know anything about EggDrop, but have you tried typing *egg* and then hitting the **Tab** key twice?

---

### Post by Peepsalot on 2006-12-03
Well i've never heard of it before but maybe this page has your answers:
[http://www.eggheads.org/support/egghtml/1.6.18/](http://www.eggheads.org/support/egghtml/1.6.18/)

typing eggdrop in terminal does not do anything?

---

### Post by aysiu on 2006-12-03
Apparently you need some kind of configuration file? ```
eggdrop 

Eggdrop v1.6.17 (C) 1997 Robey Pointer (C) 2004 Eggheads
[18:59] --- Loading eggdrop v1.6.17 (Sun Dec  3 2006)
[18:59] * CONFIG FILE NOT LOADED (NOT FOUND, OR ERROR)
``` Maybe this might help?
[http://www.egghelp.org/files.htm#config](http://www.egghelp.org/files.htm#config)

---

### Post by Dr Small on 2006-12-03
If i type eggdrop in the terminal, it's output it:

```

Eggdrop v1.6.17 (C) 1997 Robey Pointer (C) 2004 Eggheads
[22:00] --- Loading eggdrop v1.6.17 (Sun Dec  3 2006)
[22:00] * CONFIG FILE NOT LOADED (NOT FOUND, OR ERROR)

```

[quote=aysiu]but have you tried typing egg and then hitting the Tab key twice?[/quote]
I really don't understand what you mean...

[quote=Peepsalot]Well i've never heard of it before but maybe this page has your answers:
[http://www.eggheads.org/support/egghtml/1.6.18/](http://www.eggheads.org/support/egghtml/1.6.18/)[/quote]

I'll check it out.

Dr Small

---

### Post by aysiu on 2006-12-03
You know how you usually type a command and hit **Enter**?

If you type *part* of the command (say, *egg* instead of *eggdrop*) and the hit the **Tab** key twice instead of hitting **Enter**, all the possible commands starting with *egg* will appear.

---

### Post by Voxxi on 2006-12-03
> **Dr Small said:**
> 
I really don't understand what you mean...


What he is referring to is the terminals "autocomplete" feature. If you type a command, and press tab twice, the terminal will show you all the commands you could enter. For instance:

I want to use "sudo". I type su into the terminal and press tab twice. Then the terminal shows me ALL the commands I could run that start with "su". Its a very useful feature, and it also works with filenames. When you can be bothered typing out a full filename in the terminal, just press tab and it will complete the filename for you. ;)

---

### Post by aysiu on 2006-12-03
Here's an example in action. If I type *gnome* and hit **Tab** twice, I get this: ```
username@ubuntu:~$ gnome
gnome-about                              gnome-language-selector                  gnome-terminal.wrapper
gnome-about-me                           gnome-menu-spec-test                     gnome-text-editor
gnome-accessibility-keyboard-properties  gnome-mouse-properties                   gnome-theme-manager
gnome-app-install                        gnome-nettool                            gnome-theme-thumbnailer
gnome-at-properties                      gnome-network-preferences                gnome-thumbnail-font
gnome-audio-profiles-properties          gnome-open                               gnometris
gnome-background-properties              gnome-panel                              gnome-typing-monitor
gnome-btdownload                         gnome-panel-screenshot                   gnome-ui-properties
gnome-calculator                         gnome-pilot-make-password                gnomevfs-cat
gnome-cd                                 gnome-power-inhibit-test                 gnomevfs-copy
gnome-character-map                      gnome-power-manager                      gnomevfs-df
gnome-control-center                     gnome-power-preferences                  gnomevfs-info
gnome-cups-add                           gnome-screensaver                        gnomevfs-ls
gnome-cups-icon                          gnome-screensaver-command                gnomevfs-mkdir
gnome-cups-manager                       gnome-screensaver-preferences            gnomevfs-monitor
gnome-default-applications-properties    gnome-screenshot                         gnomevfs-mv
gnome-desktop-item-edit                  gnome-search-tool                        gnomevfs-rm
gnome-dictionary                         gnome-session                            gnome-video-thumbnailer
gnome-display-properties                 gnome-session-properties                 gnome-volume-control
gnome-doc-prepare                        gnome-session-remove                     gnome-volume-manager
gnome-font-properties                    gnome-session-save                       gnome-volume-manager-gthumb
gnome-font-viewer                        gnome-settings-daemon                    gnome-volume-properties
gnome-help                               gnome-sound-properties                   gnome-window-properties
gnome-keybinding-properties              gnome-sound-recorder                     gnome-wm
gnome-keyboard-properties                gnome-system-log                         gnome-www-browser
gnome-keyring-daemon                     gnome-system-monitor                     
gnome-keyring-manager                    gnome-terminal                       
``` If, however, I type *gnome* and hit **Enter**, I get this: ```
username@ubuntu:~$ gnome
bash: gnome: command not found
```

---

### Post by Dr Small on 2006-12-04
Ok. I now understand about the "double tab" to show more things you can do, and all, but I still haven't figured out eggdrop.

I went to the website you specified, and downloaded the config file, but for the life of me, I can't find out where I need to _put_ the config file.

Furthermore, when I tried copying it into /usr/share/doc/eggdrop-data/
it won't let me copy it into there, so I'm really confused now.

Dr Small

---

### Post by aysiu on 2006-12-04
```
sudo mv *configfile* /usr/share/doc/eggdrop-data/
``` If you prefer drag and drop, read this:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by Puck7 on 2007-08-08
ok i have managed to make the eggdrop,.
what aysiu said its ok, make sure you edit your conf file and the name should be eggdrop.conf . You can edit the conf file with "pico eggdrop.conf" and make sure you do as they say in there, there are 2 lines you have to remove, with "die bla bla bla". The editing can be done only with root permissions, so with sudo. 
after that you have exit the root administration and you can fire up the egg only with your basic username typing "./eggdrop -m eggdrop.conf" anyway everything is on  the screen. After that you have to connect to the bot thruw telnet or on irc, depending on your configuration.

---

### Post by Jenga201 on 2007-08-09
is it possible that sudo apt-get install eggdrop is incomplete ?

No matter what i do, i get a 'cannot load module channels.so' error.

I know my eggdrop.conf works (probably) because i use it on my windrop bot...same thing as eggdrop, but for windows.

is anybody else having this trouble, or just me?  ...I'm going to go compile it to see if that version works.

---

### Post by Jenga201 on 2007-08-09
yep...compiled eggdrop fine...my conf was also good.

seems sudo apt-get install eggdrop is messed up somehow.

---

### Post by stealth17 on 2007-08-15
[http://www.egginfo.org/?page=config](http://www.egginfo.org/?page=config)

---

### Post by stealth17 on 2007-08-15
> **Jenga201 said:**
> yep...compiled eggdrop fine...my conf was also good.

seems sudo apt-get install eggdrop is messed up somehow.

I'm trying to compile. Where do I get Tcl?

---

### Post by Raff7 on 2007-08-18
> **stealth17 said:**
> I'm trying to compile. Where do I get Tcl?
install the tk8.5-deb (if i'm not wrong with the name) and u can continue the installation

---

### Post by freesp on 2008-02-27
Hello, i know how to get a eggdrop working
i dont have much knowledge about linux etc.. but if you use (msn)
send it to me in a private message,, and ill tell you how to configure and setup a eggdrop.

---

### Post by notwen on 2008-02-27
I run 5+ eggs on EFnet.  Here is the most basic instructions I have came across.

[egghelp.org]("http://www.egghelp.org/setup.htm")

---

