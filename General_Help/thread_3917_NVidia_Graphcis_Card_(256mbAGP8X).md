---
title: "NVidia Graphcis Card (256mb/AGP8X)"
date: 2004-11-10
forum: General Help
---

### Post by dubdubdub on 2004-11-10
I recently built this PC for gaming (before my obsession with Ubuntu consumed my need for gaming!). I put a 256mb NVidia graphics card in it. What can I do to tell if the right drivers are installed and that it is infact utilizing all of that videoram?

In device manager the only video card I can see is:
"NVidia [GeForce FX 5200]
Bus Type: PCI

But as stated above, it is in an AGP slot.

I am sometimes experiencing lags when maximizing windows and dragging windows. Doesn't seem right for a system with AMD Sempron 2500+ (1.8ghz), 512mb DDR400 and a 256mb video card.

Any help on this would be greatly appreciated!

Tia-dub

---

### Post by ubuntu-geek on 2004-11-10
If you havent already.

sudo apt-get install nvidia-glx
sudo nvidia-glx-config enable

Then make sure you have something like this in your /etc/X11/XF86Config-4, I just copy and pasted mine.

> Section "Device"
        Identifier      "NVIDIA Corporation NV18 [GeForce4 MX - nForce GPU]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
EndSection

---

### Post by JonAtkinson on 2004-11-10
You might also want to try downloading the package nvidia-settings.

If you run it from the comman line (It doesn't install a menu item, unfortunately);```
$ nvidia-settings
```you can get all sorts of information about the card and driver, and also modify some hardware settings such as cursor shadow, hardware gamma and suchlike.

Cheers,

--Jon

---

### Post by dubdubdub on 2004-11-10
Specifically I have a NVidia 5200. Is it the same even for that card?

thanks for all your help

---

### Post by jdodson on 2004-11-10
[QUOTE=dubdubdub]Specifically I have a NVidia 5200. Is it the same even for that card?

thanks for all your help[/QUOTE]

yep.  nvidia is that good :-)

---

### Post by dubdubdub on 2004-11-10
hrmmm.....so yeah what does this mean? heh

> dub@ubuntu:~ $ sudo apt-get install nvidia-glx
Password:
Reading Package Lists... Done
Building Dependency Tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  nvidia-glx: Depends: nvidia-kernel-1.0.6629 but it is not installable
E: Broken packages
dub@ubuntu:~ $


And if I try to install with Synaptic, I get this error: 
>  nvidia-glx:
 Depends: nvidia-kernel-1.0.6629  but it is not installable
 

---

### Post by FLeiXiuS on 2004-11-11
[QUOTE=dubdubdub]hrmmm.....so yeah what does this mean? heh



And if I try to install with Synaptic, I get this error:[/QUOTE]


I'd update your apt client.

```

sudo apt-get update
sudo apt-get upgrade

```

Then go about installing the nvidia packages again.

```

sudo apt-get install nvidia-glx

```


**BE SURE TO ENABLE UNIVERSE!**
[http://ubuntuforums.org/showthread.php?t=179](http://ubuntuforums.org/showthread.php?t=179)

---

### Post by dubdubdub on 2004-11-11
I updated and made sure universe was enabled in /etc/apt/sources.list. I still get the following error:

> dub@ubuntu:~ $ sudo apt-get install nvidia-glx
The following packages have unmet dependencies:
  nvidia-glx: Depends: nvidia-kernel-1.0.6629 but it is not installable
E: Broken packages


And if this helps, here is my sources.list 
>  deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted


deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main


deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main

deb [http://ftp.kulnet.kuleuven.ac.be/debian/](http://ftp.kulnet.kuleuven.ac.be/debian/) unstable non-free contrib



does that look right?

---

### Post by mercurus on 2004-11-11
The version number looks like the new nvidia drivers released a few days ago. It doesn't look as though the archive's repository has quite everything that is required though. Basically, I'd guess that the nvidia-glx package is a bit broken at the moment.

Try and download an earlier version and use dpkg to install it and its dependencies. Alternatively, just wait for the archive to catch up :)

Cheers
mercurus

---

### Post by dubdubdub on 2004-11-11
So if I would have installed Ubunutu say, 3 weeks ago, I would have been able to install it then?

I will keep running apt-get update and apt-get upgrade peridoically until it lets me install it. 

On that note, I am suprised at how quickly updates are available. Do those commands update the OS or the OS and all of its components and 3rd party applications?

Apple only releases an OS update like every few months. Security updates every 2-3 weeks.

---

### Post by candymanobh3 on 2004-11-14
GoTo this website: [http://kanotix.com/files/](http://kanotix.com/files/) 

Scroll down till you see "Install scripts for graphic cards after HD install" 

Download the nvidia script and remember where you downloaded it to. 

Press/Hold Ctrl+Alt+F1 

Login @ the prompt. 

Now you are logged in change to the directory that you downloaded the scripts to: 
```
cd /your/download/location/
``` 

next to run script type "sudo sh nameofscript.sh" e.g: 

```
sudo sh install-nvidia-6629-debian.sh
``` 

This script will download, compile, and install the nvidia driver of your choosing. 

When process is complete and you are back at the prompt -if not automatic- type "startx" and you will be back in familiar territory. 

If this is confusing please let me know as I am working completely from memory here. My own computer's power supply is dead. 

--Good luck.

---

### Post by Razvan on 2004-11-14
[QUOTE=candymanobh3]GoTo this website: [http://kanotix.com/files/](http://kanotix.com/files/) 

Scroll down till you see "Install scripts for graphic cards after HD install" 

Download the nvidia script and remember where you downloaded it to. 

Press/Hold Ctrl+Alt+F1 

Login @ the prompt. 

Now you are logged in change to the directory that you downloaded the scripts to: 
```
cd /your/download/location/
``` 

next to run script type "sudo sh nameofscript.sh" e.g: 

```
sudo sh install-nvidia-6629-debian.sh
``` 

This script will download, compile, and install the nvidia driver of your choosing. 

When process is complete and you are back at the prompt -if not automatic- type "startx" and you will be back in familiar territory. 

If this is confusing please let me know as I am working completely from memory here. My own computer's power supply is dead. 

--Good luck.[/QUOTE]
 did it help?

im allways a bit sceptic about those scrips, but thats my personal paranoia ;-) 

try taking hoary out of your sources.list, do a reload in synaptic...it should now have the nvidia-6111-driver which works great

install it, enable it, then you can turn hoary back on ;-)

---

### Post by Razvan on 2004-11-14
whoops, im sorry!

this is one of the good scripts!!!!

---

