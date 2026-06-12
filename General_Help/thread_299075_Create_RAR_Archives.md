---
title: "Create RAR Archives"
date: 2006-11-13
forum: General Help
---

### Post by FusionXN1 on 2006-11-13
Is there any software for linux that can create and extract rar files in a graphical interface like WINRAR for Windows?

WINRAR for linux only has command line :(

Thanks! :-D

---

### Post by Ramses de Norre on 2006-11-13
```
sudo aptitude install rar unrar
```
You can then just use file-roller to create or extract .rar archives.

---

### Post by FusionXN1 on 2006-11-13
Thanks for the fast reply! Is this 100% free?

---

### Post by jamyskis on 2006-11-13
*snip*

I stand corrected...

---

### Post by Ramses de Norre on 2006-11-13
No, both rar and unrar are in multiverse.. There is a free package unrar-free however which is in universe but it probably has limited capabilities.

---

### Post by FusionXN1 on 2006-11-13
So how much dos this cost?

---

### Post by Ramses de Norre on 2006-11-13
Ow you mean free like in bear:D Then they are absolutely free! You might need to edit your sources file (sudo gedit /etc/apt/sources.list) and enable the lines containing "universe" or "multiverse" by removing the "#" in front of them, then do ```
sudo aptitude update && sudo aptitude install rar unrar
```

I meant they are not free like in speech, they are closed source, proprietary and released under a non-free license.

---

### Post by FusionXN1 on 2006-11-13
WOW, I love the linux community, thanks for the fast responce!

Cant i just go into .. (i forgot what its called as im on windows and thinking of going back to ubuntu)a "place" and enable them, i remember somewhere that was a setting for community releases and not-free stuff...

---

### Post by Ramses de Norre on 2006-11-13
Synaptic you mean? I think you can enable them there too, yes ;)

---

### Post by FusionXN1 on 2006-11-13
Yep, thanks a lot for your help. If you have time please check out my other threads:

[http://ubuntuforums.org/showthread.php?t=299062](http://ubuntuforums.org/showthread.php?t=299062)
[http://ubuntuforums.org/showthread.php?t=299089](http://ubuntuforums.org/showthread.php?t=299089)

---

### Post by b3tzi on 2006-11-18
> **Ramses de Norre said:**
> ```
sudo aptitude install rar unrar
```
You can then just use file-roller to create or extract .rar archives.

> 
b3tzi@b3tzi:~$ sudo aptitude install rar unrar
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initialising package states... Done
Building tag database... Done
No candidate version found for rar
No candidate version found for unrar
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done


What's wrong with it?

---

### Post by Ramses de Norre on 2006-11-18
They are in multiverse, have you enabled that?
You can do so in synaptic (settings>repositories), or in /etc/apt/sources.list.

---

### Post by b3tzi on 2006-11-18
I didn't enabled it. 

Here is my repositories list:

> 
## Gaim 2.0 beta 3
deb-src [http://ma.archive.ubuntu.com/ubuntu/](http://ma.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ma.archive.ubuntu.com/ubuntu/](http://ma.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://ma.archive.ubuntu.com/ubuntu/](http://ma.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted
deb-src [http://ma.archive.ubuntu.com/ubuntu/](http://ma.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ma.archive.ubuntu.com/ubuntu/](http://ma.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe
deb-src [http://ma.archive.ubuntu.com/ubuntu/](http://ma.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe


---

### Post by b3tzi on 2006-11-18
Solved! :mrgreen:

---

### Post by FusionXN1 on 2006-11-19
Still cant see to create a rar archieve, i can open but cant see create. Any screenshots?

---

### Post by patrick295767 on 2006-11-19
> **FusionXN1 said:**
> Is there any software for linux that can create and extract rar files in a graphical interface like WINRAR for Windows?

WINRAR for linux only has command line :(

Thanks! :-D

xarchive too
> sudo apt-get -f -y install xarchive file-roller 
xarchive & file-roller &  # depending on your mood or preferences

---

### Post by FusionXN1 on 2006-11-20
I got the package "rar" and I can now create archives. Question though, it says "Shareware Version" and synaptic said 40days to register? Doe's this mean I have to purchase it? If so, is there another alternative to create rar archives for free?

Thanks. :mrgreen:

---

### Post by FusionXN1 on 2006-11-23
Anyone answer my question?

---

