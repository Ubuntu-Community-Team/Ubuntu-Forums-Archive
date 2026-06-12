---
title: "Docky question"
date: 2014-05-16
forum: General Help
---

### Post by wvoutlaw2k on 2014-05-16
I'm in the process of making a customized remaster of Xubuntu, and I want to include Docky with my remaster.

My goal is to have Docky autostart from the get-go with a particular set of apps included in Docky.

What I have done is set up Docky to where it has the following items in the dock:
[LIST]
[*]Docky config tool
[*]Thunar file manager
[*]Google Chrome
[*]Rhythmbox
[*]F-Spot
[*]Pidgin
[*]LibreOffice Writer
[*]Trash
[/LIST]
Is there a hidden config file/folder in my home directory containing this info which I can simply copy over to the system to make Docky an autostarted app and include these apps as default for all users?

---

### Post by Frogs Hair on 2014-05-16
Hello and Welcome

Open the file manager and look for show hidden in preferences or behavior . Not all applications store configurations in that location and it may be inside an other folder such as .config.

---

### Post by wvoutlaw2k on 2014-05-16
Okay I found the config in /home/myname/.gconf/apps/docky-2

Now I need to know where to copy this info to.

The actual config file is located at /home/barry/.gconf/apps/docky-2/Docky/Interface/DockPreferences/Dock1/%gconf.xml

---

### Post by Frogs Hair on 2014-05-16
Please indicate how you are creating the re-master I have no experience with the process and can't offer any assistance. With new Ubuntu versions every six months I never considered making a re-spin . For cloning you can use the following.    [http://clonezilla.org/](http://clonezilla.org/)

---

### Post by wvoutlaw2k on 2014-05-16
I use Remastersys 3.0.4 - using "remastersys dist" - to make my remasters.

---

