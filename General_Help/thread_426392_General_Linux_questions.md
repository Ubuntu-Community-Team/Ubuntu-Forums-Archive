---
title: "General Linux questions"
date: 2007-04-28
forum: General Help
---

### Post by extension on 2007-04-28
I am somewhat new to Linux and am trying to understand some basic concepts and was hoping someone could offer me some more insight.

1) How do I add a command to run at startup? I know with Gnome I can use the startup manager but I am using OpenBox on one of my  PC's, is there a generic linux way to add commands? 

  The commands I want to add are to mount a drive, share it and then start remote software. They all need to be run as root. 

2) How do I share files? Is it through Samba? From the tutorials I have read Samba *appears* like a Microsoft interoperability application but is it also the Linux way to share files?

3) Is there a single place where file associations are stored?

4) Is there an easy way to know where executables are located? I have LIRC installed but how do I know where the lircd executable exists?

5) Is there a way to see what libraries an executable depends on? Sometimes Ill start an application with a missing library and the app just crashes at runtime, it would be nice to see a list of dependencies for the application instead of having to scour the new looking for clues.

Any help with any of these questions would be greatly appreciated.

---

### Post by murlosad on 2007-04-28
I can answer a few of these for you.

1) to mount a drive you can add the mount command to /etc/fstab, which is where your boot process looks for mountable volumes when you startup your pc.

2) if you are sharing over a network Samba is the way to go, especially if you are sharing to an XP computer, but you can use it to share to other *nix boxes.

3) not sure

4) type 'which command' i.e. 'which lircd' into a terminal

5) the best way to install anything is throught a package manager (synaptic or apt-get or something similar) which will handle the dependencies for you, failing that there is a command that will show you package dependencies, but I can't remember off the top of my head.

Hope this helps a bit

---

### Post by extension on 2007-04-28
Thank you, those were very helpful answers. 

A follow up to question 1 is how do I run arbitrary commands at startup as root not using the Gnome interface?

I would like to run:

lirdc -d /dev/lirc0

---

### Post by murlosad on 2007-04-28
did some searching... you should be able to use a script called .xsession which resides in your home folder. if it is not there you should be able to create it.  Then you can add the programs that you want to run. Now these programs will only run once you've logged in to X via gdm or kdm or whatever. for most purposes this should be fine.

Hope this helps

the page I got that from is [http://icculus.org/openbox/2/faq.php](http://icculus.org/openbox/2/faq.php) which looks like it has lots more info about openbox, might be worth a read through.

---

### Post by roachk71 on 2007-04-28
Another way to add a startup command (for graphical applications) is by appending them to your .xinitrc script, in your home directory...At least it works in Damn Small Linux. Just be sure to end the command with an ampersand.

NOTE: This works in DSL due to the fact a graphical login isn't used by default, so it may have other effects if one is used. So for this method to work as described, you may have to edit your .bash_profile script to match, along with runlevel changes (such as using sysv-rc-conf to disable X startup.) I don't recommend it if your Linux experience is lacking...

---

### Post by eggdeng on 2007-04-28
> **extension said:**
> Thank you, those were very helpful answers. 
A follow up to question 1 is how do I run arbitrary commands at startup as root not using the Gnome interface?
I would like to run:
lirdc -d /dev/lirc0

It is very easy to create a little shell script, as follows

```
sudo gedit /etc/init.d/myscript.sh
```

Insert the file header followed by your command

```
#!/bin/bash
lirdc -d /dev/lirc0
```

Save the file and make it executable
```
sudo chmod +x /etc/init.d/myscript.sh
```

As you have saved the file to the init.d directory it will run as root on startup. An even quicker way to do this is as suggested by the previous poster. Open the file /etc/init.d/rc.local 

```
sudo gedit /etc/init.d/rc.local 
```
append your command with a trailing ampersand
```
lirdc -d /dev/lirc0 &
```
and save the file.

---

