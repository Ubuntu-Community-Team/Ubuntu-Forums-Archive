---
title: "Gwenview in 16.04"
date: 2016-06-19
forum: General Help
---

### Post by hornetster on 2016-06-19
Have recently installed 16.04 x64, and installed Gwenview to view photos etc.
If I try to open a file in Gwenview, it will show no files in the file system. No errors, etc, just cannot browse anything.
Assuming I am missing some KDE library or similar.
Anyone point me in the right direction?
Thanks.

---

### Post by vasa1 on 2016-06-19
Please post the output of
```
sudo apt-get update
```and```
sudo apt-get upgrade
```and```
sudo apt-get dist-upgrade
``` If you're concerned about what the last command does, you can always press "N" instead of "Y" to stop the dist-upgrade.

Then, you can also post the terminal messages you get when you launch gwenview from a terminal.

In all cases, please use [code] tags to format the terminal output properly.

---

### Post by hornetster on 2016-06-19
Always try & keep the updates, 'updated'!

```
john@Boss-Ubunt:~$ sudo apt-get update
Hit:1 http://au.archive.ubuntu.com/ubuntu xenial InRelease
Hit:2 http://au.archive.ubuntu.com/ubuntu xenial-updates InRelease             
Hit:3 http://au.archive.ubuntu.com/ubuntu xenial-backports InRelease           
Hit:4 http://security.ubuntu.com/ubuntu xenial-security InRelease              
Hit:5 http://archive.canonical.com/ubuntu xenial InRelease                     
Reading package lists... Done                           
john@Boss-Ubunt:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
john@Boss-Ubunt:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
john@Boss-Ubunt:~$ gwenview
kipi.library: UI file : "/usr/share/kxmlgui5/kipi/kipiplugin_kxmlhelloworldui.rc"
kipi.library: Loaded plugin  "KXMLHelloWorld"
klauncher not running... launching kdeinit
klauncher not running... launching kdeinit
klauncher not running... launching kdeinit
couldn't create slave: "Cannot talk to klauncher: The name org.kde.klauncher5 was not provided by any .service files"
No file found for ".xml" , even though update-mime-info said it would exist.
Either it was just removed, or the directory doesn't have executable permission...
("/home/john/.local/share/mime", "/usr/share/mime")
No file found for ".xml" , even though update-mime-info said it would exist.
Either it was just removed, or the directory doesn't have executable permission...
("/home/john/.local/share/mime", "/usr/share/mime")
mCurrentMainPageId == 'StartMainPageId'
```

So, klauncher....
Looked for something to install, but can't work it out...?
Thanks.

---

### Post by vasa1 on 2016-06-19
I searched the net for "Cannot talk to klauncher: The name org.kde.klauncher5 was not provided by any .service files" and came up with some links not especially related to gwenview but ...:

The accepted answer to [http://askubuntu.com/questions/617955/problem-with-kde-programs-after-upgrading-to-15-04/617956](http://askubuntu.com/questions/617955/problem-with-kde-programs-after-upgrading-to-15-04/617956) suggests **apt-get install kinit kio kio-extras kded5**. Please read that fully.

Another link:
[http://www.forums.fedoraforum.org/showthread.php?p=1762531](http://www.forums.fedoraforum.org/showthread.php?p=1762531)

And this: [http://ubuntuforums.org/showthread.php?t=2277019](http://ubuntuforums.org/showthread.php?t=2277019)

BTW, as the last link indicates, it may not be the best idea to use a KDE app in a non-KDE environment unless you really, really, need to!

---

### Post by hornetster on 2016-06-20
Thanks. did that and that solved 'most' of the probs, but now get "URL cannot be listed remote:/" popping up a number of times (5?), when starting Gwenview.
Apparently this is a reported Bug: [https://bugs.kde.org/show_bug.cgi?id=343997](https://bugs.kde.org/show_bug.cgi?id=343997), and as 1 of the users there says, it happens without even trying to browse (just on opening.)
A suggestion there is "Ok, just fixed the issue by installing the packages kinit and kio", but these have already been installed previously.
And, I realise this is a KDE app in a non-KDE environment, but have previously used this in older versions of Ubuntu, without a prob..... Also, am always open to suggestions for a "comprehensive, good, simple photo viewer", but Gwenview seems to be one of the better ones out there...?
Thanks.

---

### Post by vasa1 on 2016-06-20
> **hornetster said:**
> ... Also, am always open to suggestions for a "comprehensive, good, simple photo viewer", but Gwenview seems to be one of the better ones out there...?
Thanks.Did you look at **gThumb**? It's in the repos if you have Universe enabled.

---

