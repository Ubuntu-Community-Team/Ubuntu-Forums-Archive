---
title: "gksudo gedit won't open anything but right click open with gedit does."
date: 2008-06-12
forum: General Help
---

### Post by trendal.toews on 2008-06-12
Somebody help me please before I pull out my hare.](*,)

In the process of trying to get some videos to play gedit stopped working.

When I go [COLOR="DeepSkyBlue"]gksudo gedit /etc/apt/sources.list[/COLOR] in terminal it just gives me a blank stare until hit ctrl-C .  If I browse to that file and go right click open with gedit it will open fine. But I want to edit the file.  What the scoop did I break????

Using Hardy and lovin' it...... till now.

Thank you

---

### Post by drs305 on 2008-06-12
> **KatmanHH said:**
> If I browse to that file and go right click open with gedit it will open fine. But I want to edit the file.  What the scoop did I break????

Thank you

don't know - maybe the file is locked open by some process. but if you can't edit it with the right click and gedit, open nautilus as root, then right click and it should open gedit with the ability to edit and save the file. if that doesn't work i would expect the problem is with the status of the file and not an issue with gedit.

```
gksudo nautilus
```

---

### Post by avtolle on 2008-06-12
Or, if you can stand to use a non-graphical editor```
sudo nano /etc/apt/sources.list
``` which will open the file for editing. Save=^o, <Enter>, ^x to exit.

---

### Post by trendal.toews on 2008-06-12
same result with gksudo nautilus.  Works for a little and then the pointer changes back to an arrow.  Somehow I must have lost the ability or permission to edit those files.  Because I can view them fine.  

So next.....:confused:

---

### Post by trendal.toews on 2008-06-12
> **avtolle said:**
> Or, if you can stand to use a non-graphical editor```
sudo nano /etc/apt/sources.list
``` which will open the file for editing. Save=^o, <Enter>, ^x to exit.

Already tried that one but it will open but then locks up cant navigate or edit and must force close terminal and reopen.

---

### Post by drs305 on 2008-06-12
Do you have the ability to execute any sudo functions?

Here are a couple of things you might check if it might be a sudo problem:

Are you listed part of the **admin** group (you should see admin):
```
groups *username*
```

Is your hosts file okay. The line 127.0.1.1 should just have your username attached (e.g. 127.0.1.1 computername):
```
sudo cat /etc/hosts
```

---

### Post by aysiu on 2008-06-12
Can you post the output of these commands? ```
groups
cd /etc/apt
ls -al
```

---

### Post by trendal.toews on 2008-06-12
groups

tt adm dialout cdrom floppy audio dip video plugdev fuse lpadmin admin


cd /etc/apt
ls -al

total 60
drwxr-xr-x   4 root root  4096 2008-06-12 13:47 .
drwxr-xr-x 135 root root 12288 2008-06-12 13:54 ..
drwxr-xr-x   2 root root  4096 2008-05-09 12:42 apt.conf.d
-rw-------   1 root root     0 2008-04-22 10:49 secring.gpg
-rw-r--r--   1 root root  3151 2008-06-12 13:31 sources.list
drwxr-xr-x   2 root root  4096 2008-05-28 09:24 sources.list.d
-rw-r--r--   1 root root  3151 2008-06-12 13:31 sources.list.save
-rw-r--r--   1 root root  3151 2008-06-12 12:55 sources.old
-rw-------   1 root root  1200 2008-06-11 13:23 trustdb.gpg
-rw-r--r--   1 root root  6713 2008-06-12 13:47 trusted.gpg
-rw-r--r--   1 root root  8274 2008-06-11 13:23 trusted.gpg~


Is that what you wanted?

---

### Post by aysiu on 2008-06-12
Yeah, that looks good to me. Try the second command drs305 gave.

---

### Post by trendal.toews on 2008-06-12
> **drs305 said:**
> Do you have the ability to execute any sudo functions?

Here are a couple of things you might check if it might be a sudo problem:

Are you listed part of the **admin** group (you should see admin):
```
groups *username*
```

Is your hosts file okay. The line 127.0.1.1 should just have your username attached (e.g. 127.0.1.1 computername):
```
sudo cat /etc/hosts
```


Yes and Yes to those questions

---

### Post by unutbu on 2008-06-12
```
cd /root
ls -la --sort=time 
```

Has your .bashrc, .profile changed since the last time gksudo worked? What files have changed most recently? Might any of them be the culprit?

---

### Post by trendal.toews on 2008-06-12
> **unutbu said:**
> ```
cd /root
ls -la --sort=time 
```

Has your .bashrc, .profile changed since the last time gksudo worked? What files have changed most recently? Might any of them be the culprit?

