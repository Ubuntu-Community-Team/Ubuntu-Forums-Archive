---
title: "Google Earth in 14.04"
date: 2014-07-15
forum: General Help
---

### Post by RogerDavis on 2014-07-15
I tried to install Google Earth by the following:
---------------------------
[http://www.webupd8.org/2014/04/install-google-earth-in-ubuntu-1404.html](http://www.webupd8.org/2014/04/install-google-earth-in-ubuntu-1404.html)
---------------------------------------------
sudo apt-get install libfontconfig1:i386 libx11-6:i386 libxrender1:i386 libxext6:i386 libgl1-mesa-glx:i386 libglu1-mesa:i386 libglib2.0-0:i386 libsm6:i386
cd /tmp && wget [http://dl.google.com/dl/earth/client/current/google-earth-stable_current_i386.deb](http://dl.google.com/dl/earth/client/current/google-earth-stable_current_i386.deb)
sudo dpkg -i google-earth-stable_current_i386.deb
sudo apt-get install -f
--------------------------------------
It mumbled on for several minutes, downloading and installing LOTS of stuff.  It appeared to be successful, but no icon is present, and I can't launch it in Terminal with any variation of Google-Earth, Google Earth, Earth, etc.

This is a 64 bit machine and Ubuntu, but the above all appear to be 32 bit commands?

So now, there are 3 questions
- If it's a failed install, is all the stuff it put on my drive otherwise useless?
- If useless, how do I get rid of it?
- How do I get Google Earth installed and working???

---

### Post by oldos2er on 2014-07-15
Moved to General Help.

```
google-earth
```

---

### Post by RogerDavis on 2014-07-15
```
roger@roger-desktop:~$ google-earth
google-earth: command not found
roger@roger-desktop:~$ 
```

Actually, I already tried that, along with many other variations.

---

### Post by silex89 on 2014-07-16
> **RogerDavis said:**
> I tried to install Google Earth by the following:
---------------------------
[http://www.webupd8.org/2014/04/install-google-earth-in-ubuntu-1404.html](http://www.webupd8.org/2014/04/install-google-earth-in-ubuntu-1404.html)
---------------------------------------------
sudo apt-get install libfontconfig1:i386 libx11-6:i386 libxrender1:i386 libxext6:i386 libgl1-mesa-glx:i386 libglu1-mesa:i386 libglib2.0-0:i386 libsm6:i386
cd /tmp && wget [http://dl.google.com/dl/earth/client/current/google-earth-stable_current_i386.deb](http://dl.google.com/dl/earth/client/current/google-earth-stable_current_i386.deb)
sudo dpkg -i google-earth-stable_current_i386.deb
sudo apt-get install -f
--------------------------------------
It mumbled on for several minutes, downloading and installing LOTS of stuff.  It appeared to be successful, but no icon is present, and I can't launch it in Terminal with any variation of Google-Earth, Google Earth, Earth, etc.

This is a 64 bit machine and Ubuntu, but the above all appear to be 32 bit commands?

So now, there are 3 questions
- If it's a failed install, is all the stuff it put on my drive otherwise useless?
- If useless, how do I get rid of it?
- How do I get Google Earth installed and working???

Hi there :)

The 32-bit commands you say are, as explained in the WebUpd8 site, multiarch libraries that need to be installed in order to make the app work. It's strange, I just executed the exact same procedure on my machine (64-bit Ubuntu 14.04) and it worked. Maybe trying to download the package again and install it from a folder that your user owns instead of /tmp, like the Downloads folder *could* make a difference...

Repeat the procedure and post the output. I'll see if I can help you.

Kind regards!

EDIT: To answer your questions
1.- If you give up on your installation of Google Earth, then yes...
2.- If you want to remove these libraries, you can issue a sudo apt-get autoremove to delete them safely.
3.- Do what I asked you so I can see the output the terminal gives you.

---

### Post by RogerDavis on 2014-07-16
```
roger@roger-desktop:~$ sudo apt-get install libfontconfig1:i386 libx11-6:i386 libxrender1:i386 libxext6:i386 libgl1-mesa-glx:i386 libglu1-mesa:i386 libglib2.0-0:i386 libsm6:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libglib2.0-0:i386 is already the newest version.
libglu1-mesa:i386 is already the newest version.
libsm6:i386 is already the newest version.
libx11-6:i386 is already the newest version.
libxext6:i386 is already the newest version.
libxrender1:i386 is already the newest version.
libfontconfig1:i386 is already the newest version.
libgl1-mesa-glx:i386 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.

```

```
roger@roger-desktop:~$ cd /tmp && wget http://dl.google.com/dl/earth/client/current/google-earth-stable_current_i386.deb
--2014-07-15 22:45:00--  http://dl.google.com/dl/earth/client/current/google-earth-stable_current_i386.deb
Resolving dl.google.com (dl.google.com)... 74.125.239.9, 74.125.239.3, 74.125.239.0, ...
Connecting to dl.google.com (dl.google.com)|74.125.239.9|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 45684888 (44M) [application/x-debian-package]
Saving to: &#8216;google-earth-stable_current_i386.deb&#8217;

100%[======================================>] 45,684,888  6.85MB/s   in 6.4s   

2014-07-15 22:45:06 (6.85 MB/s) - &#8216;google-earth-stable_current_i386.deb&#8217; saved [45684888/45684888]
```


```
roger@roger-desktop:/tmp$ sudo dpkg -i google-earth-stable_current_i386.deb
Selecting previously unselected package google-earth-stable.
(Reading database ... 238897 files and directories currently installed.)
Preparing to unpack google-earth-stable_current_i386.deb ...
Unpacking google-earth-stable (7.1.2.2041-r0) ...
Setting up google-earth-stable (7.1.2.2041-r0) ...
Processing triggers for man-db (2.6.7.1-1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.54ubuntu1) ...
roger@roger-desktop:/tmp$ 
```


```
roger@roger-desktop:/tmp$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
roger@roger-desktop:/tmp$  
```

All this is MUCH shorter and took MUCH less time than the first time around.

This time it worked!

HOWEVER, the pictures don't work.  They only pop up empty white boxes.  Water bodies aren't outlined.  Any ideas on this?  A year or so ago this was due to not installing a 64 bit version.  I did that, and then everything worked.

Thanks!

---

### Post by silex89 on 2014-07-16
> **RogerDavis said:**
> 
HOWEVER, the pictures don't work.  They only pop up empty white boxes.  Water bodies aren't outlined.  Any ideas on this?  A year or so ago this was due to not installing a 64 bit version.  I did that, and then everything worked.

Thanks!

I'm not entirely sure if I understood what this problem is. I have no issues with my Google Earth at all, it shows everything correctly. You could now try to run it from a terminal and see what the output is. Maybe the content is not being fetched from the internet and that's why you don't see it....

Nice to know you got it working :D

---

### Post by RogerDavis on 2014-07-16
I can explain how to duplicate the problem.  Please make sure the test machine is a 64 bit machine, with 64 bit Ubuntu 14.04.
1) Under "Layers", make sure "Photos" and "Panarama" are selected.  "360 Cities" can be either selected or not, doesn't matter.
2) Enter "Creek Park La Mirada, CA" in Search, click "Search"
3) Notice the two icons, blue on top, red on bottom, on left, but near center screen.
4) Place your cursor over either, see picture title displayed.
5) Left click the icon, see picture displayed.
In my case, the picture window opens, but it's just white, no picture or text at all.

