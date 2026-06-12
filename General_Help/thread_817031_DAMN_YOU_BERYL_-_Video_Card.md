---
title: "DAMN YOU BERYL - Video Card"
date: 2008-06-03
forum: General Help
---

### Post by clarkyscored on 2008-06-03
Hi there,

My Ubuntu was working completely fine until when trying to install Beryl and not having a clue what I was doing, I updated the video card drivers. Now they don't work and it's stuck in the lowest resolution.

When I try update I get this message...


E: nvidia-glx: subprocess post-removal script returned error exit status 2

I can't copy the error text it comes up with so I'll try summarise it.

dpkg-divert: error checking `/usr/lib32/libgl.so.1': no such directory
dpkg: error processing nvidia-glx (--remove) :

subprocess post-removal script returned error exit status 2
errors were encountered while processing:
nvidia-glx 
E: Sub-Process /usr/bin/dpkg returned error code (1)
A package failed to install. Trying to recover


My video card is a Nvidia8600 I think I tried to make it install the wrong driver...a 7series one I think...

Any help?

---

### Post by danwood76 on 2008-06-03
Why were you trying to install beryl?
Compiz fuzion is installed with hardy by default and is an combination of beryl and compiz.

What version of ubuntu are you using?

---

### Post by edm1 on 2008-06-03
Beryl hasn't been used in a LONG time. Last release was a year and 3 months ago. Compiz-fusion is what you're after, and luckily it's installed by default. Just need to get your video card working.

---

### Post by clarkyscored on 2008-06-03
I thought I had to. I'm a complete n00b to this...


I'm using the latest Ubuntu. 64 one....err anything else?

---

### Post by clarkyscored on 2008-06-03
> **edm1 said:**
> Beryl hasn't been used in a LONG time. Last release was a year and 3 months ago. Compiz-fusion is what you're after, and luckily it's installed by default. Just need to get your video card working.

So how do I get my videocard working again?

---

### Post by danwood76 on 2008-06-03
Are you in the ubuntu GUI or a terminal?

If your in a terminal run the following command to completely remove the nvidia driver:
```

sudo apt-get purge nvidia-glx

```
reboot and in a terminal again run:
```

sudo apt-get install nvidia-glx

```
That should reinstall the repos version of the driver and fix your issue.

---

### Post by clarkyscored on 2008-06-03
I'm getting the exact same error as before.

---

### Post by clarkyscored on 2008-06-03
Got this while deleting too

michael@michael-desktop:~$ sudo apt-get purge nvidia-glx
[sudo] password for michael: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  nvidia-glx
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 22.4MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 112146 files and directories currently installed.)
Removing nvidia-glx ...
dpkg-divert: error checking `/usr/lib32/libGL.so.1': No such file or directory
dpkg: error processing nvidia-glx (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 nvidia-glx
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by danwood76 on 2008-06-03
as a quick hack around you can create that file its looking for by doing this:

```

sudo touch /usr/lib32/libGL.so.1

```
This should enable the uninstall to finish.

---

### Post by clarkyscored on 2008-06-03
michael@michael-desktop:~$ sudo touch /usr/lib32/libGL.so.1
touch: cannot touch `/usr/lib32/libGL.so.1': No such file or directory

Does the same after I try to do the original purge...


What exactly have I done. I originally installed the wrong driver I think...I think I installed the 7series one when I was meant to do the 8series or something. Am I supposed to have a completely different driver?

---

### Post by edm1 on 2008-06-03
We'll need to know the exact make and model of your video card first. If you're not sure can you post the output of 'lspci'.

---

### Post by danwood76 on 2008-06-03
> **clarkyscored said:**
> michael@michael-desktop:~$ sudo touch /usr/lib32/libGL.so.1
touch: cannot touch `/usr/lib32/libGL.so.1': No such file or directory


Do this, it means the directory doesnt exist:
```

sudo mkdir /usr/lib32
sudo touch /usr/lib32/libGL.so.1

```
That should do it with no errors, then try the purge again.

---

### Post by danwood76 on 2008-06-03
Btw I think you have half installed the driver and its missing some dependancies.
The driver in the ubuntu repos should work fine with your card, its just a case of uninstalling the drivers youve installed so the repo version can be installed in its place.

---