.bashrc or .profile hasent changed.
ls -la --sort=time
total 76
drwx------  2 root root 4096 2008-06-12 13:49 .gconfd
drwxr-xr-x 14 root root 4096 2008-06-12 13:49 .
-rw-r--r--  1 root root 1825 2008-06-12 13:49 .recently-used.xbel
drwx------  3 root root 4096 2008-06-12 13:48 .synaptic
drwx------  3 root root 4096 2008-06-12 13:06 .gconf
drwxr-xr-x  3 root root 4096 2008-06-11 11:10 .cache
drwx------  3 root root 4096 2008-06-11 11:10 .config
drwxr-xr-x  3 root root 4096 2008-06-11 11:10 .local
drwx------  4 root root 4096 2008-06-09 15:18 .gnome2
drwxr-xr-x  3 root root 4096 2008-06-09 15:18 .nautilus
drwxr-xr-x  2 root root 4096 2008-06-09 15:18 Desktop
drwx------  2 root root 4096 2008-06-05 11:20 .aptitude
drwxr-xr-x 21 root root 4096 2008-06-04 08:46 ..
-rw-r--r--  1 root root  947 2008-05-14 11:05 .nvidia-settings-rc
drwx------  2 root root 4096 2008-05-09 12:52 .gnome2_private
-rw-------  1 root root 1024 2008-05-09 12:41 .rnd
drwxr-xr-x  2 root root 4096 2008-04-22 11:06 .wapi
-rw-r--r--  1 root root 2227 2007-10-20 04:51 .bashrc
-rw-r--r--  1 root root  141 2007-10-20 04:51 .profile

---

### Post by unutbu on 2008-06-12
Try System>Administration>System Log.
Look in messages -- near the end of the file -- for anything that looks like an error.

---

### Post by trendal.toews on 2008-06-12
> **drs305 said:**
> Do you have the ability to execute any sudo functions?

Yes I do.  Example sudo apt-get update works fine.

---

### Post by trendal.toews on 2008-06-12
> **unutbu said:**
> Try System>Administration>System Log.
Look in messages -- near the end of the file -- for anything that looks like an error.


The only thing like an error that I can see relates to trying to play a .mov file unsuccessfully, which is what prompted the tweaking which broke the gedit. At least gedit broke in somewhat the same timeframe.


The last time gedit worked right I had entered sudo gedit into terminal and hit enter.  It opened a blank page and then a few minutes later I went to open uhh cant' remember what file??? But it didn't open at all.

---

### Post by drs305 on 2008-06-12
> **KatmanHH said:**
> The last time gedit worked right I had entered sudo gedit into terminal and hit enter.  It opened a blank page and then a few minutes later I went to open uhh cant' remember what file??? But it didn't open at all.

There has long been a discussion about sudo vs gksudo. One of the arguments for using gksudo was that sudo could mess up permissions when used with a gui-based program.

Well, since we haven't tried it yet:
```
sudo cat /etc/sudoers
```

](*,)

---

### Post by trendal.toews on 2008-06-12
Well, since we haven't tried it yet:
```
sudo cat /etc/sudoers
```

](*,)[/QUOTE]

Okaaay, so what does this mean?????

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults	env_reset

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

I'm in deeper than I've been before, which is never a bad thing but anyways what do I do know??

---

### Post by drs305 on 2008-06-12
> **KatmanHH said:**
>  this mean?????

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults	env_reset



Well, my lines as above show something different and I believe are the standard lines in sudoers:
```

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Defaults

# Defaults
**Defaults !lecture,tty_tickets,!fqdn**


```

You might want to save your sudoers file and then modify it as above:
```

sudo cp /etc/sudoers /etc/sudoers.bak
export EDITOR=gedit
sudo -E visudo

```

---

### Post by trendal.toews on 2008-06-12
You might want to save your sudoers file and then modify it as above:
```

sudo cp /etc/sudoers /etc/sudoers.bak
export EDITOR=gedit && sudo -E visudo

```[/QUOTE]

first command works 

second command give the same results as sudo gedit.  Nothing but a blinking cursor until you hit ctrl-c

---

### Post by drs305 on 2008-06-12
> **KatmanHH said:**
> You might want to save your sudoers file and then modify it as above:
```

sudo cp /etc/sudoers /etc/sudoers.bak
export EDITOR=gedit && sudo -E visudo

```


You don't have to use gedit - my bad. You can edit it with the native editor.
```
sudo visudo
```

I think it's vi.  If you aren't familiar with it:
Move the cursor to the line you want to edit.
Hit Insert.
Type or paste the new line.
Hit ESC.
Delete key to erase the remainder of the old line.
If you need to delete an entire line, put the curson on it and type: "**dd**"
Type "**:wq**" then Enter to save.
To abort the edit: "**:q**" Enter.
If you get lost, hit ESC a couple of times then "**:q**" and try again ;-)

---

### Post by trendal.toews on 2008-06-12
okay drs305 I followed you there as much as I could but I still cant use gedit.

---

### Post by trendal.toews on 2008-06-13
This is totally off topic but I just must say it.

V  ista 
I  s
S  o
T  otally
A  ssinine

---

### Post by trendal.toews on 2008-06-16
Well I went off the deep end. Backed her up and reinstalled.  Fixed the problem.  Just hate to admit defeat.:oops:

Thanks for the help.

---

### Post by cooltd825 on 2008-07-01
> **KatmanHH said:**
> Well I went off the deep end. Backed her up and reinstalled.  Fixed the problem.  Just hate to admit defeat.:oops:

Thanks for the help.

damn it.....  I was hoping this would get fixed.  I'm having the same issue, and I'd really really like to not to a full reinstall.  

don't get me wrong, Nano works just fine, but some programs prompt for gedit for certain things and then my the installation of whatever program gets screwed over.

---

### Post by mexlinux on 2008-09-29
I'm having this exact problem, any other clues?

It's just gedit the one that is not working....

---

