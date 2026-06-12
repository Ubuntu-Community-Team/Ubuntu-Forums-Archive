---
title: "How do I fix this?"
date: 2013-11-09
forum: General Help
---

### Post by Draygon01 on 2013-11-09
I see this when I try to install multiple things

The following packages have unmet dependencies:
  libasound2: Breaks: libasound2-plugins (< 1.0.24) but 1.0.22-0ubuntu6 is to be installed
  libglib2.0-0: Breaks: gnome-control-center (< 1:3) but 1:2.30.1-0ubuntu2 is to be installed
                Breaks: gvfs (< 1.8) but 1.6.1-0ubuntu1build1 is to be installed
  libpango1.0-0: Breaks: plymouth (< 0.8.2-2ubuntu19) but 0.8.2-2ubuntu2.2 is to be installed
  ppp: Breaks: network-manager (<= 0.8.0.999-1) but 0.8-0ubuntu3.3 is to be installed
       Breaks: network-manager-pptp (<= 0.8.0.999-1) but 0.8-0ubuntu3 is to be installed
E: Broken packages



What is this and what does it mean?

---

### Post by ian-weisser on 2013-11-09
It means that you seem to be trying to install a non-Ubuntu package. Perhaps a PPA, or some .deb you downloaded from the web, or some third party repository, or some old/obsolete package from someplace you perhaps shouldn't use.

That non-Ubuntu package is not easily compatible with your current system.

What, exactly, were you trying to install? And from where?

---

### Post by Draygon01 on 2013-11-09
i got that from typing "sudo apt-get install python-minimal"

---

### Post by ian-weisser on 2013-11-09
Was python-minimal the most recent? Or the original? It seems unlikely that python-minimal (which is included in the default install of Ubuntu) would be interacting with Plymouth and some of those other packages.

Anyway,

First go into Software Center --> Software Sources --> Other Software tab and deactivate (uncheck) all the PPAs.

Second, try the following command. Show us the *entire* terminal session, everything from the original command all the way through all of the error messages. If we're lucky, it will show us the problem package(s).
```
sudo dpkg --configure -a
```

---

### Post by Draygon01 on 2013-11-10
It showed this.

patachu@X41:~$ sudo dpkg --configure -a
dpkg: parse error, in file '/var/lib/dpkg/available' near line 29258 package 'libxcb-keysyms1':
 `Replaces' field, invalid package name `li`xcb-keysyms0': character ``' not allowed (only letters, digits and characters `-+._')
patachu@X41:~$

---

### Post by Bucky Ball on 2013-11-10
Just a tip for future reference: you'll improve your chances of getting help by using descriptive title for your threads. Generic ones like 'how do I fix this' tell us nothing and generally don't get you far. 

You might like to have a look at the link in my signature for further tips on improving your chances of getting support in future. Good luck.

---

### Post by Draygon01 on 2013-11-10
patachu@X41:~$ sudo dpkg --configure -a dpkg: parse error, in file '/var/lib/dpkg/available' near line 29258 package 'libxcb-keysyms1': `Replaces' field, invalid package name `li`xcb-keysyms0': character ``' not allowed (only letters, digits and characters `-+._')  I looked for this on google put I could not find anything on it.

---

### Post by ian-weisser on 2013-11-10
Please use ```
 tags to make your output readable.
[CODE]Like this
```

Open a terminal.
Here's how to rebuild the /var/lib/dpkg/available file when it gets corrupted ( [http://askubuntu.com/questions/55099/dpkg-error-parsing-file-var-lib-dpkg-available-near-line-0](http://askubuntu.com/questions/55099/dpkg-error-parsing-file-var-lib-dpkg-available-near-line-0) ):
```
sudo dpkg --clear-avail
sudo apt-get update
```

---

### Post by Draygon01 on 2013-11-10
```
patachu@X41:~$ sudo apt-get update -f
Get:1 http://us.archive.ubuntu.com precise Release.gpg [198B]
Ign http://us.archive.ubuntu.com/ubuntu/ precise/main Translation-en_US        
Ign http://us.archive.ubuntu.com/ubuntu/ precise/restricted Translation-en_US  
Ign http://us.archive.ubuntu.com/ubuntu/ precise/universe Translation-en_US    
Ign http://us.archive.ubuntu.com/ubuntu/ precise/multiverse Translation-en_US  
Get:2 http://us.archive.ubuntu.com precise-updates Release.gpg [198B]          
Ign http://us.archive.ubuntu.com/ubuntu/ precise-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ precise-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ precise-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ precise-updates/multiverse Translation-en_US
97% [Connecting to archive.canonical.com (91.189.92.191)] [Connecting to securi/usr/lib/apt/methods/gpgv: error while loading shared libraries: unexpected PLT reloc type 0x05
Hit http://us.archive.ubuntu.com precise Release                               
E: Method gpgv has died unexpectedly!                                          
E: Sub-process gpgv returned an error code (127)
E: Method /usr/lib/apt/methods/gpgv did not start correctly


```

I ended up getting this in response.

---

### Post by Draygon01 on 2013-11-10
> **ian-weisser said:**
> Was python-minimal the most recent? Or the original? It seems unlikely that python-minimal (which is included in the default install of Ubuntu) would be interacting with Plymouth and some of those other packages.

Anyway,

First go into Software Center --> Software Sources --> Other Software tab and deactivate (uncheck) all the PPAs.

Second, try the following command. Show us the *entire* terminal session, everything from the original command all the way through all of the error messages. If we're lucky, it will show us the problem package(s).
```
sudo dpkg --configure -a
```

So I did some research and fixed a few things.  This is now what I get when I run what you asked in Terminal.

```
dpkg: parse error, in file '/var/lib/dpkg/status' near line 33277 package 'gconf-defaults-service':
 duplicate value for user-defined field `Original-Maintainer'


```

---

### Post by ian-weisser on 2013-11-10
To repair a corrupted /var/lib/dpkg/status file, restore from the system's backup status file.
See [http://askubuntu.com/questions/343616/dpkg-exit-with-error-parsing-file-var-lib-dpkg-status-what-to-do](http://askubuntu.com/questions/343616/dpkg-exit-with-error-parsing-file-var-lib-dpkg-status-what-to-do)
```
sudo rm /var/lib/dpkg/status
sudo cp /var/backups/dpkg.status.0 /var/lib/dpkg/status
sudo apt-get update
```

---

