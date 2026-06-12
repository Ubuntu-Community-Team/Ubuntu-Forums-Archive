---
title: "When would I received a bug fix that is already published."
date: 2022-07-07
forum: General Help
---

### Post by debasish-raychawdhuri on 2022-07-07
Hi,

I am running Ubuntu 22.04 LTS and I am facing this bug [https://bugs.launchpad.net/ubuntu/+source/gtk4/+bug/1971532](https://bugs.launchpad.net/ubuntu/+source/gtk4/+bug/1971532) which is fixed. I found this page [https://launchpad.net/ubuntu/+source/gtk4](https://launchpad.net/ubuntu/+source/gtk4) that says a higher version with the bug fix is already in the updates repo. When and how would I receive this update? This is extremely important for the kind of work I do. 

Thanks

---

### Post by deadflowr on 2022-07-08
Since that's only the source you would need to look at what packages you have that built from it.
Probably open a terminal and run
```
dpkg -l | grep gtk-4
```
It's possible the fixed versions are already updated.

If not, you can run either Software Updater, or try updating through the terminal by running
```
sudo apt update
sudo apt full-upgrade
```

Sometimes updates may take a minute as Ubuntu has an implementation called phased updates
See more on phased-updates here: [https://wiki.ubuntu.com/PhasedUpdates]("https://wiki.ubuntu.com/PhasedUpdates")
Though looking at it none of the current SRU packages being phase updated seem be related to gtk4: [https://people.canonical.com/~ubuntu-archive/phased-updates.html]("https://people.canonical.com/~ubuntu-archive/phased-updates.html")

---

### Post by debasish-raychawdhuri on 2022-07-08
Seems I still did not get the updated version.

> $ dpkg -l | grep gtk-4
ii  gir1.2-gtk-4.0:amd64                       4.6.2+ds-1ubuntu3                       amd64        GTK graphical user interface library -- gir bindings
ii  gir1.2-javascriptcoregtk-4.0:amd64         2.36.3-0ubuntu0.22.04.1                 amd64        JavaScript engine library from WebKitGTK - GObject introspection data
ii  libgtk-4-1:amd64                           4.6.2+ds-1ubuntu3                       amd64        GTK graphical user interface library
ii  libgtk-4-bin                               4.6.2+ds-1ubuntu3                       amd64        programs for the GTK graphical user interface library
ii  libgtk-4-common                            4.6.2+ds-1ubuntu3                       all          common files for the GTK graphical user interface library
ii  libjavascriptcoregtk-4.0-18:amd64          2.36.3-0ubuntu0.22.04.1                 amd64        JavaScript engine library from WebKitGTK
ii  libwebkit2gtk-4.0-37:amd64                 2.36.3-0ubuntu0.22.04.1                 amd64        Web content engine library for GTK





> $ sudo apt update
Hit:1 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) jammy InRelease
Hit:2 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) jammy-updates InRelease              
Hit:3 [https://download.docker.com/linux/ubuntu](https://download.docker.com/linux/ubuntu) jammy InRelease                 
Hit:4 [https://brave-browser-apt-release.s3.brave.com](https://brave-browser-apt-release.s3.brave.com) stable InRelease          
Hit:5 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) jammy-backports InRelease            
Hit:6 [https://dl.google.com/linux/chrome/deb](https://dl.google.com/linux/chrome/deb) stable InRelease                  
Hit:7 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security InRelease               
Hit:8 [http://apt.insync.io/ubuntu](http://apt.insync.io/ubuntu) jammy InRelease                     
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
All packages are up to date.




> 
$ sudo apt full-upgrade
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  chromium-codecs-ffmpeg-extra gnome-video-effects gstreamer1.0-vaapi
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.




> 
$ dpkg -l | grep gtk-4
ii  gir1.2-gtk-4.0:amd64                       4.6.2+ds-1ubuntu3                       amd64        GTK graphical user interface library -- gir bindings
ii  gir1.2-javascriptcoregtk-4.0:amd64         2.36.3-0ubuntu0.22.04.1                 amd64        JavaScript engine library from WebKitGTK - GObject introspection data
ii  libgtk-4-1:amd64                           4.6.2+ds-1ubuntu3                       amd64        GTK graphical user interface library
ii  libgtk-4-bin                               4.6.2+ds-1ubuntu3                       amd64        programs for the GTK graphical user interface library
ii  libgtk-4-common                            4.6.2+ds-1ubuntu3                       all          common files for the GTK graphical user interface library
ii  libjavascriptcoregtk-4.0-18:amd64          2.36.3-0ubuntu0.22.04.1                 amd64        JavaScript engine library from WebKitGTK
ii  libwebkit2gtk-4.0-37:amd64                 2.36.3-0ubuntu0.22.04.1                 amd64        Web content engine library for GTK




---

### Post by deadflowr on 2022-07-08
Maybe try changing mirrors/download servers. 
Open Software and Updates and see:
[https://help.ubuntu.com/community/Repositories/Ubuntu#Download_Server]("https://help.ubuntu.com/community/Repositories/Ubuntu#Download_Server")

It happens sometimes where a server is out of sync or something.
Changing mirrors can help.
(It helps more often than you would think)

---

### Post by debasish-raychawdhuri on 2022-07-08
Thanks! changing the repo source to the main server downloaded a host of updates and the problem got fixed. I was previously using the setting for Indian server.

---

### Post by deadflowr on 2022-07-08
Yeah, I'm always surprised, even now, every time changing mirrors fixes repository problems.

That said, if the problem has been fixed, please mark this thread a solved:
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

---

