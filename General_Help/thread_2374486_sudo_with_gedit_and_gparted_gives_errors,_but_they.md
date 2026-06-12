---
title: "sudo with gedit and gparted gives errors, but they work without sudo"
date: 2017-10-16
forum: General Help
---

### Post by sdowney717 on 2017-10-16
I need to edit fstab file. I usually just do 'sudo gedit /etc/fstab'
So what can I do ?
I tried sudo su, I tried gksu.```

root@scott-MS-7596:/home/scott# sudo gedit /etc/fstab
No protocol specified
Unable to init server: Could not connect: Connection refused

(gedit:5058): Gtk-WARNING **: cannot open display: :0
root@scott-MS-7596:/home/scott# 


```

---

### Post by Perfect Storm on 2017-10-16
Try with
```
sudo -H
```
instead.

---

### Post by sdowney717 on 2017-10-16
??
```


root@scott-MS-7596:/home/scott# sudo -H gedit 
No protocol specified
Unable to init server: Could not connect: Connection refused

(gedit:5268): Gtk-WARNING **: cannot open display: :0
root@scott-MS-7596:/home/scott# sudo -H gedit /etc/fstab
No protocol specified
Unable to init server: Could not connect: Connection refused

(gedit:5273): Gtk-WARNING **: cannot open display: :0
root@scott-MS-7596:/home/scott# sudo -H
usage: sudo -h | -K | -k | -V
usage: sudo -v [-AknS] [-g group] [-h host] [-p prompt] [-u user]
usage: sudo -l [-AknS] [-g group] [-h host] [-p prompt] [-U user] [-u user]
            [command]
usage: sudo [-AbEHknPS] [-r role] [-t type] [-C num] [-g group] [-h host] [-p
            prompt] [-T timeout] [-u user] [VAR=value] [-i|-s] [<command>]
usage: sudo -e [-AknS] [-r role] [-t type] [-C num] [-g group] [-h host] [-p
            prompt] [-T timeout] [-u user] file ...
root@scott-MS-7596:/home/scott# 
```
```

root@scott-MS-7596:/home/scott# sudo -H gparted
Created symlink /run/systemd/system/-.mount &#8594; /dev/null.
Created symlink /run/systemd/system/home.mount &#8594; /dev/null.
Created symlink /run/systemd/system/run-user-0.mount &#8594; /dev/null.
Created symlink /run/systemd/system/run-user-1000.mount &#8594; /dev/null.
Created symlink /run/systemd/system/run-user-121.mount &#8594; /dev/null.
Created symlink /run/systemd/system/tmp.mount &#8594; /dev/null.
No protocol specified

(gpartedbin:5386): Gtk-WARNING **: cannot open display: :0
Removed /run/systemd/system/-.mount.
Removed /run/systemd/system/home.mount.
Removed /run/systemd/system/run-user-0.mount.
Removed /run/systemd/system/run-user-1000.mount.
Removed /run/systemd/system/run-user-121.mount.
Removed /run/systemd/system/tmp.mount.
root@scott-MS-7596:/home/scott#
```

---

### Post by deadflowr on 2017-10-16
Why?
You are already root.

---

### Post by sdowney717 on 2017-10-16
> **deadflowr said:**
> Why?
You are already root.

it did not matter, I tried not as root, tried as root, they dont run.
I am saying I have a real problem here.
Can you run these with root privileges?

```

root@scott-MS-7596:/home/scott# gedit
No protocol specified
Unable to init server: Could not connect: Connection refused

(gedit:7138): Gtk-WARNING **: cannot open display: :0
```

