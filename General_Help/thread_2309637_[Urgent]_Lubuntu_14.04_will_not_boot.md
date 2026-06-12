---
title: "[Urgent] Lubuntu 14.04 will not boot"
date: 2016-01-12
forum: General Help
---

### Post by ubupro97 on 2016-01-12
As far as I can tell I did not do anything unusual. I did mess around with libinput, installed a version and a package and then removed it. 
Okay, so to try nuke mouse acceleration I installed this package:
[http://packages.ubuntu.com/xenial/libinput10](http://packages.ubuntu.com/xenial/libinput10)

and I tried to install this package, but there was a missing dependency which I tried to install:
[http://packages.ubuntu.com/xenial/xserver-xorg-input-libinput](http://packages.ubuntu.com/xenial/xserver-xorg-input-libinput)

I installed [B][SIZE=1][FONT=arial]xserver-xorg-core-livid (from trusty1) and xserver-xorg-core-utopia (from trusty2) or something. I still couldn't install the previous package, so I sudo apt-get purge 'd all three. That's all I can remember that I did during this boot. (RIP formatting)

[/FONT][/SIZE][/B]Edit: I was testing this: [https://www.reddit.com/r/linux_gaming/comments/3zypm1/172016_update_for_cs_go_fixes_headphone_and/cyq5ua2](https://www.reddit.com/r/linux_gaming/comments/3zypm1/172016_update_for_cs_go_fixes_headphone_and/cyq5ua2)


When attempting to boot:
[COLOR=#333333][FONT=arial]The screen is blank and nothing happens. When I load recovery, I can drop to terminal at tty1. tty7 is blank with a flashing cursor. I tried doing sudo reboot gdm (running GNOME3, removed lightdm) with no luck.[/FONT][/COLOR]

---

### Post by Bashing-om on 2016-01-12
ubupro97; Ouch !

This may take a lot of time, effort and frustration to resolve.
I do think that we have to lay the foundation for the GUI to run in as the 1st priority.
So what are we working with ? :
```

uname -r
apt-cache policy linux-generic-lts-*
apt-cache policy xserver-xorg-core-lts-*
apt-cache policy xserver-xorg-lts-*
apt-cache policy xserver-xorg-video-all-lts-*
apt-cache policy xserver-xorg-input-all-lts-*
apt-cache policy libwayland-egl1-mesa-lts-*

```
Let's determine what level of HWE we are dealing with.

And what is the display hardware/driver ? :
```

lspci -vnn | grep -i VGA
sudo lshw -C display

```

Before we get too deep, we know we will have to have access to the software repository, what state is the package manager in ? :
```

sudo apt update
sudo apt upgrade

```

[INDENT][INDENT]oh Boy
[INDENT][INDENT][INDENT]this might get real fun
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ubupro97 on 2016-01-12
> **Bashing-om said:**
> 
And what is the display hardware/driver ? :
```

lspci -vnn | grep -i VGA
sudo lshw -C display

```


If it's easier for you, I can easily do a fresh install. Partitions are in an uglier arrangement anyway.

I'm not sure how to save the logs from these commands to a flash drive. I have access to an installation of Ubuntu 14.04 on a different drive if that helps.'

My display hardware is NVIDIA GTX 660 (2GB), running driver version 355.11 (proprietary). I also have Intel integrated graphics on the system (enabled in BIOS) which I believe work for the sake of debugging (HD 4400 on i3-4170).

> 
Before we get too deep, we know we will have to have access to the software repository, what state is the package manager in ? :
```

sudo apt update
sudo apt upgrade

```


I did this just before the reboot that broke everything, all updates were up to date. There are some packages held back for whatever reason. I recently did sudo apt autoremove.

---

**Edit**

Disclaimer: Not knowing how to transfer logs, I am writing notes on my phone and posting them here.

I  removed the outputs from my discrete graphics card (HDMI and DVI) and  plugged in a display to my motherboard (VGA) and tried booting to no  luck.

Then I checked the package manager. Packages no longer  needed and can be removed with sudo apt autoremove had some important  looking ones I recognised:

x11-apps
x11-session-utils
xinit
xinput
policykit-desktop-privileges
...
(10 total)

So did I somehow remove xinput which is my only way of interacting with the xserver..?

There were also some packages held back, all ending in '-lts-vivid'

---

### Post by Bashing-om on 2016-01-12
ubupro97; Hey ...

It is your system and your call as to what you want to do . I (we) am (are) here to assist .

There is little to learn in taking that nuclear solution of a (RE-)install; Though a much faster means to reach resolution of this issue. In a (RE-)install we learned from past errors in judgement and means .. do not repeat in making the new install . Now that is progress.

If you want to try and repair this install we continue ... to make things easier on you and less prone to error, we can use our pastebin site for the deposit of command's outputs.
```

sudo apt install pastebinit

```
then run - for an instance:
```

uname -r | pastebinit

```
the result is a URL back in terminal ... pass that link back here to the channel and we can then access that file.

Similarly:
```

apt-cache policy linux-generic-lts-* | pastebinit

```

We get the xserver libraries' version compatible, then we consider re-installing the graphic's driver .

Maybe
[INDENT][INDENT]no step for a stepper
[/INDENT][/INDENT]

---

### Post by ubupro97 on 2016-01-13
> **Bashing-om said:**
> ubupro97; Ouch !

```

uname -r

3.19.0-37-generic
```

```
apt-cache policy linux-generic-lts-*

``` 
Oops, missed one.

```
apt-cache policy xserver-xorg-core-lts-*
```
[http://pastebin.ubuntu.com/14484229/](http://pastebin.ubuntu.com/14484229/)

```
apt-cache policy xserver-xorg-lts-*
```
[http://pastebin.ubuntu.com/14484229/](http://pastebin.ubuntu.com/14484229/)

```
apt-cache policy xserver-xorg-video-all-lts-*
```
[http://pastebin.ubuntu.com/14484232](http://pastebin.ubuntu.com/14484232)

```
apt-cache policy xserver-xorg-input-all-lts-*
```
[http://pastebin.ubuntu.com/14484240](http://pastebin.ubuntu.com/14484240)

```
apt-cache policy libwayland-egl1-mesa-lts-*
```
Package was not found.


> And what is the display hardware/driver ?
```
lspci -vnn | grep -i VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation Device [8086:041e] (rev 06) (prog-if 00 [VGA controller])
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GK106 [GeForce GTX 660] [10de:11c0] (rev a1) (prog-if 00 [VGA controller])
```


```
sudo lshw -C display
```

[http://pastebin.ubuntu.com/14484269/](http://pastebin.ubuntu.com/14484269/)


```
sudo apt upgrade

Reading package lists...
Building dependency tree...
Reading state information...
The following packages were automatically installed and are no longer required:
  linux-headers-3.19.0-33 linux-headers-3.19.0-33-generic
  linux-image-3.19.0-33-generic linux-image-extra-3.19.0-33-generic
  linux-signed-image-3.19.0-33-generic policykit-desktop-privileges x11-apps
  x11-session-utils xinit xinput
Use 'apt-get autoremove' to remove them.
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
```

---

### Post by Bashing-om on 2016-01-13
ubupro97; Well ...

Do not know enough yet to make a call .. You say you are running 14.04 .. BUT but but ... you are running vivid's kernel and do not have the supporting xserver packages installed .

Verify what release you are running ... and then if it is indeed 14.04 we install the supporting structures .
You are of optimus (hybrid graphic's) and have the nvidia driver installed ... I can see that in installing the xserver packages that the driver will break .. no big deal  .. as upon completion of the installs we purge and re-install the driver .

So, show us what you are running for a fact.
```

cat /etc/issue
lsb_release -a 

```

[INDENT][INDENT]I think, I do think
[/INDENT][/INDENT]

---

### Post by ubupro97 on 2016-01-14
> **Bashing-om said:**
> ubupro97; Well ...

Do not know enough yet to make a call .. You say you are running 14.04 .. BUT but but ... you are running vivid's kernel and do not have the supporting xserver packages installed .

Verify what release you are running ... and then if it is indeed 14.04 we install the supporting structures .
You are of optimus (hybrid graphic's) and have the nvidia driver installed ... I can see that in installing the xserver packages that the driver will break .. no big deal  .. as upon completion of the installs we purge and re-install the driver .

So, show us what you are running for a fact.
```

cat /etc/issue
lsb_release -a 

```

A couple things: I don't believe I ever manually forced updating the kernel. This is 14.04.3 LTS. I may have stupidly followed something apt told me and forcibly installed an update meant for vivid. I don't believe I am using Optimus, I just have two separate graphic units which the intel one is never used to render anything (I don't get the Optimus options for selecting a which GPU does what on Windows, I usually don't bother installing the intel driver on Windows). I had set the motherboard to keep the integrated graphics enabled (with IDG Multi-Monitor enabled) for debugging purposed, but had not run anything off of it. When this issue occurred I plugged a spare VGA monitor into the motherboard and unplugged my discrete GPU's outputs in case that solved anything. It did not, but I am still using it, hence the two graphics units in use (I have a third monitor not doing much at the moment).


```

$ cat /etc/issue
Ubuntu 14.04.3 LTS \n \l 

$ lsb_release -a 
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty
```

For reference, you're probably onto something (if you didn't know that) given that my install of Ubuntu 14.04 (not Lubuntu) says I'm running 3.16.0-52-generic.

[B]Edit:

[/B]I doubt these wi**l**l be of any use, but I booted from an older kernel version of Lubuntu which I found in grub (recovery mode), resumed normal boot and then there were some logs visible in tty7 (ctrl+alt+f7) which I still don't know how to view as a file, but I took a picture with an old iPod:

[https://imgur.com/BUUPQIg](https://imgur.com/BUUPQIg)

Minor Edit: Thanks imgur for having ambiguous characters [It showed |g which I thought was an l (lowercase L) rather than an I (uppercase i)]

**Edit 2**:

I'll quickly add which I haven't mentioned previously, I have installed GNOME3 and I am running gdm with lightdm removed. I believe I left the DE itself installed (I currently have two terminal emulators).

---

### Post by Bashing-om on 2016-01-14
ubupro97; Wellllpp;

Let say that you installed 14.04 some time after the 1st point release, as such the release would have been HWE enabled by default.
So now we need to install the supporting xserver packages for the 3.19.0-37-generic kernel which is vivid's kernel.
Let's do:
```

sudo apt-get install --install-recommends linux-generic-lts-vivid xserver-xorg-core-lts-vivid xserver-xorg-lts-vivid xserver-xorg-video-all-lts-vivid xserver-xorg-input-all-lts-vivid libwayland-egl1-mesa-lts-vivid

```
see: [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)
for the background info.

I can foresee we will have to re-install the graphic's driver - maybe - . We cross that bridge when we get to it . We see if the system reboots to the GUI after the xserver packages are installed.

[INDENT][INDENT]could be
[INDENT][INDENT][INDENT]nothing but a thing
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ubupro97 on 2016-01-15
> **Bashing-om said:**
> ubupro97; Wellllpp;

Let say that you installed 14.04 some time after the 1st point release, as such the release would have been HWE enabled by default.
...


Just quickly while I'm out before I get home to try that, what exactly is HWE and what impact is it having here? I installed this copy of 14.04 this year.

---

### Post by Bashing-om on 2016-01-15
ubupro97; Hey ...

Prudent to make sure that you know what you are doing .. the link I provided above gives all the relevant info as the what HWE is and why . Says it much better than I can ... but in essence it is using a later release kernel in an older install. We must have the supporting xserver packages for the kernel in use. Presently you do not have these xserver packages installed.

The graphics driver is dependent on these packages, and we do not know the state of the driver at this time. Nor, what the state of the graphic's driver will be when the xserver packages are installed. 
We just re-install a driver after the xserver packages are installed - as required.

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by ubupro97 on 2016-01-15
> **Bashing-om said:**
> ubupro97; Wellllpp;
```

sudo apt-get install --install-recommends linux-generic-lts-vivid xserver-xorg-core-lts-vivid xserver-xorg-lts-vivid xserver-xorg-video-all-lts-vivid xserver-xorg-input-all-lts-vivid libwayland-egl1-mesa-lts-vivid

```


Thanks for the link.

I've got no idea what the argument "--install-recommends" does, but I didn't get much in terms of output from the above command (yes I used sudo and correctly entered my su password).

Output:
[https://paste.ubuntu.com/14514227](https://paste.ubuntu.com/14514227)

Edit: The paste didn't work properly, it had two messages that read "E: <package> could not be found". One was libwayland-egl1-mesa-lts-vivid, can't remember the other.

I did apt-get update and apt-get upgrade and tried again to the same lack of useful output.

---

### Post by Bashing-om on 2016-01-16
ubupro97l Hey ...

On a positive result from a command there will be no return back to the screen - just the system doing as it was told and no back talk or sass about it.

So, now we want to know the status of the packages and the package manager.
Post back:
```

sudo apt update
sudo apt upgrade
sudo apt install -f
sudo dpkg -C
sudo lshw -C display

```

And we see what there is to do.

[INDENT][INDENT]there is a way that seems right
[INDENT][INDENT][INDENT]but leads to a broken system
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

