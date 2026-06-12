---
title: "[SOLVED] Can't install new packages or update old ones"
date: 2014-07-18
forum: General Help
---

### Post by NeoX12 on 2014-07-18
Every time I run an update or try to install new software, I get this error at the end:
```

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 fglrx-pxpress
Setting up fglrx-pxpress (0.6~hybrid0.0.2) ...
dpkg: error processing fglrx-pxpress (--configure):
 subprocess installed post-installation script returned error exit status 1


```

But the program does install right I guess.. because I can see the GUI.
After:

```

sudo apt-get update&& apt-get upgrade

```

I am asked to restart the system ^ so.. I am guessing they do install. 

But any solution for the problem I mentioned? 

Thanks a lot for your help.

---

### Post by plucky on 2014-07-18
Try from a terminal ```
sudo apt-get install -f
``` and post the output if any errors.

Good Luck

---

### Post by NeoX12 on 2014-07-18
> **plucky said:**
> Try from a terminal ```
sudo apt-get install -f
``` and post the output if any errors.

Good Luck

I got this:

```

mashruf@SIS:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libxss1
The following NEW packages will be installed:
  libxss1
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 8,646 B of archives.
After this operation, 77.8 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://ca.archive.ubuntu.com/ubuntu/ precise/main libxss1 amd64 1:1.2.1-2 [8,646 B]
Fetched 8,646 B in 3s (2,431 B/s)  
Selecting previously unselected package libxss1.
(Reading database ... 294884 files and directories currently installed.)
Unpacking libxss1 (from .../libxss1_1%3a1.2.1-2_amd64.deb) ...
Setting up libxss1 (1:1.2.1-2) ...
Setting up google-chrome-stable (36.0.1985.125-1) ...
update-alternatives: using /usr/bin/google-chrome-stable to provide /usr/bin/x-www-browser (x-www-browser) in auto mode.
update-alternatives: using /usr/bin/google-chrome-stable to provide /usr/bin/gnome-www-browser (gnome-www-browser) in auto mode.
update-alternatives: using /usr/bin/google-chrome-stable to provide /usr/bin/google-chrome (google-chrome) in auto mode.
Setting up fglrx-pxpress (0.6~hybrid0.0.2) ...
dpkg: error processing fglrx-pxpress (--configure):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 fglrx-pxpress
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Could someone please explain to me wth is going on lol

---

### Post by kc1di on 2014-07-18
the installer installed everything but had problems installing fglrx-pxpress.  I believe that is a driver for ATI/AMD cards. 

you might try this and see if it clears the error. in a terminal : ```
sudo dpkg --configure -a 
```

---

### Post by NeoX12 on 2014-07-18
> **kc1di said:**
> the installer installed everything but had problems installing fglrx-pxpress.  I believe that is a driver for ATI/AMD cards. 

you might try this and see if it clears the error. in a terminal : ```
sudo dpkg --configure -a 
```

I get this:

```

mashruf@SIS:~$ sudo dpkg --configure -a
Setting up fglrx-pxpress (0.6~hybrid0.0.2) ...
dpkg: error processing fglrx-pxpress (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 fglrx-pxpress

```

---

### Post by plucky on 2014-07-18
Try ```
sudo dpkg -r fglrx-pxpress
``` to remove the package.

---

### Post by NeoX12 on 2014-07-18
> **plucky said:**
> Try ```
sudo dpkg -r fglrx-pxpress
``` to remove the package.

Done! Removed and ran

```

sudo dpkg --configure -a

```

What now? :D 
Should I try and run a 

sudo apt-get update&&apt-get upgrade 

^ ?

---

### Post by NeoX12 on 2014-07-18
Managed to install google chrome <3

```

mashruf@SIS:~/Downloads/Programs$ sudo dpkg -i google-chrome-stable_current_amd64.deb 
[sudo] password for mashruf: 
(Reading database ... 294885 files and directories currently installed.)
Preparing to replace google-chrome-stable 36.0.1985.125-1 (using google-chrome-stable_current_amd64.deb) ...
Unpacking replacement google-chrome-stable ...
Setting up google-chrome-stable (36.0.1985.125-1) ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for man-db ...
mashruf@SIS:~/Downloads/Programs$ 


```

holy **** this is fun.

Any check ups I can post here? Just so I know nothing else is wrong with my system?

---

### Post by kc1di on 2014-07-18
you should be fine now.  you might want to run ```
sudo apt-get clean
sudo apt-get autoclean
``` just to clean out any leftover apt cash files. 

Cheers , enjoy ;)

---

### Post by kc1di on 2014-07-18
also Just a suggestion you may want to install synaptic package manager , it just make things easier in MHO.
you can do that with this commmand ```
sudo apt-get install synaptic
```

---

### Post by Navneet_Kumar on 2014-07-18
Yup,installing the synaptic package manager reduces the burden and along with it also install ubuntu tweak tool,so as to do the auto-cleaning itself...........hope it will help   :D

---

### Post by grahammechanical on 2014-07-18
Have you considered this advice?

[https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)

The advice is different for different versions of Ubuntu. If I read that advice correctly then, fglrx-pxpress is not needed for 14.04 which you are using.

Regards.

---

### Post by NeoX12 on 2014-07-18
> **kc1di said:**
> also Just a suggestion you may want to install synaptic package manager , it just make things easier in MHO.
you can do that with this commmand ```
sudo apt-get install synaptic
```

Executed all the three commands man. Thanks a bunch :)

---

### Post by NeoX12 on 2014-07-18
> **grahammechanical said:**
> Have you considered this advice?

[https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)

The advice is different for different versions of Ubuntu. If I read that advice correctly then, fglrx-pxpress is not needed for 14.04 which you are using.

Regards.

I am using 12.04 but yes, I am going to take a good look at the link. Thank you.

---

### Post by kc1di on 2014-07-18
Your Welcome , Enjoy ;)

---

