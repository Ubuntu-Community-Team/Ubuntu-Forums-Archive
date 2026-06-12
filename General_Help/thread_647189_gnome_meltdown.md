---
title: "gnome meltdown"
date: 2007-12-22
forum: General Help
---

### Post by cancertoast on 2007-12-22
Ok guys, I really have no clue as to what is going on.  I was trying to install beagle and followied the instructions I looked up (and from my limirted exp they would not cause this problem) and rebooted.  All of a sudden I get these popup boxes (along with large-fonted applications, as well as a black wallpaper for my desktop):
```

GConf error: Adding client to server's list failed, CORBA error: IDL:omg.org/CORBA/UNKNOWN:1.0
All further errors shown only on terminal

```

```

An error occurred while loading or saving configuration information for Nautilus. Some of your configuration settings may not work properly.


```

```

An error occurred while loading or saving configuration information for gnome-settings-daemon. Some of your configuration settings may not work properly.


```

```

An error occurred while loading or saving configuration information for evolution-alarm-notify. Some of your configuration settings may not work properly.


```

I get this same error for 'gnome-session', 'nm-applet', 'vino session', 'update-notifier', and 'gnome-panel'.



Does anyone care to lend me a hand?  Otherwise I have no recourse but to do what I know will work for a fact, reformat.

---

### Post by tgilber1 on 2007-12-22
Before reinstalling, try renaming your gconf settings and log out.  Then log back into gnome.  When it finds the gconf settings missing, it will create a new one.

[LIST=1]
[*]From GUI menu bar, click #System#Accessories#Terminal to access terminal to type the following commands
[*]cp ./gconf ./gconf.bak
[*]Log out
[*]Log in
[/LIST]

Hopefully, error messages should be gone.  The old settings are in the .gconf.bak in case you want to revert back to the original settings.
Check to see if old directory is still there if you want with "ls -l ./gconf*

---

### Post by cancertoast on 2007-12-22
The thing is /I have no GUI.  All I have is the CTRL+ALT+F* buttons.

---

### Post by tgilber1 on 2007-12-22
If you do not have a GUI, then follow the same commands except for the first one.

[LIST=1]
[*]Log into system from CLI or CTRL*Fx
[*]cp ./gconf ./gconf.bak
[*]"sudo /etc/init.d/gdm restart" or "sudo shutdown -r now" to reboot
[*]Log in
[/LIST]



> **tgilber1 said:**
> Before reinstalling, try renaming your gconf settings and log out.  Then log back into gnome.  When it finds the gconf settings missing, it will create a new one.

[LIST=1]
[*]From GUI menu bar, click #System#Accessories#Terminal to access terminal to type the following commands
[*]cp ./gconf ./gconf.bak
[*]Log out
[*]Log in
[/LIST]

Hopefully, error messages should be gone.  The old settings are in the .gconf.bak in case you want to revert back to the original settings.
Check to see if old directory is still there if you want with "ls -l ./gconf*

---

### Post by cancertoast on 2007-12-22
running those exact commands did nothing.  I typed:

cp ./gconf ./gconf.bak  and all it said was  

```

cp something something './gconf' no such file or directory

```

Luckily I can still see and use my desktop app shortcuts, at least i dont have to jump from computer to computer to try and figure this out..

---

### Post by torgrot on 2007-12-22
change the file names in the above from cp ./gconf ./gconf.bak to cp ./.gconf ./.gconf.bak  Notice the extra period.

torgrot

---

### Post by cancertoast on 2007-12-22
Unfortunately at this point i think my install is hosed.  I made my way into aptitude somehow and it kept trying to uninstall KDE apps but all i got was errors....  I will try again, however, I think i screwed myself :(  I am booted into windows right now as all I get in linux is CLI.

---

### Post by tgilber1 on 2007-12-22
Check to see if gnome-session is installed

dpkg -l gnome-session

if you do not see ii (installed) before package, you will not be able to log into gnome

sudo apt-get purge gnome-session  # to remove any corrupted files - probably can skip this step

sudo apt-get install gnome-session # a clean start

---

### Post by cancertoast on 2007-12-22
Didn't work.  It wouldnt uninstall or reinstall.  There are a string of kde apps that want to be removed from my system (karbon kate, kdepasswd, etc there are about 14 apps or so in all) and they all give this:
```
 errors encountered while processing exit status 139
```

when i do dpkg -l gnome-session it says it isnt installed/error (not in those exact words).  What do I do next?

---

### Post by tgilber1 on 2007-12-23
> **cancertoast said:**
> Didn't work.  It wouldnt uninstall or reinstall.  There are a string of kde apps that want to be removed from my system (karbon kate, kdepasswd, etc there are about 14 apps or so in all) and they all give this:
```
 errors encountered while processing exit status 139
```

when i do dpkg -l gnome-session it says it isnt installed/error (not in those exact words).  What do I do next?

sudo apt-get install gnome-session

---

### Post by cancertoast on 2007-12-23
It says I already have the latest version.  I have also already run 'sudo apt-get purge'.  On an aside, I have 16 packages in all that are partially installed and I can not seem to get rid of them.  They simply will not uninstall.

When I try and run gnome-session I get this: ```
 (gnome-session:5660) Gtk-WARNING **: cannot open display 
```

---

### Post by tgilber1 on 2007-12-23
> **cancertoast said:**
> It says I already have the latest version.  I have also already run 'sudo apt-get purge'.  On an aside, I have 16 packages in all that are partially installed and I can not seem to get rid of them.  They simply will not uninstall.

When I try and run gnome-session I get this: ```
 (gnome-session:5660) Gtk-WARNING **: cannot open display 
```

Sounds like you deleted your xorg driver.  Check to see if you have X installed by checking with dpkg

dpkg -l xserver* xorg*

If they shoud pn or un, it means that they have been purged or uninstalled.

un = unpacked / not installed (no config files exist)

rc = reinstall required / config files 

pn = purged / not installed (no config files exist)


Paste your dpkg -l into the post.  Also, what kind of video adapter do you have.  Additionally, paste the /var/log/gdm/\:0.log.* files into the post for people to look at.  

Lastly, to fix broken packages, you can do the following:

sudo apt-get -f install <broken-package name> or sudo apt-get -f update (not sure if this one will fix everything, but worth a try)

You could provide a list of broken packages or half-installed.  If you cannot get Ubuntu working soon, It may be your system is too hosed thereby making it worth reinstalling ubuntu.

---

### Post by cancertoast on 2007-12-23
How can i copy and or paste what my console outputs if I dont have x (no GUI interface at all), or post on the forums for that matter.

---

