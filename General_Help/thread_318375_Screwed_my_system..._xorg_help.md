---
title: "Screwed my system... xorg help"
date: 2006-12-13
forum: General Help
---

### Post by telovoyagarcar on 2006-12-13
I uninstalled Beryl, and i was also trying to use aigxl instead of the plain gxl that i also removed, changed stuff in the xorg.conf file, and a few more files (which i dont even remember their names) that had something to do with video... then i installed the latest version of beryl... 

Now i cant load gnome or anything... the video is totally messed up.
i got to the terminal and saw various xorg.conf.something else files... 
i guess those are backups of the ones before i messed up?...
i tried renaming one that was something like xorg.conf.784373478 to replace the one that does not work.. but still no video..

I have an ATI card...
what can i do to go back???

---

### Post by amd-64 on 2006-12-13
This will regenerate xorg.conf after asking you a few questions. Default answers are safe if you not sure of the answer.

Ctrl-Alt-F1 will get you to a text terminal
login with your user name and password

```
sudo dpkg-reconfigure  xserver-xorg

```

Go back to X11 using: Ctrl-Alt-F7
Kill and restart X:  Ctrl-Alt-Backspace
Your graphical login should be coming up now.

---

### Post by telovoyagarcar on 2006-12-13
ok...
this is what i can do..
start the system in a terminal, login with the root account and then "startx"
That will let me start gnome..
But if i let the system start the default way, it will hang in that very first kind of gray screen that X loads before seeing the login window with the session options and stuff.
It is like if the thing that crashes is the login window... it will never load. 
i think i modified one of those "init.d" files somewhere when i was playing with xgl

---

### Post by amd-64 on 2006-12-14
I am on kde and I do not even know what you use to start gnome. If Beyrl was not uninstalled cleanly, your system may be getting stuck looking for it.

First try to find the changes you made
```
cd /etc/init.d
ls -lsrt 
```
this will sort the files by date, the bottom ones are likely the ones you changed. Depending on the editor you used, there may even be a backup stored with a .bak or a ~ extension. These will have the original dates and won't be at the bottom of the list. 

You should also look for a beyrl startup script in your configuration files.
```
cd /etc
sudo grep -R beyrl *
```

If you absolutely cannot find what changes you made to your init files, you could try a more shotgun approach. 
```
sudo dpkg-reconfigure -a
```
This will reconfigure a lot of packages, it can take a long time on a slow machine. 

Hope this helps

---

### Post by telovoyagarcar on 2006-12-14
Well
I tried with **sudo dpkg-reconfigure -a** and after some time and hundreds of ENTER keys, i still have the same problem.

The login screen shows for like one second and then dissapears .... i get this gray screens with the ubuntu "hourglass" spinning forever... 

Is there a log or anything somewhere that might give me or you a clue of whats going on? 

Thanks

---

### Post by kakalaky on 2006-12-15
Check /var/log/Xorg.0.log and post the output of the following command here:

```
cat /etc/X11/xorg.conf
```

---

### Post by amd-64 on 2006-12-15
If you are getting a graphical output (hourglass) then it is unlikely X11 problem. There should be more information about the error in your /var/log/messages or /var/log/syslog

When this sitution happened to me before, what happened was that some files in my home directory became owned by root and the login could not proceed. Can you check the ownership of files in your home directory.

at a terminal and under your user name: 

cd 
ls -lart | more

Check for any hidden files or folders that you are not owner of. Not sure what names exactly  .Xauthority, .ICEauthority or something similar

if your user name is yx, you can use the following to regain ownership of any of these files

sudo chown -R yx:yx file

---

