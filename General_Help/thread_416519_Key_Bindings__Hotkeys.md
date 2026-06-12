---
title: "Key Bindings / Hotkeys"
date: 2007-04-21
forum: General Help
---

### Post by oomingmak on 2007-04-21
Can anybody tell me where Ubuntu stores the settings for key bindings?

If I wanted to back up all the changes I've made, what file should I save?

---

### Post by Brucevdk on 2007-04-21
Any user related settings you modify under your own account are stored in hidden folders in your home directory (~). When you are prompted for a password (or use sudo/gksudo) settings you modify are usually stored in */etc/*.

So if you want to back something up just copy your whole home directory (including the hidden files) somewhere safe. 

Any user settings related to anything GNOME are stored in *~/.gconf*, keybindings are stored in *~/.gconf/apps/metacity* (replace metacity with compiz or beryl if you're using those window managers). You can edit these files (the [GConf Configuration Database]("http://advogato.org/proj/GConf/")) using *gconf-editor*.

Note that a lot of settings are not exposed through GUIs, such as the ability to bind keys to custom commands. However, they can be found in GConf.

---

### Post by oomingmak on 2007-04-21
Thanks very much!

You answered several questions that I wanted to ask, all in one go.

 :)

I did make a backup of my home folder from my feisty beta install in preparation for a clean 7.04 release version install, but there was loads of crap in there because I was testing out pretty much anything that I could get my hands on seeing (as I knew I was going to format and start again). 

The only thing that I had really heavily customised was the keyboard shortcuts (spent ages on it) and it seemed overkill to replace the entire home folder (complete with all the junk) just to get the keyboard shortcuts back.

I did play around with sbackup and noticed that it backed up quite a few more things than just the home folder (most if which I didn't understand because the linux file system layout is still a total mystery to me). So, I wasn't sure if just backing up my Home folder / partition would mean that I got **all** of my settings back, or whether there were a few things scattered around elsewhere.

[quote=Brucevdk]Note that a lot of settings are not exposed through GUIs, such as the ability to bind keys to custom commands. However, they can be found in GConf.[/quote]
I was thinking of trying out something called "xbindkeys" (if that would make things any easier). :confused:

---

### Post by oomingmak on 2007-07-03
I have just tried to restore a backed up copy of my key bindings (~/.gconf/apps/metacity), but despite having restarted the system, when I check the Keyboard Shortcuts applet, none of my keyboard shortcuts are present.

Can someone please tell me how to restore my keyboard settings without having to restore the entire Home partition?

---