```
root@scott-MS-7596:/home/scott# gparted
Created symlink /run/systemd/system/-.mount &#8594; /dev/null.
Created symlink /run/systemd/system/home.mount &#8594; /dev/null.
Created symlink /run/systemd/system/media-scott-1ca42e1a\x2dc943\x2d4755\x2db8e5\x2da9a6e91f4ed6.mount &#8594; /dev/null.
Created symlink /run/systemd/system/run-user-0.mount &#8594; /dev/null.
Created symlink /run/systemd/system/run-user-1000.mount &#8594; /dev/null.
Created symlink /run/systemd/system/run-user-121.mount &#8594; /dev/null.
Created symlink /run/systemd/system/tmp.mount &#8594; /dev/null.
No protocol specified

(gpartedbin:7193): Gtk-WARNING **: cannot open display: :0
Removed /run/systemd/system/-.mount.
Removed /run/systemd/system/home.mount.
Removed /run/systemd/system/media-scott-1ca42e1a\x2dc943\x2d4755\x2db8e5\x2da9a6e91f4ed6.mount.
Removed /run/systemd/system/run-user-0.mount.
Removed /run/systemd/system/run-user-1000.mount.
Removed /run/systemd/system/run-user-121.mount.
Removed /run/systemd/system/tmp.mount.
root@scott-MS-7596:/home/scott# 

```

I can run gedit without sudo privileges. But how can I edit fstab without using gedit? And besides it should work.

---

