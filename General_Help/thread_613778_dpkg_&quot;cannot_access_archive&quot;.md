---
title: "dpkg &quot;cannot access archive&quot;"
date: 2007-11-15
forum: General Help
---

### Post by papaquack on 2007-11-15
Hi all!!!  These forums have been great and have helped me solve quite a few problems.  Well... unfortunately I've come across something that I can't seem to find an answer and I'm hoping someone might be able to help me.  Here's the situation:

I have a box that has a fresh gutsy install (from cd) that is working just fine. The only thing is that it is not connected to the internet. So, in order to update it, or add new software, I am using this cool new site to search for the updates, provide me a list of .debs to download and move over to my internet-challenged box, and provide me with a batch file to install the updates or programs. Props to epimeteo for providing an awesome (and much needed) service to those of us who have needs like this.

[http://ubuntuforums.org/showthread.php?t=572819](http://ubuntuforums.org/showthread.php?t=572819)
[http://nonetdebs.homeip.net/](http://nonetdebs.homeip.net/)

OK... I"ve got my .debs and I've got my script. I've copied them from my WinXP computer to a USB drive and moved them onto gutsy in the following folder:

/home/<user>/LocalRepo

Both the script file and all my debs are there. I open my termial... cd to /home/<user>/LocalRepo... and run ls to make sure my files are there. They are... everything's cool. At this point, I should make note that the script file is just running dpkg commands, one after another... as follows:

```

#!/bin/bash
# This script is to upgrade packages
# Created on [http://nonetdebs.homeip.net](http://nonetdebs.homeip.net)
# Date: Wednesday 14th of November 2007 08:50:25 PM
dpkg -i ./libpoppler2_0.6-0ubuntu2.1_i386.deb 
dpkg -i ./poppler-utils_0.6-0ubuntu2.1_i386.deb 
dpkg -i ./libpoppler-glib2_0.6-0ubuntu2.1_i386.deb 
...
apt-get install -f
#EOF

```

From the terminal, in /home/<user>/LocalRepo, which is where all my files and scripts are, I run the following command:

```
sudo bash update
```

This is what I get:

```

<user>@linuxbox:~/LocalRepo$ sudo bash update
(Reading database ... 90728 files and directories currently installed.)
Preparing to replace libpoppler2 0.6-0ubuntu2.1 (using .../libpoppler2_0.6-0ubuntu2.1_i386.deb) ...
Unpacking replacement libpoppler2 ...
 (--install):rocessing 
 cannot access archive: No such file or directory
Setting up libpoppler2 (0.6-0ubuntu2.1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 
(Reading database ... 90728 files and directories currently installed.)
Preparing to replace poppler-utils 0.6-0ubuntu2.1 (using .../poppler-utils_0.6-0ubuntu2.1_i386.deb) ...
Unpacking replacement poppler-utils ...
 (--install):rocessing 
 cannot access archive: No such file or directory
Setting up poppler-utils (0.6-0ubuntu2.1) ...
Errors were encountered while processing:
 
(Reading database ... 90728 files and directories currently installed.)
Preparing to replace libpoppler-glib2 0.6-0ubuntu2.1 (using .../libpoppler-glib2_0.6-0ubuntu2.1_i386.deb) ...
Unpacking replacement libpoppler-glib2 ...
 (--install):rocessing 
 cannot access archive: No such file or directory
Setting up libpoppler-glib2 (0.6-0ubuntu2.1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 
] is not known. option '

```
 
If I run the dpkg command by itself from the terminal, it works (as follows):

```

<user>@linuxbox:~/LocalRepo$ sudo dpkg -i ./libpoppler2_0.6-0ubuntu2.1_i386.deb
(Reading database ... 90728 files and directories currently installed.)
Preparing to replace libpoppler2 0.6-0ubuntu2.1 (using .../libpoppler2_0.6-0ubuntu2.1_i386.deb) ...
Unpacking replacement libpoppler2 ...
Setting up libpoppler2 (0.6-0ubuntu2.1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

```

Why does dpkg work when I run it one at a time from the terminal, as opposed to the same exact command running inside my script? I am running the script as sudo and I have also marked the script executable as well. And I'm 100% sure that I've got all the files and the script in the right directory and that I'm running the script from a terminal in that directory. I have also played around in the script and edited the commands in the followiing ways and they still error out:

```

sudo dpkg -i ./libpoppler2_0.6-0ubuntu2.1_i386.deb 
sudo dpkg -i /home/<user>/LocalReopo/libpoppler2_0.6-0ubuntu2.1_i386.deb 

```

Also, at the end of the script is the apt-get command which produces:
```
] is not known. option '
```

Removing the apt-get from the script removes that error. Running the apt-get as sudo, by itself, from the terminal works. Go figure.

Can anyone from this great community help me out? I would sure appreciate it. Thanks so much!!!

---

### Post by JasonF on 2007-11-15
It would seem your script is in DOS format. Open it in nano and hit ctrl-o to save it.  When it asks what filename to write to hit alt-d (or other combinations if needed, they are listed on the bottom of the screen) until it no longer lists a specific format on the file name, eg not "Filename to write [DOS-Format]" then save it.

There is a difference is the way newlines are written in a text file between various platforms which is what is causing you problem.

---

### Post by papaquack on 2007-11-15
Ok... that makes sense. However, I've never used nano... so when I pull up nano, do my ctl-o and it says:

File Name to Write [DOS Format]: update

How do I change to a different format? Thanks.

---

### Post by JasonF on 2007-11-15
> **papaquack said:**
> Ok... that makes sense. However, I've never used nano... so when I pull up nano, do my ctl-o and it says:

File Name to Write [DOS Format]: update

How do I change to a different format? Thanks.

Alt + d while the File Name to Write message is visible will toggle the dos format.
When it doesn't list a specific format it will save as UNIX, which is what you want.

---

### Post by papaquack on 2007-11-15
That was it!!!  Thank you sooooooo much... it worked perfectly!!! The .debs installed and the apt-get command worked as it should. Thanks again!!!

---

