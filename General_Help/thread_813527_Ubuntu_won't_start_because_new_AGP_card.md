---
title: "Ubuntu won't start because new AGP card"
date: 2008-05-30
forum: General Help
---

### Post by brit0n on 2008-05-30
OK simple situation. I installed an AGP card and ran it in Windows. Now I reboot to Ubuntu and it fails to boot because of X files or some similarly names thing which I assume is the lack of the driver. I choose the options to look at the log and it tells me I don't have screens - it tells me this on two screens lol

I reboot to Windows and go and get a Linux driver for the new card - NVidia so it covers every card to date bar some really old legacy drivers. While there, I also print out the instructions on how to install. Seems easy enough so I stick the driver file where I should be able to get access to it - two places just in case: 1 on a USB stick and 2 on another drive which doesn't have any operating system but is in the PC not on the Network.

I reboot into Ubuntu again and let it fail doing the X-files thing. I don't bother to get the log this time. I am left at a login prompt so I log in (successfully).

Now if I understand this correctly, right now, all I have to do is to follow the instructions:

1. Change to the directory where I copied the driver file (*.run) - the NVidia instructions say:

 # cd yourdirectory

First question, how do I do this? I don't have # but I have some complicated $ thing at the start of the line (I can't look as I have to be in Windows to send this question). How can I see my other drives if Ubuntu hasn't booted? I tried all the old DOS type commands I can think of and I tried getting a list of commands none of which seemed to offer a way to do it. Even if I can't get to the USB stick, I ought to be able to get the command prompt pointing at the other hard drive partition I copied the file to, right?

2. If I ever manage to switch to that drive, I then need to run the following command:

 # sh thenameofthedriverfile

Do I need to use SUDO or something for that? Is that hash # important or is that the prompt that I don't get? Is sh something that I should be warned about or is it a very weird way of saying "run" or something? (I didn't see anything like it in the list of commands, which is why I am asking.)

I suppose the obvious question I should add is:

3. My understanding of Ubuntu was that it was designed to allow non-Linux users to use Linux without having to learn the entire OS from the bottom up. This, as I read it up before I chose Ubuntu, included automatic driver installation/updating. Is there some way I can give Ubuntu that driver to install automatically when I reboot or some similar process whereby I don't get thrown back to what looks remarkably like an old DOS screen?

Any help would be greatly appreciated. Please tell me what to do and also what it means I will be doing. Telling me to "Type xyz and do a jkq" is no use at all as I never let my PC run me lol "Type xyz - this is a command to make the OS list available partitions. Then do a jkq - this is a means of telling the OS that the file you are about to run is a graphics driver file (if you don't understand that, see <link> for details" would be EXCELLENT! Thanks!

---

### Post by eriqjaffe on 2008-05-30
Probalby the easiest way to install nVidia drivers is through a program called EnvyNG.

Since you can't launch X, you'll need to use the "text-only" version of EnvyNG:

```
sudo apt-get install envyng-core
```

...which will install EnvyNG, assuming your system has internet access.

```
sudo envyng -t
```

...will launch EnvyNG in text mode.

See [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) for details about EnvyNG.

---

### Post by MrFSL on 2008-05-30
Few things

1) Which model nvidia driver did you buy? You can post the output of ```
lspci | grep -i nvidia
```

2) Ubuntu suggests using the Restricted Driver Manager not the nvidia driver binary.

I suggest booting to a terminal (i.e. no graphics) and running:

```
sudo dpkg-reconfigure -phigh xserver-xorg
``` ... and follow the prompts.

3) Lastly, (FYI) the "no screens" error is more then likely referring to the "screens" section of the Xorg configuration file.

---

### Post by brit0n on 2008-05-31
> **eriqjaffe said:**
> Probalby the easiest way to install nVidia drivers is through a program called EnvyNG.

Since you can't launch X, you'll need to use the "text-only" version of EnvyNG:

```
sudo apt-get install envyng-core
```

...which will install EnvyNG, assuming your system has internet access.

```
sudo envyng -t
```

...will launch EnvyNG in text mode.

See [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) for details about EnvyNG.

Thanks eriq - so far, this looks like the best bet. So I read the site and unfortunately that requires me to use Envy Legacy. Ubuntu doesn't seem to want to update itself until AFTER I get the GUI working. So first question: Can I get Ubuntu to update the kernel while at Grub or the command line? If I can, I can probably just carry on and use EnvyNG which should do everything else for me.

If not, I am pointed back to my original problem - I had to get the Debian package in somewhere that I could use it. To do that, I had to put it somewhere from another OS and then be able to access it from the (minimal) command line on failed boot. In which case, I could have run the NVidia package in the first place.

