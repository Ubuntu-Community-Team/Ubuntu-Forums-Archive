---
title: "[SOLVED] Any way to disable resticted drivers from recovery mode?"
date: 2007-10-14
forum: General Help
---

### Post by dorkdork777 on 2007-10-14
The long story :
[INDENT]I recently installed Kubuntu 7.10 RC, and everything worked fine - NVidia restricted drivers and all - until I tried to play WoW. After I quit it, the screen was zooming in on itself (as if KMag was filling the entire screen). Seeing no other way out, I reinstalled Kubuntu.

Then, on my fresh install, I enabled NVidia's restricted drivers, and restarted. After the Kubuntu loading bar filled up, the screen would turn black with an evil 'Mode not supported' error (the kind I get when I'm trying to force my monitor into a resolution it doesn't support), so I couldn't even log on, let alone get to the Restricted Drivers manager. The odd thing was, the restricted drivers worked fine in my previous install. Seeing no other way out, I reinstalled Kubuntu.

Now I've got a fully working desktop, but just with no 3D acceleration, so I can't enjoy a few rounds of Alien Arena in my spare time. I'd love to, but thanks to my previous install's problems, I'm slightly afraid to enable the restricted drivers, in case it gave me that error again.[/INDENT]

So basically, what I'd like to know, is this: would there be any way to revert to the non-restricted drivers (the nv drivers) in Kubuntu's Recovery Mode?

I'm still pretty much a Linux newbie, so I will need my hand held throughout the process, if it gets any more difficult than running a few commands.

Thanks in advance!

---

### Post by PmDematagoda on 2007-10-14
Try:-

```
sudo dpkg-reconfigure xserver-xorg
```

And select "nv" as the driver.

---

### Post by dorkdork777 on 2007-10-14
Thanks a lot - I enabled the restricted drivers, resarted my computer, and got the same message. I restarted again into Recovery Mode, and your command let me select the right drivers. Everything except 3D is now working perfectly again. :)

But that still leaves me with the problem of no Alien Arena...

---

### Post by PmDematagoda on 2007-10-14
Why don't you try this:-

1) Download the latest Nvidia driver for Linux from the Nvidia web site(The installation instructions are given)

2) After installation, run
```

sudo dpkg-reconfigure xserver-xorg
```
again

Then see if that made an improvement.

---

### Post by dorkdork777 on 2007-10-14
TBH, their instructions aren't massively clear... They say to type "sh NVIDIA-Linux-x86-100.14.11.pkg1.run" to install the driver. I started Konsole, typed 'cd Desktop', then ran that command. Failing that, I typed "sh '/home/chris/Desktop/NVIDIA-Linux-x86-100.14.11-pkg1.run'", then it told me it must be run as root, so I put sudo in front of the command, and ran it. It gave me this - 

>   ERROR: You appear to be running an X server; please exit X before
         installing.  For further details, please see the section INSTALLING
         THE NVIDIA DRIVER in the README available on the Linux driver
         download page at [www.nvidia.com](www.nvidia.com).

So I suppose I'm going to have to do this in Recovery mode?

---

### Post by PmDematagoda on 2007-10-14
Yes, or you will have to end the X-session, I did this installation by going to Recovery Mode as I don't know how to stop X in the normal sessions.

---

### Post by dorkdork777 on 2007-10-14
More problems!

I entered Recovery mode, ran the command, the installer started and told me that it is reccomended to exit the installer and switch to run level 3 (telint3) before installing. I ignored this and continued, accepted the licence agreement, and it told me that no precompiled interface was found, and shall the installer download a kernel interface for my kernel?

I said yes, and it said "Unable to connect to download.nvidia.com (unknown host)", and it would need to compile a kernel interface. It then said that I do not have libc header files installed, and that the install failed.


Any help?

---

### Post by PmDematagoda on 2007-10-14
You don't have a DSL or similar connection? How do you connect to the internet?

---

### Post by dorkdork777 on 2007-10-14
I have a wireless card but it doesn't work with Kubuntu, so I use a wireless adapter that plugs into the Ethernet port, and Kubuntu thinks it's a wired connection. It works out-of-the-box with no configuration or anything.

---

### Post by PmDematagoda on 2007-10-16
Do you have the "build-essentials" package installed?

If you haven't you will have to use:-

```
sudo apt-get install build-essential
```

I am not sure how to get it without an internet connection, so you will have to use your wireless one. After that, try the installation again and see if it works now.

---

### Post by dorkdork777 on 2007-10-18
No worries - I just updated to the final Kubuntu 7.10, and everything is working fine now! I've now fully switched to Kubuntu. I only boot into Windows for games, and with Wine getting better by the minute, it won't be long before I can run them perfectly under it (not to say that Ubuntu has no good games, however - I've just tried out Neverball and Alien Arena, and they're pretty damn sweet, and they're the first two games I've downloaded!). :D

TYVM for the help, BTW - without it, I'd have had to reinstall Kubuntu for the third time in one day, which I don't think anyone would enjoy doing!

---

