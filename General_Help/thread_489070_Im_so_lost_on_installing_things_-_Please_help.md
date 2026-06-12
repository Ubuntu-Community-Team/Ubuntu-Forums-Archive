---
title: "Im so lost on installing things - Please help"
date: 2007-06-30
forum: General Help
---

### Post by margaf77 on 2007-06-30
Im a noob and am lost about what to do with tarballs. I downloaded teatime_applet_2-2.8.0.tar.gz and when I follow these instructions for install I get an error on the 1st step.
[COLOR="Red"]
tar xzf teatime_applet_2-version[/COLOR]    -  unpack the files
[COLOR="Red"]cd teatime_applet_2-version[/COLOR]      -     change to the new teatime directory
[COLOR="Red"]./configure[/COLOR]              -             prepare the package to compile (for configuration parameters do an ./configure --help)
[COLOR="Red"]make[/COLOR]                    -              compile
[COLOR="Red"]make install[/COLOR]           -               install the executable & suportfiles (usualy you only can do this as root / superuser)


The error I get is:

tar: teatime_applet_2-2.8.0.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors


This should be simple yet I cant seem to do it. :(



On another related tangent, when I download a tarball what should I do with it first. I download to my desktop and then dont know where to put it before I extract/install. Do I extract right from where it is and it will create the folders where they are supposed to go or do I need to put it in a certain folder.

---

### Post by margaf77 on 2007-07-01
OK I got past the extraction of the tarball, I was not typing the right path in but now I get an error:

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

---

### Post by Old *ix Geek on 2007-07-01
> tar: teatime_applet_2-2.8.0.tar.gz: Cannot open: No such file or directory
If you're failing at this step, it sounds like you're not in the directory where the zipped file is. So, to answer your other question, too: It generally doesn't matter where you place a downloaded file--as long as you know where it is AND you're in that directory when attempting to unzip and extract its files (OR you use the pathname of that directory in your unpacking command).

I have a subdirectory called **downloads** in my home directory, and I place everything I download into this directory.  Then, when I unpack tarballs, their directory structure is created right there as subdirectories of **downloads**.  If you use this same method you'll always know where your downloaded files are, and then it's just a simple matter of making sure you're IN that directory when you're unpacking them, and then moving into the newly-created subdirectory they create.

So in your example:  Place the downloaded file into a directory; navigate to that directory; issue the command to unpack it; navigate into the new directory it created; then issue **./configure** to run its setup routine.

By the way, when you're unpacking something with **tar**, it's useful to add the **v** (for verbose) argument to your other options; this will cause a list of file names to be displayed as the unpacking is taking place, so you can see as it's happening what it's doing.  In your example: **tar xvfz teatime_applet_2-2.8.0.tar.gz**.

---

### Post by margaf77 on 2007-07-01
> **Old *ix Geek said:**
> If you're failing at this step, it sounds like you're not in the directory where the zipped file is. So, to answer your other question, too: It generally doesn't matter where you place a downloaded file--as long as you know where it is AND you're in that directory when attempting to unzip and extract its files (OR you use the pathname of that directory in your unpacking command).

I have a subdirectory called **downloads** in my home directory, and I place everything I download into this directory.  Then, when I unpack tarballs, their directory structure is created right there as subdirectories of **downloads**.  If you use this same method you'll always know where your downloaded files are, and then it's just a simple matter of making sure you're IN that directory when you're unpacking them, and then moving into the newly-created subdirectory they create.

So in your example:  Place the downloaded file into a directory; navigate to that directory; issue the command to unpack it; navigate into the new directory it created; then issue **./configure** to run its setup routine.

By the way, when you're unpacking something with **tar**, it's useful to add the **v** (for verbose) argument to your other options; this will cause a list of file names to be displayed as the unpacking is taking place, so you can see as it's happening what it's doing.  In your example: **tar xvfz teatime_applet_2-2.8.0.tar.gz**.

Thanks so much for the answer I figured that out but Im still so lost. This is becoming more and more humbling as I go.   I now got to the[COLOR="Red"] ./configure[/COLOR] step and I cant get past it....grrrr Heres what it says now. I think I have to somehow get these packages(?) on my system but have no idea how to.

[COLOR="Red"]No package 'glib-2.0' found
No package 'gdk-pixbuf-2.0' found
No package 'gtk+-2.0' found
No package 'gstreamer-0.10' found
No package 'gnome-vfs-2.0' found
No package 'libpanelapplet-2.0' found
No package 'libxml-2.0' found
No package 'gconf-2.0' found[/COLOR]


Also when Im donw with this install if that ever happens, can I just delete the tarball on my desktop?

---

### Post by margaf77 on 2007-07-01
OK, using this  [COLOR="Red"]sudo apt-get install libgtk2.0-dev libglib2.0-dev[/COLOR] I have gotten it to now say I am missing less packages than before.

[COLOR="Red"]
No package 'gstreamer-0.10' found
No package 'gnome-vfs-2.0' found
No package 'libpanelapplet-2.0' found
No package 'libxml-2.0' found
No package 'gconf-2.0' found
[/COLOR]

This is so much more trouble than its worth, Im seriously thinking of sticking with XP. :mad:

---

### Post by Dean92 on 2007-07-01
What the errors are telling you is that the program needs the packages in the error in order to funcion properly.

To fix this, all you have to do is 

1): Run Synaptic:
(System->Administration->Synaptic Package Manager).
2):In Synaptic search for the missing packages, and install them.

P.S. 
Don't switch back yet, once you get used to Ubuntu, it's a pleasure to work with.
Even when things don't work 100%, since it becomes fun messing with programs.

Dean.

---

### Post by d_xtremw on 2007-07-01
Dean's right. Been a windows user my entire life. started using ubuntu about a week and a half ago and im addicted. I was having all those exact same problems that you're having and these forums really helped me out. (tryna become a master at ubuntu lool) anyways to the point of this reply:

run "sudo apt-get update"
and "sudo apt-get install" to make sure all your missing files are up to date. using the synaptic package master like he said, just find the missing files, mark for installation and apply.  Im not sure how or what i did initially but all ( actually most) of the mising files i needed were automatically installed for me wen i did some command.  hope this helps

---