So I did a lot of reading and worked out a way of getting to the downloaded file(s). Finally I found out that I had to mount drives to get to them and I managed to do that (more like with a sledgehammer than I am used to doing but I wanted to do it fast).

Then I ran the NVidia package. Unfortunately this gave me all sorts of errors because it couldn't install header files or something and failed to download them.

So I rebooted into Windows (this Ubuntu reboot has so far taken 19 reboots into Windows to do one small driver update which makes me think there is a better way to do this otherwise why would so many people rave about Linux! lol).

Went back the Envy site to download the Debian package and printout the instructions. Unfortunately, this will now require me to do some stuff manually which will probably require another 10 hours of reading:

[INDENT]*"2) Enable Ubuntu's "universe" and "multiverse" repositories. See Point E."*[/INDENT]

This sent me to Point E which sent me to Enabling Extra Repositories at monkeyblog which told me I had to use something called Synaptic. I have no idea what that is and the only description it gave of how to do it required the GUI which I can't (yet) get to. So I don't think I can even try this method.

Which brings me back to what seems to be the SIMPLEST method that I have found so far.... EnvyNG. To do this, I need Ubuntu to update its kernel without requiring the Xserver (I don't know what that is so I may have got that part wrong).

So can I update Ubuntu to 8.04 (or later) from that command line interface I get to on failed boot? If so, how? (I can then use EnvyNG instructions I hope). If not, any other ideas?

---

### Post by brit0n on 2008-05-31
> **MrFSL said:**
> Few things

1) Which model nvidia driver did you buy? You can post the output of ```
lspci | grep -i nvidia
```

Any command in Ubuntu (even command line) is not going to reference any driver not yet installed - the downloaded driver is not yet known to Linux.

Which model driver? There is only one NVidia driver package - NVidia issues a universal Linux driver file and I have the latest version. This covers all except some very old legacy cards which are listed and do not include mine.

> 2) Ubuntu suggests using the Restricted Driver Manager not the nvidia driver binary.

I suggest booting to a terminal (i.e. no graphics) and running:

```
sudo dpkg-reconfigure -phigh xserver-xorg
``` ... and follow the prompts.

I don't know much about this but that looks awfully as though I am going to permanently change something in the configuration without solving the problem. Without knowing what that change is, I can't do that any more than I would have in any of the other OSs I have used over the last 40 years. If you can tell me what that command will do, I maybe could use it and undo it later so that I am at least back to where I am now. Or is that going to lead me to be able to get to the GUI, updating the kernel on the way and allow me to go back and use EnvyNG? If it is going to allow me to proceed, how is it going to get access to the NVidia driver?

> 3) Lastly, (FYI) the "no screens" error is more then likely referring to the "screens" section of the Xorg configuration file.

Thanks MrFSL that is very clear. When I eventually get into Ubuntu, I shall study that file and try to work out what is going on when I boot.

---

### Post by MrFSL on 2008-05-31
You obviously used to be a windows user:
> Any command in Ubuntu (even command line) is not going to reference any driver not yet installed - the downloaded driver is not yet known to Linux.

lspci lists all devices configured on the pci bus and references the manufacturer/ vendors, and products id against a known set. For this reason - regardless of what driver (or not installed) you have installed we can identify what chipset is in your hardware and how the system references it.

> Which model driver? There is only one NVidia driver package 
Sorry - I meant what model card did you buy.

> This covers all except some very old legacy cards which are listed and do not include mine.
Yes it might cover the newer cards however there are known bugs with the linux driver against the most modern chipsets (see the nvidia forums)

> I don't know much about this but that looks awfully as though I am going to permanently change something in the configuration without solving the problem. Without knowing what that change is, I can't do that any more than I would have in any of the other OSs I have used over the last 40 years. If you can tell me what that command will do, I maybe could use it and undo it later so that I am at least back to where I am now. Or is that going to lead me to be able to get to the GUI, updating the kernel on the way and allow me to go back and use EnvyNG? If it is going to allow me to proceed, how is it going to get access to the NVidia driver?

... where do I start. In linux the graphical end is run by a local server called the X server. By default this is the xorg server. You can think of the dpkg-reconfigure statement as a way of "reinstalling" this xorg program... so that you can get into the "initial installation wizard" (for lack of a better term). 

... What this command will do is update the /etc/X11/xorg.conf file which is the configuration file for this xorg server. 

However - don't take my word for it... THe answer to your question has been answered multiple times on this forum. ... Just search and see.

