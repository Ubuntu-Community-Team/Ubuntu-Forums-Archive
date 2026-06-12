---
title: "[SOLVED] gdm fails to start"
date: 2007-07-13
forum: General Help
---

### Post by red777 on 2007-07-13
Help please,
I have kde installed over ubuntu,.I was doing some tinkering with sound card & inadvertently set kde as the default manager,I want to re set to gdm because I can now only boot from live cd,I have tried a few tips from previous posts, ie remove gdm & re installed but it came back with failed to restart gdm.
can anyone help or do I have to do a complete re install

Thanks in advance

---

### Post by red777 on 2007-07-13
here is some info I got from terninal
ubuntu@ubuntu:~$ sudo apt-get remove --purge gdm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  gdm* ubuntu-desktop*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 13.8MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 91544 files and directories currently installed.)
Removing ubuntu-desktop ...
Removing gdm ...
Purging configuration files for gdm ...
Removing user `gdm' ...
Done.
ubuntu@ubuntu:~$ sudo apt-get install ubuntu-desktop gdm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  msttcorefonts
The following NEW packages will be installed:
  gdm ubuntu-desktop
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 1832kB of archives.
After unpacking 13.8MB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main gdm 2.18.1-0ubuntu1 [1814kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main ubuntu-desktop 1.43 [18.1kB]       
Fetched 1832kB in 1m9s (26.3kB/s)                                              
Preconfiguring packages ...
Selecting previously deselected package gdm.
(Reading database ... 91345 files and directories currently installed.)
Unpacking gdm (from .../gdm_2.18.1-0ubuntu1_i386.deb) ...
Selecting previously deselected package ubuntu-desktop.
Unpacking ubuntu-desktop (from .../ubuntu-desktop_1.43_i386.deb) ...
Setting up gdm (2.18.1-0ubuntu1) ...
grep: /etc/X11/default-display-manager: No such file or directory
Adding group `gdm' (GID 118) ...
Done.
Warning: The home dir you specified already exists.
Adding system user `gdm' (UID 109) ...
Adding new user `gdm' (UID 109) with group `gdm' ...
The home directory `/var/lib/gdm' already exists.  Not copying from `/etc/skel'.
adduser: Warning: that home directory does not belong to the user you are currently creating.
 * Reloading GNOME Display Manager configuration...                              * Changes will take effect when all current X sessions have ended.
invoke-rc.d: initscript gdm, action "reload" failed.

Setting up ubuntu-desktop (1.43) ...

---

### Post by deepclutch on 2007-07-13
go to a virtual terminal by pressing ctrl+alt+f1 and login.run "sudo /etc/init.d/gdm restart" it shud work.if ur saying no display it will be another problem.
/etc/X11/default-display-manager:missing?
u shud make as:
```
cd /etc/X11/ ;sudo touch default-display-manager;sudo echo  "/usr/sbin/gdm" >> default-display-manager
```

---

### Post by red777 on 2007-07-13
nope got this
ubuntu@ubuntu:~$ cd /etc/X11/ ;sudo touch default-display-manager;sudo echo  "/usr/sbin/gdm" >> default-display-manager
bash: default-display-manager: Permission denied
ubuntu@ubuntu:/etc/X11$

---

### Post by splintercellguy on 2007-07-13
sudo -s then try again.

---

### Post by deepclutch on 2007-07-13
OK.first make sure a file is whether already there called /etc/X11/default-display-manager?
if not try below :


```
sudo echo "/usr/sbin/gdm" >> /etc/X11/default-display-manager
```restart gdm
```
/etc/init.d/gdm restart
```


Also explain a bit more clearly what happens when u try login in Ubuntu?are u sure it is with gdm?Are u sure display works(GUI)?
if not try my suggestion as below if above step fails :
login at a vte with ur local username and passwd the,
```
startx;gnome-session 
```
^ this will help u login to ur Gnome hopefully.

---

### Post by red777 on 2007-07-13
ubuntu@ubuntu:~$ sudo echo "/usr/sbin/gdm" >> /etc/X11/default-display-manager
bash: /etc/X11/default-display-manager: Permission denied
ubuntu@ubuntu:~$ /etc/init.d/gdm restart
open: Permission denied
 * Stopping GNOME Display Manager...                                            open: Permission denied
                                                                         [ OK ]
open: Permission denied
 * Starting GNOME Display Manager...                                            open: Permission denied
                                                                         [fail]
ubuntu@ubuntu:~$ 

any more options

---

### Post by red777 on 2007-07-13
ubuntu@ubuntu:~$ startx;gnome-session
xauth:  creating new authority file /home/ubuntu/.serverauth.9095
X: user not authorized to run the X server, aborting.
xinit:  Server error.
Couldnt get a file descriptor referring to the console
gnome-session: you're already running a session manager
ubuntu@ubuntu:~$

---

### Post by deepclutch on 2007-07-13
I think gdm is running!press ctrl+alt+F7 ?else  X is not working for U.
OK.u need to run above command as:
```
sudo  startx;gnome-session  
```
try?

---

### Post by red777 on 2007-07-13
ubuntu@ubuntu:~$ startx;gnome-session
xauth:  creating new authority file /home/ubuntu/.serverauth.9095
X: user not authorized to run the X server, aborting.
xinit:  Server error.
Couldnt get a file descriptor referring to the console
gnome-session: you're already running a session manager
ubuntu@ubuntu:~$ sudo  startx;gnome-session
xauth:  creating new authority file /home/ubuntu/.serverauth.9386


Fatal server error:
Server is already active for display 0
        If this server is no longer running, remove /tmp/.X0-lock
        and start again.

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(gnome-session:9414): Gtk-WARNING **: cannot open display:

---

### Post by deepclutch on 2007-07-13
did u pressed CTRL+ALT+F7 to check display is there?

---

### Post by red777 on 2007-07-13
I tried ctrl alt F7 but got nothing,I'm still using the live cd to do everything so that might be an issue.I get as far as the kubuntu splash then everything stops.I'm assuming it's because I don't have kde fully loaded,I used synaptic to download kde & had the option of which type of session to use,but I can't get that far now,everything just stops.I am only guessing that it's because I inadvertently set kdm as default in terminal.I just want to revert to how I had it before if I can.

---

### Post by deepclutch on 2007-07-13
if u want gdm back,trry in a terminal and select gdm as default:
```
sudo dpkg-reconfigure gdm
```

---

### Post by red777 on 2007-07-13
no luck so far,system still wont get past kubuntu splash message,I might just throw in the towel & do a re install

---

