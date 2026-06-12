---
title: "Thunar - archive options missing from context menu"
date: 2016-09-15
forum: General Help
---

### Post by Maximus559 on 2016-09-15
In Thunar file manager, I typically create and extract archives by right-clicking and selecting "Extract To...", "Extract Here", or "Create Archive." These context menu items recently disappeared on two separate installations of Xubuntu 16.04 64-bit. Archive Manager still works, and thunar-archive-plugin is still installed. I don't remember doing anything to cause this, so I'm guessing this happened with a recent update. Any help would be appreciated.

---

### Post by speartip on 2016-09-16
Not sure why they've disappeared. They appear on my system. Nevertheless you can recreate them again by following the instructions here:
[http://docs.xfce.org/xfce/thunar/custom-actions#opening_a_root_thunar](http://docs.xfce.org/xfce/thunar/custom-actions#opening_a_root_thunar)
Check out the "working with archives" section.
Also worth bookmarking the page for future use.

edit... On close inspection you may just need the thunar-archive-plugin installing.

---

### Post by Maximus559 on 2016-09-17
As stated above, thunar-archive-plugin was already installed. I tried reinstalling it (sudo apt-get install --reinstall), but this didn't seem to change anything.

The custom actions don't look like the right answer. They are format-specific, whereas the context menu used to work with all archives.

---

### Post by Bucky Ball on 2016-09-17
Have you got Xarchiver installed?

---

### Post by Maximus559 on 2016-09-17
No, xarchiver was not originally installed. I installed it, but the problem remains.

To clarify, here are the menu items I'm referring to:

[IMG]http://goodies.xfce.org/_media/projects/thunar-plugins/tap-extract-archive.png[/IMG] [IMG]http://goodies.xfce.org/_media/projects/thunar-plugins/tap-create-archive.png[/IMG]

---

### Post by Maximus559 on 2016-09-25
This is still an issue after several rounds of updates. Is there anything I can do to verify that thunar-archive-plugin is configured correctly?

---

### Post by vasa1 on 2016-09-25
Could you close all instances of Thunar and then temporarily rename *~/.config* to something else (like ~/.config.bak)? Now when you run Thunar do the options appear? If they do, it may point to something in your *~/.config* folder being messed up. Possibly something in *~/.config/Thunar/*?.

---

### Post by Maximus559 on 2016-09-27
I tried renaming ~/.config. My "Places" shortcuts disappeared, but the archive menu items were still missing.

---

### Post by vasa1 on 2016-09-27
Do these context items appear when you right-click on a file _in Thunar itself_? I looked at the goodies.xfce.org images you posted and both refer to right-clicking on icons on the desktop. That information won't solve your problem but might give someone a clue in case there's a difference in behavior.

You could also consider asking via the Xubuntu users mailing list: [https://lists.ubuntu.com/mailman/listinfo/xubuntu-users](https://lists.ubuntu.com/mailman/listinfo/xubuntu-users) although, judging by the thread titles, nothing similar has been reported there.

BTW, when you run *sudo apt-get update*, is the output okay or are there messages you feel are worth mentioning?

---

### Post by Maximus559 on 2016-10-18
> **vasa1 said:**
> Do these context items appear when you right-click on a file _in Thunar itself_?

No. I'm not seeing the archive menu items in Thunar or on the desktop.

> **vasa1 said:**
> BTW, when you run *sudo apt-get update*, is the output okay or are there messages you feel are worth mentioning?

Here is the output of *sudo apt-get update*:

```
Ign:1 http://dl.google.com/linux/chrome/deb stable InReleaseHit:2 http://dl.google.com/linux/chrome/deb stable Release                                                 
Hit:3 http://us.archive.ubuntu.com/ubuntu xenial InRelease                                                 
Get:4 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease [95.7 kB]                           
Get:5 http://security.ubuntu.com/ubuntu xenial-security InRelease [94.5 kB]         
Hit:7 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease                            
Get:8 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages [408 kB]
Ign:9 https://dl.bintray.com/sbt/debian  InRelease          
Get:10 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 Packages [51.9 kB]
Get:11 https://dl.bintray.com/sbt/debian  Release [814 B]           
Hit:11 https://dl.bintray.com/sbt/debian  Release                                             
Get:13 http://security.ubuntu.com/ubuntu xenial-security/universe i386 Packages [51.8 kB]                              
Get:14 http://security.ubuntu.com/ubuntu xenial-security/universe Translation-en [31.6 kB]                             
Get:15 http://us.archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages [403 kB]                                  
Get:16 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 DEP-11 Metadata [7,410 B]                      
Get:17 http://us.archive.ubuntu.com/ubuntu xenial-updates/main Translation-en [156 kB]                                 
Get:18 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 DEP-11 Metadata [335 kB]                          
Get:19 http://us.archive.ubuntu.com/ubuntu xenial-updates/main DEP-11 64x64 Icons [197 kB]                             
Get:20 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages [345 kB]                             
Get:21 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe i386 Packages [341 kB]                              
Get:22 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe Translation-en [123 kB]                             
Get:23 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 DEP-11 Metadata [106 kB]                      
Get:24 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe DEP-11 64x64 Icons [117 kB]                         
Fetched 2,863 kB in 41s (69.7 kB/s)                                                                                    
Reading package lists... Done
```

I tried doing a *sudo apt-get purge thunar* followed by *sudo apt-get install thunar* - still no luck. Is there anything else I can do short of reformatting and reinstalling that might solve this problem?

---

### Post by edward-chetwynd-talbot on 2016-10-30
+1 - I too ran into a missing context menu entry for the Xfce Archive plugin on Xubuntu 16.04 LTS (amd64).
All my personal context menu items I added myself all still work perfectly.
Surprisingly, on a 32bit installation Xubuntu 16.04 LTS installation I have here, this plugin is still in the context menu, and working as it should.
Both systems are up-to-date.
Trying to resolve the issue,
=== I've restored my ~/.config/Thunar to a rsync'ed backup of a week ago (when all was still fine). This did not improve the situation.
=== I've sudo apt install --reinstall thunar-archive-plugin; this too did not resolve the issue.
=== on both the working 32 bit and 64 bit install the same version of thunar-archive-plugin is installed

```

ect@tiki:~$ dpkg -l | grep thunar*
ii  libthunarx-2-0                                              1.6.10-2ubuntu1+patch1                        amd64        extension library for thunar
ii  thunar                                                      1.6.10-2ubuntu1+patch1                        amd64        File Manager for Xfce
ii  thunar-archive-plugin                                       0.3.1-4                                       amd64        Archive plugin for Thunar file manager
ii  thunar-data                                                 1.6.10-2ubuntu1+patch1                        all          Provides thunar documentation, icons and translations
ii  thunar-media-tags-plugin                                    0.2.1-1                                       amd64        Media tags plugin for Thunar file manager
ii  thunar-volman                                               0.8.1-2                                       amd64        Thunar extension for volumes management

```

=== The .tap files and links are present and seem to be in good order:

```

ect@tiki:/usr/lib/x86_64-linux-gnu/thunar-archive-plugin$ ll
total 112
drwxr-xr-x   2 root root  4096 Oct 30 13:16 ./
drwxr-xr-x 104 root root 94208 Oct 28 11:17 ../
-rwxr-xr-x   1 root root  1306 Jun 27  2015 ark.tap*
-rwxr-xr-x   1 root root  1389 Jun 27  2015 engrampa.tap*
-rwxr-xr-x   1 root root  1494 Jun 27  2015 file-roller.tap*
lrwxrwxrwx   1 root root    15 Jun 27  2015 gnome-file-roller.tap -> file-roller.tap*
lrwxrwxrwx   1 root root    21 Jun 27  2015 org.gnome.FileRoller.tap -> gnome-file-roller.tap*

```

== As with OP, the Archive Manager itself works fine (apart from some weird window size issues introduced with 14.04 --> 16.04).

---

### Post by edward-chetwynd-talbot on 2016-10-30
I also noticed now that another Thunar plug-in, the thunar-media-tags-plugin is not working anymore. This looks like Thunar might have an issue with/ can not find all of its plug-ins. Will dive into it.

---

### Post by edward-chetwynd-talbot on 2016-10-30
In the end, solved it myself. Apparently, it was a remnant of an attempt to solve the (still actual) "crash on rename" bug in Thunar.
Trying to solve this bug, I compiled, build, and patch Thunar as described here ([http://tqdev.com/2016-xubuntu-16-04-thunar-crashes-on-rename](http://tqdev.com/2016-xubuntu-16-04-thunar-crashes-on-rename))
This however, did not solve the "crash on rename" bug.

 As a result of this, Thunar lost all its plugins. Hence:
== Media were not auto-mounted anymore, although settings in Thunar under Preferences > Advanced > Enable Volume Management > Configure were ticked.
== thunar-archive-plugin didn't work anymore. Create archive and Expand here options were not present anymore in the right click Thunar context menu
== Also the "Set as wallpaper" option in the context menu was absent.
== The plugin to edit media tags of media files (thunar-media-tags-plugin) did no longer work. Hence, if Properties of an audio file were selected, no tab Audio was present/ available.

Removing/ reinstalling Thunar did not resolve these issues. The issues were solved eventually by first removing remnants of the Thunar "compiled and build" from git version, followed by a reinstall:
```

~# cd /usr/local
~# find . -iname "*thunar*" -exec rm -rf {} ';'
~$ sudo apt install --reinstall thunar*
~$ sudo reboot -h now

```

This will also reinstall all the Thunar plugins.

Note: it is possible that during this process the desktop is "deleted", resulting in disappeared desktop wallpapers and desktop icons.
To restore, reinstall xfdesktop4
```

~$ sudo apt install xfdesktop4

```

---

### Post by Maximus559 on 2016-11-04
D'oh... I tried the exact same fix for the Thunar rename bug! It didn't work for me either, and I didn't make the connection to the archive plugin problem. I figured a purge and reinstall would be enough to wipe out any remnants of that change.

The procedure you posted worked for me, though I had to do a sudo on the second line as well. I didn't have any problems with the desktop disappearing. The archive menu options are now restored; thanks for your help.

---

### Post by A_M_S on 2017-02-04
Same issue here and by the same reason.

The procedure above solved the problem


Thank you!!  :D

---

