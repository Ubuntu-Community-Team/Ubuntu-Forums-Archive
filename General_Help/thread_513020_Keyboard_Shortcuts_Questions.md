---
title: "Keyboard Shortcuts Questions"
date: 2007-07-30
forum: General Help
---

### Post by explemonk on 2007-07-30
Hello,

I have literally searched and dug for hours trying to find the answers to my questions, and I am going crazy here.  The first two questions are for Gnome and the third is for KDE, all on Feisty.

Question 1:
In System -> Preferences -> Keyboard Shortcuts there are entries for launch web browser, e-mail, etc.  As far as I can tell, the apps called by the web browser, email, and terminal shortcuts are controlled by System -> Preferences -> Preferred Applications.  So how do I control what app gets launched when I press, for example, the Launch Calculator shortcut.  What if I don't want it to launch gcalctool?

Question 2:
Relatedly, though I don't expect an answer to this question (but hope for one!), does anyone know why Ubuntu has a Launch Calculator option in the Keyboard Shortcuts but Fedora doesn't?  I assume that each distro customizes the available shortcuts to its likings, but there has to be some list to customize from, doesn't there?  Or a way to add to the list?

Question 3:
When I boot the Kubuntu Live CD on my laptop (an Intel hp dv9000 series), the "special keys" like volume up/down, mute, play/stop/next/previous, all work.  When I plug in my external keyboard, my calculator button on that works, too, calling speedcrunch.  I found that the file /usr/share/applications/kxkb/ubuntu.conf is being loaded by xmodmap when the session starts, to allow the keys to work in the first place, but what I can't figure out is where the settings are for telling the keys what to do.  I can find no reference anywhere, for example, for telling my "DVD" button to launch Amarok or my mute button to mute the audio.  I've looked everywhere on the CD I can think of for config files and settings, and read numerous tutorials on getting multimedia keys to work with KDE, and the keys seem to be working in a different way than any tutorial I have read suggests.  I'm wonderfully happy that they work, but I want to know ***how*** they work.

If anyone knows, I would love to know too.  Thanks in advance for any insights!

---

### Post by Paul S on 2007-07-30
> **explemonk said:**
> 

Question 3:
When I boot the Kubuntu Live CD on my laptop (an Intel hp dv9000 series), the "special keys" like volume up/down, mute, play/stop/next/previous, all work.  When I plug in my external keyboard, my calculator button on that works, too, calling speedcrunch.  I found that the file /usr/share/applications/kxkb/ubuntu.conf is being loaded by xmodmap when the session starts, to allow the keys to work in the first place, but what I can't figure out is where the settings are for telling the keys what to do.  I can find no reference anywhere, for example, for telling my "DVD" button to launch Amarok or my mute button to mute the audio.  I've looked everywhere on the CD I can think of for config files and settings, and read numerous tutorials on getting multimedia keys to work with KDE, and the keys seem to be working in a different way than any tutorial I have read suggests.  I'm wonderfully happy that they work, but I want to know ***how*** they work.

If anyone knows, I would love to know too.  Thanks in advance for any insights!

I only know KDE.  Menu > System Settings > Keyboard & Mouse > Keyboard Shortcuts > Application Shortcuts Tab is a place where you can specify some of your keyboard special keys.  On mine, for example, under Navigation, I have XF86Back listed as an Alternate for "Back".  Also, each KDE application has it's own shortcuts configuration on the Menu Bar > Settings > Configure Shortcuts.  So, for volume up and down keys, you would go to Amarok and use it's Configure Shortcuts menu item to specify the keys you want to control the volume, etc.

HTH,

---

### Post by explemonk on 2007-07-30
> **Paul S said:**
> I only know KDE.  Menu > System Settings > Keyboard & Mouse > Keyboard Shortcuts > Application Shortcuts Tab is a place where you can specify some of your keyboard special keys.  On mine, for example, under Navigation, I have XF86Back listed as an Alternate for "Back".  Also, each KDE application has it's own shortcuts configuration on the Menu Bar > Settings > Configure Shortcuts.  So, for volume up and down keys, you would go to Amarok and use it's Configure Shortcuts menu item to specify the keys you want to control the volume, etc.

HTH,

Thanks for your response.  OK, I found the settings in Amarok that make it use my play/pause, previous, next, and stop keys.  I also found the XF86Back and XF86Forward as you mentioned in the Keyboard Shortcuts -> Application Shortcuts.  What I can find no reference to, anywhere, is how my mute, volume up/down, XF86AudioMedia, and XF86Calculator keys are working.   Nothing in the Keyboard Shortcuts settings, nothing in Amarok, nothing in KMix, nothing anywhere I can find, and believe me, I have looked everywhere I can think of.  I would think that there is a configuration file somewhere, but I can't for the life of me find it.

---

### Post by explemonk on 2007-08-01
I have finally discovered that it is KMilo that is allowing the volume up/down and mute buttons to work in Kubuntu, I assume by sending calls to KMix.  I still have absolutely no clue how the calculator, mail, web, and search buttons are working, though.  I've looked at the Keyboard and Mouse -> Keyboard Shortcuts settings, the Accessiblity -> Input Actions settings, the menu editor, looked through the file system, etc. etc. etc. and I can't find anywhere that is telling my mail button to launch KMail or my calculator button to launch speedcrunch.

I also can't figure out how to add a Launch Calculator option to the keyboard shortcuts in Gnome on Fedora 7 (like exists in Ubuntu), but at least I can add a custom command in gconf-editor if I have to.

---

### Post by jolla on 2007-08-02
Try out [ReMoot,]("http://www.kde-apps.org/content/show.php/ReMoot?content=63140") I found it very good for the multimedia keys. It controls a number of apps like Xine, Kaffeine, Amarok and a bunch of other players. Either you use it with LinEAK or you go to System-settings>>keyboard-and-mouse>>keyboard-shortcuts>>command-shortcuts>>KDE-menu-editor. There you add a few "shortcuts" (eg commands to ReMoot like "remoot next") and asign them to a key. 
works very well!  :-)

---

### Post by frodon on 2007-08-02
@jolla, i still wonder why you persist to advice a tool which is not in the ubuntu repositories when you can just create a bind in metacity or just use xbindkeys which is in the repositories and has a nice GUI.

[http://ubuntuforums.org/showthread.php?t=79560](http://ubuntuforums.org/showthread.php?t=79560)

---

### Post by jolla on 2007-08-02
oh! Sorry, that was for our kubuntu friends! I should have added this for the ubuntuers:
In Gnome you can use the excellent program [xbindkeys]("http://ubuntuforums.org/showthread.php?t=79560") that will let you map commands to all those special keys, and other key bindings as well! you can for example use [ReMoot]("http://www.kde-apps.org/content/show.php/ReMoot?content=63140"). xbindkeys with ReMoot will let you control a bunch (not just one action per key, for example the keyboard button play works with all the supported apps)) of multimedia apps  with your multimedia keybord. Xbindkeys can make use of all those other keys as well, like mail and chat keys. :)

(though lineak and klineak are in the repositories, ReMoot just use stuff like LinEAK or Xbindkeys to execute its commands )

---

