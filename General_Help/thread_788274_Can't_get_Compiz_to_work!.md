---
title: "Can't get Compiz to work!"
date: 2008-05-09
forum: General Help
---

### Post by jamieh on 2008-05-09
Hi,
I installed 8.04 yesterday (from scratch, no upgrade), and Compiz wasn't enabled by default (no surprise), so I followed this:

[http://howtoforge.com/compiz-fusion-ubuntu-8.04-nvidia-geforce-fx-5200]("http://howtoforge.com/compiz-fusion-ubuntu-8.04-nvidia-geforce-fx-5200")

It didn't work! I followed EVERY STEP carefully, but it still wouldn't work!
What am I doing wrong?
The only difference is he has a 5200, and I have a 5600XT.

Please help me!
Thanks!

EDIT:
Here is the output for "compiz --replace" in Terminal:

```
jamie@jamie-ubuntu:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0314 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Illegal instruction
```

EDIT AGAIN:
The propriatary nVidia driver is enabled, but Compiz didn't enable itself after the reboot, and when I went to Desktop Effects and enabled them, it said "Do you want to keep these settings" or something like that, and I said "Yes", but when I did, the window closed, and nothing changed. I go back to Desktop Effects, and it is disabled again!

---

### Post by macaholic on 2008-05-09
What is the output of compiz --replace from a comamnd line?

---

### Post by jamieh on 2008-05-10
> **macaholic said:**
> What is the output of compiz --replace from a comamnd line?

```
jamie@jamie-ubuntu:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0314 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Illegal instruction
```

---

### Post by jamieh on 2008-05-10
Sorry to bump, but I **really** need help with this!
Thank you!

---

### Post by Exsecrabilus on 2008-05-10
That guide explains exactly what I would explain.

I don't get your problem so there's nothing I can really do.

Sorry, I'm not that pro at Ubuntu myself.

---

### Post by kornguy26 on 2008-05-10
go to your package manager and install xgl and it should work

---

### Post by Exsecrabilus on 2008-05-10
Ubuntu 8.04 comes pre-installed with the *xserver-xgl* package.

But looking at your Terminal output, it seems that it is missing (like **Kornguy26** above me has already stated.)

Can you check if you have it installed?

---

### Post by jamieh on 2008-05-10
> **Exsecrabilus said:**
> Ubuntu 8.04 comes pre-installed with the *xserver-xgl* package.

But looking at your Terminal output, it seems that it is missing (like **Kornguy26** above me has already stated.)

Can you check if you have it installed?

How do you install XGL? (Sorry, I'm a noob)

---

### Post by skip mcshwang on 2008-05-11
Here's what I would do:

Completely remove compiz by typing this in the terminal:

> sudo apt-get remove --purge compiz* libcompizconfig*

Then use synaptic to reinstall compiz and compizconfig-settings-manager. (System > Administration > Synaptic Package Manager, double click "compiz" and "compizconfig-settings-manager" and then click Apply.)

---

### Post by Tomatz on 2008-05-11
Dont install xgl you dont need it with a nvidia card.

Compiz always checks for xgl when starting.

---

### Post by Tomatz on 2008-05-11
> **skip mcshwang said:**
> Here's what I would do:

Completely remove compiz by typing this in the terminal:



Then use synaptic to reinstall compiz and compizconfig-settings-manager. (System > Administration > Synaptic Package Manager, double click "compiz" and "compizconfig-settings-manager" and then click Apply.)


Yeah try that. From the output nothing should be wrong with compiz.

If it doesn't work:

```
sudo nvidia-settings
```

And see if tweaking your screen resolution and saving it to xorg.conf helps.

---

### Post by jamieh on 2008-05-11
> **Tomatz said:**
> Yeah try that

Sorry, it still doesn't work, when I enable desktop effects, then close the window, then re-open it, they are disabled again. If you don't get it, I've attached a video.

[http://www.youtube.com/watch?v=Y7LavRgitGs](http://www.youtube.com/watch?v=Y7LavRgitGs)

Please help!

---

### Post by jamieh on 2008-05-11
> **Tomatz said:**
> And see if tweaking your screen resolution and saving it to xorg.conf helps.
```

jamie@jamie-ubuntu:~$ sudo nvidia-settings
[sudo] password for jamie: 
sudo: nvidia-settings: command not found
jamie@jamie-ubuntu:~$ 


```

---

### Post by Tomatz on 2008-05-11
saw the video and that is strange. IMO considering compiz-fusions's output is fine and you have reinstalled it. It is your graphics drivers that are the problem, not compiz.

Have you tried envyng it automatically (well almost) downloads and installs the latest nvidia drivers.


[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)


Good luck


**P.s**

If you run into problems after installing the drivers with envyng and rebooting and you cant start gnome. Type the following at the cli (black screen of death lol) after loging in.

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

then

```
sudo shutdown -r now
```

Might be a good idea to write them down ;)

---

### Post by jamieh on 2008-05-11
This must be a big problem, because even after using Envy, it still won't work, it's still won't keep the Desktop Effects settings!

---

### Post by Galban on 2008-05-11
Listen, I have myself a Nvida GeForce 6200 and I got big hard time to get graphics acceleration with Hardy (nvidia-glx-new). I have been checking lots of threads about Nvidia+Compiz+Hardy in this forum and curiously almost nobody having GPU's newer than GeForce 7 series were having any troubles to get graphics acceleration up and running . The hard work done by a guy (lessgov2007) that manage to find out that latests drive released by Nvidia are NOT any more supporting the Nvidia GeForce 6200.Now your case once again, a GPU older than a 6 series (yours is 5) is showing exactly the same symptoms. With those elements founded the only possible statements is only one:  Nvidia is pushing people with "old" GPU's to buy newer ones. But, there is the solution founded by lessgov2007.. install a driver version that were still supporting the 6 and older series. That HOW-TO is in the post #11 in this thread ---->    [http://ubuntuforums.org/showthread.php?t=780425]("http://ubuntuforums.org/showthread.php?t=780425")

---

### Post by jamieh on 2008-05-11
Here's my Xorg.conf:

```
Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "us"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver        "nvidia"
    Option        "NoLogo"    "True"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    Defaultdepth    24
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
    Load        "glx"
EndSection
```

---

### Post by jamieh on 2008-05-11
> **Galban said:**
> Listen, I have myself a Nvida GeForce 6200 and I got big hard time to get graphics acceleration with Hardy (nvidia-glx-new). I have been checking lots of threads about Nvidia+Compiz+Hardy in this forum and curiously almost nobody having GPU's newer than GeForce 7 series were having any troubles to get graphics acceleration up and running . The hard work done by a guy (lessgov2007) that manage to find out that latests drive released by Nvidia are NOT any more supporting the Nvidia GeForce 6200.Now your case once again, a GPU older than a 6 series (yours is 5) is showing exactly the same symptoms. With those elements founded the only possible statements is only one:  Nvidia is pushing people with "old" GPU's to buy newer ones. But, there is the solution founded by lessgov2007.. install a driver version that were still supporting the 6 and older series. That HOW-TO is in the post #11 in this thread ---->    [http://ubuntuforums.org/showthread.php?t=780425]("http://ubuntuforums.org/showthread.php?t=780425")

I don't understand any of that, sorry.

---

### Post by Tomatz on 2008-05-11
> **Galban said:**
> Listen, I have myself a Nvida GeForce 6200 and I got big hard time to get graphics acceleration with Hardy (nvidia-glx-new). I have been checking lots of threads about Nvidia+Compiz+Hardy in this forum and curiously almost nobody having GPU's newer than GeForce 7 series were having any troubles to get graphics acceleration up and running . The hard work done by a guy (lessgov2007) that manage to find out that latests drive released by Nvidia are NOT any more supporting the Nvidia GeForce 6200.Now your case once again, a GPU older than a 6 series (yours is 5) is showing exactly the same symptoms. With those elements founded the only possible statements is only one:  Nvidia is pushing people with "old" GPU's to buy newer ones. But, there is the solution founded by lessgov2007.. install a driver version that were still supporting the 6 and older series. That HOW-TO is in the post #11 in this thread ---->    [http://ubuntuforums.org/showthread.php?t=780425]("http://ubuntuforums.org/showthread.php?t=780425")


That makes sense.

Basically you will have to get older drivers. I will have a hunt for some.

---

### Post by jamieh on 2008-05-11
Where can the old drivers be found, and how do I install them?

---

### Post by Tomatz on 2008-05-11
Here is one:

[http://www.nvidia.com/object/linux_display_ia32_100.14.11.html](http://www.nvidia.com/object/linux_display_ia32_100.14.11.html)

Its about a year old so if the problem is with the newer drivers, this should work.

Installation instructions in the link below:

[http://www.adamspotton.com/node/1](http://www.adamspotton.com/node/1) [B]<==HOWTO
[/B]

Really hope this works for you. Just take your time and double check commands before you enter them.

**To execute the driver (at the cli, step 6 in the howto) make sure it is downloaded to your _home folder_, rclick on it then click properties, permissions, _check_ allow executing as a program. Then when you get to _step 6_ type:**

> sudo sh NVIDIA-Linux-x86-100.14.11-pkg1.run   [COLOR="Red"]<==write that down[/COLOR]

**Let it rewrite your xorg.conf**

Post back if you get stuck :)

---

### Post by Galban on 2008-05-11
=; People!!!, don't look too far . Right here in this thread it is the solution for our problem, let's say an EnvyNG way, easy, safe and fast, the only thing it is to don't let it install the lastest one (driver). [COLOR="Red"]PLEASE!! refer to this thread, post #11 ---> [http://ubuntuforums.org/showthread.php?t=780425]("http://ubuntuforums.org/showthread.php?t=780425") [/COLOR], there is the explanation to HOW-TO proceed and fix this issue of Nvidia new drivers with GPU's older than the 6 series.Fallow the steps described on it, and I'm ready to bet its gonna work.

---

### Post by jamieh on 2008-05-12
> **Tomatz said:**
> Here is one:

[http://www.nvidia.com/object/linux_display_ia32_100.14.11.html](http://www.nvidia.com/object/linux_display_ia32_100.14.11.html)

Its about a year old so if the problem is with the newer drivers, this should work.

Installation instructions in the link below:

[http://www.adamspotton.com/node/1](http://www.adamspotton.com/node/1) [B]<==HOWTO
[/B]

Really hope this works for you. Just take your time and double check commands before you enter them.

**To execute the driver (at the cli, step 6 in the howto) make sure it is downloaded to your _home folder_, rclick on it then click properties, permissions, _check_ allow executing as a program. Then when you get to _step 6_ type:**



**Let it rewrite your xorg.conf**

Post back if you get stuck :)

Sorry, I'm ditching Ubuntu for KDE, I used Kubuntu on my friends computer and got hooked :)
Will these work for Kubuntu 8.04 (KDE3 Edition)?

In short, I want to get Compiz on Kubuntu 8.04.

Thanks for all your help Tomatz! (And others)

And could you please help me with this?
[http://ubuntuforums.org/showthread.php?t=792244](http://ubuntuforums.org/showthread.php?t=792244)

Thanks again, Tomatz! (Is that your real name??, do you like tomatoes?)

---

### Post by jamieh on 2008-06-07
What's the latest driver that still supports Compiz?

I have an nVidia GeForce FX 5600XT.

Thx

---

### Post by Tomatz on 2008-06-07
> **jamieh said:**
> What's the latest driver that still supports Compiz?

I have an nVidia GeForce FX 5600XT.

Thx

My friend has 8.04 running compiz on a FX5500 so a FX5600 should work.

---

