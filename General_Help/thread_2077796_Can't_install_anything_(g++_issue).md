---
title: "Can't install anything (g++ issue)"
date: 2012-10-29
forum: General Help
---

### Post by girffe on 2012-10-29
Earlier I was having an issue where I was told to recompile with -fPIC. Regardless of what I did, (i.e. edit a file to use the flag, change C[XX]FLAGS), it still gave that message. So I decided to edit gcc and g++ directly in /usr/bin, to make them use -fPIC every time. Normally, g++ is just a symlink to g++-version. So I replaced the symlink with a bash script that simply called '/usr/bin/g++-version -fPIC $@'. I later found out it was compiling with gcc, but somehow g++-version ended up being changed to my bash script. Even /usr/bin/X11/g++-version was changed, and I'm certain I hadn't done anything with that file.

So I didn't have the original g++ binary anymore, and decided to cut my losses and reinstall g++ entirely. I used apt-get to remove it, and when I tried to reinstall it, it gave me this:

```


Reading package lists... Done
Building dependency tree       
Reading state information... Done
g++ is already the newest version.
The following packages were automatically installed and are no longer required:
  libdb5.1-java-gcj libdb-je-java libjpeg-turbo8-dev eclipse-platform-data libswt-gtk-3-jni nspluginwrapper libgnomecanvas2-0 libicu4j-java eclipse-rcp libswt-cairo-gtk-3-jni libgnomeui-0 gimp-gmic libdb-java
  libfftw3-3 liblapack3gf libcommons-compress-java libswt-gtk-3-java libdb5.1-java libicu4j-4.4-java libswt-gnome-gtk-3-jni jarwrapper nspluginviewer:i386 libgtkglext1 libjpeg-dev python-scour acroread-common
  libglade2-0 sat4j libcommons-el-java libfreetype6-dev libblas3gf libjpeg8-dev libgnomeui-common fastjar libjasper-java libbonoboui2-0 libgfortran3 html2text lib32z1 liblucene2-java libequinox-osgi-java
  lib32stdc++6 libbonoboui2-common libswt-webkit-gtk-3-jni libswt-glx-gtk-3-jni libgnomecanvas2-common libpng12-dev
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up g++ (4:4.6.3-1ubuntu5) ...
update-alternatives: error: alternative path /usr/bin/g++ doesn't exist.
dpkg: error processing g++ (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 g++
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I tried 'dpkg --purge g++', and although it said it worked, I continued to have the same error. 'dpkg --configure -a' also didn't help. I also can't install other software (such as emacs23 and mpich2). GCC still works fine, is there some option I can use with gcc to make it behave like g++? Or is there some way I can completely remove whatever g++ files I have right now, in order to just freshly install?

EDIT: I also tried reinstalling gcc, but this didn't change anything

---

### Post by girffe on 2012-10-30
Figured it out. Though it's unlikely someone's going to have exactly the same issue that I had and read this, I'll post the solution anyway.

The problem was that when I used apt-get remove, it didn't remove /usr/bin/g++-4.6 (no doubt due to my messing around with the files). Then, when I reinstalled, it saw the file was already there, and used it as a source for the installation (and since it was actually a 2-line bash script, that definitely caused errors). I just removed /usr/bin/g++-4.6, used apt-get install, and it worked again.

---

### Post by jerrrys on 2012-10-30
Just for future reference, the purge command can be useful.  But /usr/bin can still be a problem.  So I usually do a nautilus search (gksudo nautilus) and remove any left over packages.

[https://help.ubuntu.com/community/AptGet/Howto#Removal_commands](https://help.ubuntu.com/community/AptGet/Howto#Removal_commands)

And don't forget  :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

