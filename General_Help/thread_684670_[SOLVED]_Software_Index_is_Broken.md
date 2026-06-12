---
title: "[SOLVED] Software Index is Broken"
date: 2008-02-01
forum: General Help
---

### Post by bg1256 on 2008-02-01
Hey all, 

Running Gutsy + Gnome.

Not the first time this has happened to me, but this time around, 

```
sudo aptitude install -f
```

does not solve the problem.

Here is the output from the terminal:

```
benjamin@BG-desktop:~$ sudo aptitude install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages have been automatically kept back:
  libpulse0 
The following packages will be REMOVED:
  moodle 
0 packages upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 53.0MB will be freed.
Do you want to continue? [Y/n/?] y
(Reading database ... 189850 files and directories currently installed.)
Removing moodle ...
dpkg: error processing moodle (--remove):
 subprocess post-removal script returned error exit status 10
Errors were encountered while processing:
 moodle
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
benjamin@BG-desktop:~$ 


```

I'm at a loss.  I have no idea.

I tried to install moodle a few days ago, and it said it did not install correctly. However, in Synaptic, it says the program is installed. But, now I cannot uninstall it no matter what I do.

Help?

---

### Post by zvacet on 2008-02-01
```
sudo apt-get --purge remove moodle
```

or 

```
sudo dpkg --remove --force-remove-reinstreq moodle
```

---