---

### Post by brit0n on 2008-06-01
> **MrFSL said:**
> You obviously used to be a windows user

Used to be? Haven't seen anything in Ubuntu yet to make me use Linux exclusively lol

OK MrFSL thanks. I should have kept up - I already used lsusb so lspci was obvious but I spent some time in tuxfiles catching up a little.

Still not sure what *lspci | grep -i nvidia* is going to report except maybe the driver for the old graphics card. Maybe I should reinstall the old graphics card, reboot into Linux, update Linux, then resintall the later card and use the EnvyNG system.

If I use *lspci | grep -i nvidia*, do I have to write the results down or can I get the output in a file available in another OS so that I can post it here?

It's only a 6200 card - I needed to sort this change out before I committed the new boxes to having an Ubuntu in their multiboot list.

I read up dpkg-reconfigure and I am still not sure how the OS is going to know how to display, but I assume it will revert to some default which, though nasty looking, will let me get Ubuntu running and updated after which it seems EnvyNG is the way to avoid having to do this at every kernel/driver update.

Thanks, I'll try it.

---

### Post by brit0n on 2008-06-01
OK I got into Ubuntu. Thanks MrFSL. I did the lspci and jotted down the relevant items. But then I did the reconfigure and got Ubuntu booted. Admittedly the screen won't fit whatever I do with the controls, but that is ok because it is allowing me to get all the updates done which is the most important part of this.

After that, I can use eriq's useful suggestion to get EnvyNG in which, if I understand it correctly, will allow future updating of Ubuntu and/or the nVidia driver to be done automatically.

Thanks to both of you for bearing with me and getting me to do the right kind of reading to understand a little more about Linux.

---

### Post by brit0n on 2008-06-02
I prematurely marked the thread as solved. Please trust me when I say that I  spent more than 15 hours since then trying to get this thing configured on ONE BOX ALONE including all the research before admitting defeat and marking it unresolved again.

Here is where I got to:

[INDENT]sudo dpkg-reconfigure -phigh xserver-xorg[/INDENT]
got me into Ubuntu. That allowed me to update 8.04 (Hardy Heron). That meant I could get EnvyNG installed (instead of Envy Legacy). So far, so good.

Unfortunately, my screen is now offset to the right and below (so I am missing parts of the screen) and my second monitor shows blank once Ubuntu completes the boot process. For the former, I tried using the monitor adjustments but that only messes up the other 4 OSs' settings when I reboot into them which is not how it should work; I can find no means of adjusting the screen settings in the GUI. For the latter, I cannot find any nVidia controls for setting dual-monitor settings. Furthermore, I cannot find anywhere that I can ensure that the monitor drivers are installed.

So far, so bad. If I run EnvyNG and choose manual, it asks me to choose a driver from a list of three none of these resembles anything I am getting from nVidia driver info for my card. I cannot work out how to use the nVidia nvidia-xconfig utility - I have a tar.gz file which I can open, but unpacking it doesn't allow me to follow the instructions in the nVidia readme. Attempting to run the unified nVidia driver file produces an error message saying that my Xserver needs to be stopped. Elsewhere, the system is telling me I am not running the Xserver.

Should I dump EnvyNG again and start going through the nVidia linux forums to try to use the unified drivers provided by nVidia? Or can I safely continue with the EnvyNG system without having to relearn how to invent the wheel every time hardware is changed on a box? If EnvyNG is the answer, how do I get my screen aligned and my dual monitor setup configured?

Relevant lspci output for this box is: (extracted from the 18 total lines of output)
00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev a2)
02:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)

---

### Post by 6205 on 2008-06-02
Linux = True P'N'P aka Plug and Pray :)

---

### Post by brit0n on 2008-06-02
> **6205 said:**
> Linux = True P'N'P aka Plug and Pray :)

Ha ha! But as I don't allow any other OS to set up my hardware without me manually monitoring it (at least) or more usually personally configuring it step by step, I certainly wouldn't want or expect a Linux distro to do it. One of the attractions of Linux as far as I am concerned.

I would accept EnvyNG doing it once I had monitored the changes it made a few times.

---

### Post by eriqjaffe on 2008-06-03
> **brit0n said:**
> Ubuntu doesn't seem to want to update itself until AFTER I get the GUI working. So first question: Can I get Ubuntu to update the kernel while at Grub or the command line?Hopefully this isn't a little too late, but...

If you just want to bring your installed packages up to date:

```
sudo apt-get update && sudo apt-get upgrade
```

...from a command-line (or in a terminal) will do the job - it's the **only** way I do it.

---