I'm at a different machine now, with a correctly working Google Earth.  I see that the body of water I was checking on earlier on the Linux machine is not outlined here, but I find one that is - Lake Mathews, CA.  Please check this on your Linux 64 bit (Please make sure the test machine is a 64 bit machine, with 64 bit Ubuntu 14.04.) setup, I suspect it might be working ok, maybe.  I know it worked on 12.04 .
1) Under "Layers", make sure "Parks/Recreation Areas > Water Body Outlines" is checked. 
2) Enter "Lake Mathews, CA" in Search, click "Search"
3) Notice the blue outline around the lake (kinda, it misses just a bit).

Please let me know your results on both.

Thanks!

---

### Post by oldos2er on 2014-07-16
A fix for the panoramio not showing pics issue is in posts # 27, 28 and 29 in [this thread]("http://ubuntuforums.org/showthread.php?t=2196304").

---

### Post by RogerDavis on 2014-07-17
Since I never graduated Hogwarts (I keep having to repeat the first year), and occasionally grab the wand by the wrong end and hex myself, I need some detailed help.  You do seem to have all the answers, so I'm hoping you can help me a bit further.

Reading 27,28, and 29, I think I see two options
- reinstall using different incantations
- repair/update/whatever

I'm currently considering that my best bet is to 
-----
- remove the current installation by
sudo apt-get autoremove libfontconfig1:i386 libx11-6:i386 libxrender1:i386 libxext6:i386 libgl1-mesa-glx:i386 libglu1-mesa:i386 libglib2.0-0:i386 libsm6:i386
?   sudo apt-get autoremove google-earth-stable_current_i386.deb
?????   sudo apt-get autoremove -f

and where would    cd /tmp && wget [http://dl.google.com/dl/earth/client...rrent_i386.deb](http://dl.google.com/dl/earth/client...rrent_i386.deb)    fit in?  not?

Does all the above actually remove the 32 bit GE and all the unneeded 32 bit support?
-----
Then follow instructions in #28
sudo apt-get install libfreeimage3
cd /opt/google/earth/free
sudo tar xvf ~/Downloads/ge7.1.1.1580-0.x86_64-new-qt-libs-debian7-ubuntu12.tar.xz

Is this all I need to install a "fixed" version?  Or am I missing something?
-----

Thanks! to you, Sir Dumbledore !

---

### Post by mc4man on 2014-07-17
> **RogerDavis said:**
> 
and where would    cd /tmp && wget [http://dl.google.com/dl/earth/client...rrent_i386.deb](http://dl.google.com/dl/earth/client...rrent_i386.deb)    fit in?  not?


Doesn't fit in this fix at all. The 'fixed' libs are 64 bit so you need to 
remove the 32 bit install
install the 64 bit version of goggle-earth
Then apply the fix.

As far as installing the 64 bit version, re-read post 27 again from the top..

---

### Post by RogerDavis on 2014-07-18
- remove the current installation by the below?  Or maybe just the first and second line?  Also, I pieced these together, so I'm not sure I have the syntax right.
```
sudo apt-get autoremove libfontconfig1:i386 libx11-6:i386 libxrender1:i386 libxext6:i386 libgl1-mesa-glx:i386 libglu1-mesa:i386 libglib2.0-0:i386 libsm6:i386
? sudo apt-get autoremove google-earth-stable_current_i386.deb
????? sudo apt-get autoremove -f
```

Would 
```
cd /tmp && wget http://dl.google.com/dl/earth/client...rrent_i386.deb
```
fit into the above process anywhere, or not?

Delete status.backup and /usr/bin/google-earth.old after all the other stuff from #27 is done?

And since the instruction is to start it with ```
google-earth
``` does this process not install an icon?

---

