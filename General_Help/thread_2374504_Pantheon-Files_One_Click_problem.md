---
title: "Pantheon-Files One Click problem"
date: 2017-10-16
forum: General Help
---

### Post by Hasimir on 2017-10-16
Hi :)
I've been running Ubuntu Gnome 17.04 for a few months now.
I managed to install Pantheon-Files on it, and it works really well, except I would prefer it to NOT open files with a single click.
To fix this I read some guides and eventually installed the Elementary-Tweak tool.
I used it to configure Pantheon to open files with two-cliks.
It worked.

Then some update came along and reset Pantheon to one-click no matter what I did with the Tweak tool or with a direct terminal command meant to configure the right setting manually.
So I thought of uninstalling and reinstalling both Tools and Pantheon.
Pantheon reinstalled fine.
The Tools... did not.
For some reason I am now unable to install them. When I try I get some error with the repositories.

Help? :)

---

### Post by Frogs Hair on 2017-10-16
Do you have elementary repositories enabled on your system ? Post the output of the following. ```
sudo apt update 
```

---

### Post by Hasimir on 2017-10-16
In theory, yes.
I even did the thing written in a bunch of guides, where I modified the rep file to say "xenial" instead of "zesty".
It worked in the past, but as I mentioned now it doesn't work anymore and I get this errors:

> 
Hit:1 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) zesty InRelease
Hit:2 [http://repo.steampowered.com/steam](http://repo.steampowered.com/steam) precise InRelease                     
Hit:3 [http://ppa.launchpad.net/elementary-os/daily/ubuntu](http://ppa.launchpad.net/elementary-os/daily/ubuntu) xenial InRelease     
Ign:4 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease                   
Hit:5 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) zesty InRelease                      
Hit:6 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release                     
Hit:7 [https://repo.skype.com/deb](https://repo.skype.com/deb) stable InRelease                              
Hit:8 [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) zesty InRelease     
Hit:9 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) zesty-updates InRelease              
Get:10 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) zesty-security InRelease [89,2 kB]    
Hit:11 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) zesty-backports InRelease           
Ign:12 [https://mega.nz/linux/MEGAsync/xUbuntu_17.04](https://mega.nz/linux/MEGAsync/xUbuntu_17.04) ./ InRelease               
Hit:13 [http://ppa.launchpad.net/linrunner/tlp/ubuntu](http://ppa.launchpad.net/linrunner/tlp/ubuntu) zesty InRelease           
Ign:14 [http://ppa.launchpad.net/mpstark/elementary-tweaks-daily/ubuntu](http://ppa.launchpad.net/mpstark/elementary-tweaks-daily/ubuntu) zesty InRelease
Get:16 [https://mega.nz/linux/MEGAsync/xUbuntu_17.04](https://mega.nz/linux/MEGAsync/xUbuntu_17.04) ./ Release [988 B]         
Hit:17 [http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu](http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu) zesty InRelease 
Hit:18 [http://ppa.launchpad.net/papirus/papirus/ubuntu](http://ppa.launchpad.net/papirus/papirus/ubuntu) zesty InRelease         
Ign:19 [http://ppa.launchpad.net/philip.scott/elementary-tweaks/ubuntu](http://ppa.launchpad.net/philip.scott/elementary-tweaks/ubuntu) zesty InRelease
Hit:20 [http://ppa.launchpad.net/snwh/pulp/ubuntu](http://ppa.launchpad.net/snwh/pulp/ubuntu) zesty InRelease               
Hit:21 [http://ppa.launchpad.net/teejee2008/ppa/ubuntu](http://ppa.launchpad.net/teejee2008/ppa/ubuntu) zesty InRelease          
Err:23 [http://ppa.launchpad.net/mpstark/elementary-tweaks-daily/ubuntu](http://ppa.launchpad.net/mpstark/elementary-tweaks-daily/ubuntu) zesty Release
  404  Not Found
Err:24 [http://ppa.launchpad.net/philip.scott/elementary-tweaks/ubuntu](http://ppa.launchpad.net/philip.scott/elementary-tweaks/ubuntu) zesty Release
  404  Not Found
Reading package lists... Done                       
E: The repository 'http://ppa.launchpad.net/mpstark/elementary-tweaks-daily/ubuntu zesty Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/philip.scott/elementary-tweaks/ubuntu zesty Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.


---

### Post by Frogs Hair on 2017-10-16
I'm not sure there is much you can do considering the PPA is for an unsupported release of Ubuntu.
[https://launchpad.net/~mpstark/+archive/ubuntu/elementary-tweaks-daily/](https://launchpad.net/~mpstark/+archive/ubuntu/elementary-tweaks-daily/)

---

### Post by Hasimir on 2017-10-17
In theory this was fixed by modifying the PPA properties to read "xenial".
But I guess some recent update (either in the Tweak tool or in Ubuntu itself) closed that backdoow :(

Is there no other way to modify the settings in Pantheon-Files?
One think I noticed is that, now, the system tells me that there is "no schema" associated with that file manager settings.
So even when I manually run a command such as
> [COLOR=#242729][FONT=Consolas]gsettings set org.pantheon.files.preferences single-click false[/FONT][/COLOR]
what I get is this error
> No such schema &#8220;org.pantheon.files.preferences&#8221;

Is there a different command that might work / be compatible with my system?

---

### Post by Frogs Hair on 2017-10-17
If there is no schema there is no way to edit. The schemas are stored in various folders in the file system though I don't know of an application to edit them with even if there were an older one no longer recognized.

---

### Post by Hasimir on 2018-02-17
I've found out that the daily version of Pantheon-Files should store its schema for the one-click function in this path **io.elementary.files.preferences.single-click**
but when I type
**sudo gsettings set io.elementary.files.preferences.single-click**
I get a message explaining how to use gsettings ... problem is, the explanation is not clear at all :P
```

Usage:
  gsettings [--schemadir SCHEMADIR] set SCHEMA[:PATH] KEY VALUE

Set the value of KEY to VALUE

Arguments:
  SCHEMADIR A directory to search for additional schemas
  SCHEMA    The name of the schema
  PATH      The path, for relocatable schemas
  KEY       The key within the schema
  VALUE     The value to set

```

---

### Post by Hasimir on 2018-02-17
Solved!
In my Ubuntu installation the real position of the Pantheon FiIes schema is this : **/usr/share/glib-2.0/schemas/io.elementary.files.gschema.xml**
I edited (as root) the default key for the one-click setting, then restarted the system, and it worked :D

I found the location of the file thanks to this other thread: [https://ubuntuforums.org/showthread.php?t=2385206&p=13740803#post13740803](https://ubuntuforums.org/showthread.php?t=2385206&p=13740803#post13740803)

---

