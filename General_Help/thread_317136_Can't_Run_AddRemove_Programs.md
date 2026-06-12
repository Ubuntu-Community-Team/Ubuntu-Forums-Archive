---
title: "Can't Run Add/Remove Programs"
date: 2006-12-11
forum: General Help
---

### Post by cyberslayer on 2006-12-11
I can't run add/remove programs.  When I attempt to run it an entry in the toolbar at the bottom of the screen indicates that it is starting but after a few seconds the entry in the toolbar disappears but add/remove programs does not come up.  I am running Ubuntu 6.10 on a relatively fresh install (3 days old because I needed to change the locations of my partitions) and add/remove programs has always worked before.  I tried reinstalling GNOME-apt-get but received the error:

E: gnome-app-install: subprocess post-installation script returned error exit status 1

I know I can just use synaptic but add/remove programs is more convenient sometimes.  Anyone know how to fix this?

Thanks

---

### Post by 23meg on 2006-12-11
What do you get when you type "gnome-app-install" in a terminal? Also make sure it's not already open in another workspace.

---

### Post by SuperMike on 2006-12-11
Potentially the add/remove programs is already open (and hung in memory) and it can't reopen again? A reboot might fix that.

Potentially the hostname was renamed but the computer has not yet been rebooted. I've sometimes seen where one changes the hostname of the computer after the installation has already completed, and then you find that add/remove programs (as well as most everything else) will fail to open.

Or perhaps it's something else entirely.

---

### Post by aysiu on 2006-12-11
[These are the most promising links](http://www.google.com/search?hl=en&q=E%3A+gnome-app-install%3A+subprocess+post-installation+script+returned+error+exit+status+1&btnG=Google+Search), and they're not very promising, but I think you should check them out anyway.

---

### Post by cyberslayer on 2006-12-12
Thanks for the replies.  I tried to install a different app and found that I get the following error whenever I attempt to install, reinstall or uninstall anything from synaptic:

E: gnome-app-install: subprocess post-installation script returned error exit status 1

This is the same error I got in my original post so it seems like synaptic is trying to re-attempt the failed gnome-apt-get reinstall every time I tell it to install/reinstall/uninstall something which is causing this error message.](*,) 

- 23meg 
When I type "gnome-app-install" I get the following output:

Traceback (most recent call last):
  File "/usr/bin/gnome-app-install", line 137, in <module>
    from AppInstall.AppInstall import AppInstall
ImportError: No module named AppInstall.AppInstall

Where is this python module located on the filesystem (maybe it isn't in the path?) and where can I get it if it is missing?

- SuperMike 
I have already tried rebooting.  It didn't help.  Also, I did not change the hostname.

- aysiu
I tried the suggestions in the first few links but it still doesn't work.

Thanks for your help

---

### Post by 23meg on 2006-12-12
Did you try```
sudo apt-get -f install
```?
> Where is this python module located on the filesystem (maybe it isn't in the path?) and where can I get it if it is missing?
It's in /usr/lib/python2.4/site-packages/AppInstall on my system.

---

### Post by cyberslayer on 2006-12-12
>  Did you try
Code:

sudo apt-get -f install

?

Yes, I tried that and got the following error:

E: Sub-process /usr/bin/dpkg returned an error code (1)

Thanks

---

### Post by cyberslayer on 2006-12-12
Ok.  I have it working now.  It turns out the problem was that I had /usr/bin/python symbolically linked to /usr/bin/python2.5 instead of python2.4 (the default).  Changing this back to python2.4 fixed all the problems I was having.  The reason the AppInstall package wasn't found was because python2.4 has this package in /usr/lib/python2.4/site-packages/AppInstall but there is no corresponding package in /usr/lib/python2.5/site-packages so when Add/Remove programs starts up it runs /usr/bin/python2.5 which cannot find the AppInstall package because it does not exist for python2.5.  I probably could have fixed this by copying /usr/lib/python2.4/site-packages/AppInstall to /usr/lib/python2.5/site-packages/AppInstall but I just added an alias as was suggested in this [thread]("http://http://ubuntuforums.org/showthread.php?p=1877124#post1877124") and everything works now.

Thanks for your help.

---

### Post by 23meg on 2006-12-12
Good to know, and nice of you to go into details of how you fixed it; doing so helps others who may have the same problem in the future.

---

### Post by trevor98 on 2007-02-20
I am having the same sort of problem opening the "Add/Remove" application.  Starting it brings up the standard applicaiton but it closes without warning (even after reboot).

I tried "gnome-app-install" and got:

Introspect error: The name org.freedesktop.AppInstall was not provided by any .service files
no listening object (The name org.freedesktop.AppInstall was not provided by any .service files) 

** (gnome-app-install:6569): WARNING **: return value of custom widget handler was not a GtkWidget
/usr/lib/python2.4/site-packages/AppInstall/AppInstall.py:1270: GtkWarning: gtk_tree_model_sort_sort: assertion `tree_model_sort->default_sort_func != NULL' failed
  item.applications.set_default_sort_func(None)
Traceback (most recent call last):
  File "/usr/bin/gnome-app-install", line 141, in ?
    sys.argv, mime_search=msi)
  File "/usr/lib/python2.4/site-packages/AppInstall/AppInstall.py", line 265, in __init__
    time_source = os.stat("/etc/apt/sources.list")[stat.ST_MTIME]
OSError: [Errno 2] No such file or directory: '/etc/apt/sources.list'

I seem to be missing '/etc/apt/sources.list'

How can I fix this?
thanks much
-trevor

---

### Post by trevor98 on 2007-02-23
I fixed my problem after digging a bit. First I looked up which file was missing: '/etc/apt/sources.list'  I opened a file browser and went to '/etc/apt/' to see what was up.  The folder existed and a backup of the file existed but 'sources.list' was missing.  I attempted to copy, paste, and rename 'sources.list_backup' to the correct name but the folder was locked out of the permissions.  I attempted to change the permissions using nautilus to no avail so I ran 'sudo nautilus' from a terminal.  I had full access to the folder and restored the backup.  It worked and now my problem has been fixed.  Hopefully someone finds this in the future in a search if they need it.

---