### Post by deadflowr on 2017-10-16
So you meant the launchers work like normal, then.
( i was guessing you meant typing something like "gedit /etc/fstab" was working)
Okay,
have you looked over this thread
[https://ubuntuforums.org/showthread.php?t=2367294]("https://ubuntuforums.org/showthread.php?t=2367294")

---

### Post by sdowney717 on 2017-10-16
> **deadflowr said:**
> So you meant the launchers work like normal, then.
( i was guessing you meant typing something like "gedit /etc/fstab" was working)
Okay,
have you looked over this thread
[https://ubuntuforums.org/showthread.php?t=2367294]("https://ubuntuforums.org/showthread.php?t=2367294")

Hi, that does work, no errors now, so they will fix this?```

scott@scott-MS-7596:~$ gedit

scott@scott-MS-7596:~$ xhost +si:localuser:root
localuser:root being added to access control list
scott@scott-MS-7596:~$ sudo gedit
[sudo] password for scott: 
scott@scott-MS-7596:~$ 
```

---

### Post by Chanath on 2017-10-16
Isn't [COLOR=#000000][FONT=&quot]xhost +si:localuser:root just a workaround for Wayland? [/FONT][/COLOR]

---

### Post by ajgreeny on 2017-10-16
If you have become used to using sudo to start GUI programs as root you may have changed the ownership of some of the files in your home which then may cause BIG problems for you and can make it impossible to login as user.

**YOU SHOULD NOT USE sudo WITH GUI PROGRAMS; IT IS ASKING FOR PROBLEMS !**
Sorry for shouting but it is an important lesson that you must learn for your own sake, and as Artificial Intelligence said above, use **sudo -H **instead.

I wonder if your problems with gedit are a result of using sudo for GUI programs in the past?

---

### Post by sdowney717 on 2017-10-16
> **ajgreeny said:**
> If you have become used to using sudo to start GUI programs as root you may have changed the ownership of some of the files in your home which then may cause BIG problems for you and can make it impossible to login as user.

**YOU SHOULD NOT USE sudo WITH GUI PROGRAMS; IT IS ASKING FOR PROBLEMS !**
Sorry for shouting but it is an important lesson that you must learn for your own sake, and as Artificial Intelligence said above, use **sudo -H **instead.

I wonder if your problems with gedit are a result of using sudo for GUI programs in the past?

It did this immediately upon a fresh install, this was not an upgrade from 16.04.
I wanted to look at the drives and thought to run sudo gparted, and it immediately gave those errors.

I did install gksu, but on 16.04, I always was using sudo with gedit for a long time.

---

### Post by sdowney717 on 2017-10-18
Trying method 2, will it work? I wont know until I reboot.

```

Method 2: Globally in /etc/profile
Add the following to /etc/profile

export XAUTHORITY=/home/non-root-usersname/.Xauthority
This will permanently allow root to connect to a non-root user's X server.

Or, merely specify a particular app:

export XAUTHORITY=/home/usersname/.Xauthority kwrite
(to allow root to access kwrite, for instance.)
```

[https://wiki.archlinux.org/index.php/Running_X_apps_as_root](https://wiki.archlinux.org/index.php/Running_X_apps_as_root)

Here is my profile file now, with the added line at bottom

```
# /etc/profile: system-wide .profile file for the Bourne shell (sh(1))
# and Bourne compatible shells (bash(1), ksh(1), ash(1), ...).

if [ "${PS1-}" ]; then
  if [ "${BASH-}" ] && [ "$BASH" != "/bin/sh" ]; then
    # The file bash.bashrc already sets the default PS1.
    # PS1='\h:\w\$ '
    if [ -f /etc/bash.bashrc ]; then
      . /etc/bash.bashrc
    fi
  else
    if [ "`id -u`" -eq 0 ]; then
      PS1='# '
    else
      PS1='$ '
    fi
  fi
fi

if [ -d /etc/profile.d ]; then
  for i in /etc/profile.d/*.sh; do
    if [ -r $i ]; then
      . $i
    fi
  done
  unset i
fi

export XAUTHORITY=/home/scott/.Xauthority
```

---

### Post by rbmorse on 2017-10-18
Are you using the Wayland compositor?  I'm using Gnome on X and can run gedit with root permissions using the gksu package.

---

### Post by zika on 2017-10-19
> **sdowney717 said:**
> I always was using sudo with gedit for a long time.That does not make it less a mistake (serious one) anyhow... ;)

---

### Post by sdowney717 on 2017-10-19
> **rbmorse said:**
> Are you using the Wayland compositor?  I'm using Gnome on X and can run gedit with root permissions using the gksu package.

I dont think I am.

gksu is broke, when it asks for the password, you can not type it into the box, see I typed in my password and it shows up in the terminal instead.

If you dont sudo gedit, then what do you do?

---

### Post by ubname on 2017-10-19
> **sdowney717 said:**
> 

If you dont sudo gedit, then what do you do?


sudo nano /etc/fstab


or use the software interface

not saying that gksudo should not work

---

### Post by sdowney717 on 2017-10-19
> **ubname said:**
> sudo nano /etc/fstab


or use the software interface

not saying that gksudo should not work
have you tried gksu? try it and see.

nano is not very friendly looking to use like gedit.

What is the software interface?

And doing method 2 did not work to grant to root privilege for graphical programs.
Say you want to modify an obscure system config file, likely there wont be any software interface.

---

### Post by sdowney717 on 2017-10-19
Actually I have started using nano, and it is not too bad. 
Can copy and paste, but cut and shift to end lines does not work, unless you use cntrl shortcuts.

I did solve the sudo synaptic or sudo anything issue for graphical use at bootup.

I created a shell script made it executable. Then set it to start up in system startup programs.
```

#!/bin/bash
xhost +local:
xhost +si:localuser:root
```

on sudo and guis, he makes the point using nautilus with sudo is easier. I agree.
Explains it all here and why to be careful.

[https://beamtic.com/sudo-and-guis](https://beamtic.com/sudo-and-guis)

---

### Post by rrnbtter on 2017-10-19
Greetings,
i am a "my computer, my way" type of person.  However, using sudo with graphical programs can cause some serious issues.  Most important is that it can change permissions in the Home directory and make life unmanageable. In addition the problem will persist into a subsequent reinstall if you use a separate reusable Home partition as I do.
So you have a bunch of screwed up permissions.  You run all kinds of chmod scripts and nothing fixes it. 
Solution:  don't use sudo with GUI programs without the -H option. How hard can it be to type sudo -H as opposed to sudo. 

Solution #2: Be patient , they will get these x11 apps ported to wayland in time. ................or not!


If this post sounds like repetition it is because there is only one answer. If all else fails follow the directions.

---

### Post by jbicha on 2017-10-19
Please do not use sudo to run gedit or nautilus. Instead use the gvfs admin backend (introduced in Ubuntu 17.04).

Just use **admin://** before the file name you want to access with elevated privileges.

For instance, to change the grub bootloader config, open

```

admin:///etc/default/grub

```

---

### Post by cariboo on 2017-10-19
Moved to General Help, as this may help other members

---

