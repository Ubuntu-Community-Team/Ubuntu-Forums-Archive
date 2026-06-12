---
title: "Lubuntu new installation"
date: 2023-02-04
forum: General Help
---

### Post by alexis0b on 2023-02-04
Hi everyone
I'm very new to this world and I've installed lubuntu for the first time on an ex-Windows machine.
The installation was completed successfully with the alternate amd-64 version and the boot loader was included as well on the same device containing the OS.
When I restarded the computer I couldn't get any video signal after the bios. This means I can also enter the bios and work in it but in the moment I close it and try to enter the OS, no video output whatsoever.
My system specs:

MB: Asus M5A78LM-LX3
CPU: AMD Athlon II X3 435 2.9GHz
GPU: NVIDIA GeForce GTX 460
RAM: 8GB DDR3 1600MHz (not sure about speed)
HDD: Seagate Barracuda 500Gb

---

### Post by guiverc on 2023-02-04
You didn't provide any release details, but I suspect you installed something old & *unsupported*.

The last *alternate* ISO Lubuntu released was in 2018-April (details can be found here - [https://help.ubuntu.com/community/LXDE-lubuntu/Alternate_ISO](https://help.ubuntu.com/community/LXDE-lubuntu/Alternate_ISO)) but that release completed its three years of supported life in 2021-April.

The *alternate* ISO was less flexible, but it worked on hardware with 768MB or less of RAM which was below that required for the *primary* ISOs.  Your usage of the *alternate* ISO seems strange given you've >1GB RAM.

The EOL detail for Lubuntu 18.04 LTS can be read here - - [https://lubuntu.me/bionic-eol/](https://lubuntu.me/bionic-eol/)

[Ubuntu 18.04 LTS release announcements]("https://fridge.ubuntu.com/2020/08/14/ubuntu-18-04-5-lts-released/") tell you

> Maintenance updates will be provided for 5 years for Ubuntu Desktop,  Ubuntu Server, Ubuntu Cloud, and Ubuntu Base.  All the remaining  flavours will be supported for 3 years.

where Lubuntu being a flavor, had 3 years only, ie. 2018-April through 2021-April.

Also if you go to Lubuntu's web site ([https://lubuntu.me/downloads/](https://lubuntu.me/downloads/)) I don't see any ALTERNATE ISO offered (*there hasn't been for year+*), so I'd check where you downloaded it from, as google will offer *fan & fake* sites as well as the legitimate site for Lubuntu downloads (*depending on your language used in search*).  It's up to the user of google to detect which are which (*though I've noted some security extensions warn when going to a illegitimate Lubuntu site*).

Did you use an official Ubuntu site?  or a Lubuntu site?  (*I suspect not!*).

If you want to a *fan* site, they usually don't do the download themselves (*saving bandwidth costs*), but point your download from a Canonical/Ubuntu site; so I'd check that's where it was from. If you used a *fake* site, I'd check where it was from, and what you actually installed.  I'm mentioning this due to what I suspect is an EOL release being used given the *alternate *ISO hasn't been supported by Lubuntu more than a year.

---

### Post by oldfred on 2023-02-04
UEFI or BIOS install?
What version? 22.04?
You probably are missing the nVidia driver. Not sure about Lubuntu but Ubuntu has Safe boot and you also choose to install optional restricted drives which would then include the nVidia driver.
Can you boot to grub menu. If only one system, you have to press escape key just after vendor logo, but before grub menu. Or if BIOS, press & hold shift key until grub menu appears.
Then can you boot recovery mode or second line in grub menu.

Turn on Internet & install nVidia driver.
[https://ubuntuforums.org/showthread.php?t=2380061](https://ubuntuforums.org/showthread.php?t=2380061)

Install nVidia If you just want default version - recommended one
sudo ubuntu-drivers autoinstall

Or:
# should show newest versions available in addition
ubuntu-drivers devices
You then can manually choose any in list.
sudo apt-get install nvidia-XXX

---

### Post by alexis0b on 2023-02-05
> **guiverc said:**
> You didn't provide any release details, but I suspect you installed something old & *unsupported*.

The last *alternate* ISO Lubuntu released was in 2018-April (details can be found here - [https://help.ubuntu.com/community/LXDE-lubuntu/Alternate_ISO](https://help.ubuntu.com/community/LXDE-lubuntu/Alternate_ISO)) but that release completed its three years of supported life in 2021-April.

The *alternate* ISO was less flexible, but it worked on hardware with 768MB or less of RAM which was below that required for the *primary* ISOs.  Your usage of the *alternate* ISO seems strange given you've >1GB RAM.

The EOL detail for Lubuntu 18.04 LTS can be read here - - [https://lubuntu.me/bionic-eol/](https://lubuntu.me/bionic-eol/)

[Ubuntu 18.04 LTS release announcements]("https://fridge.ubuntu.com/2020/08/14/ubuntu-18-04-5-lts-released/") tell you



where Lubuntu being a flavor, had 3 years only, ie. 2018-April through 2021-April.

Also if you go to Lubuntu's web site ([https://lubuntu.me/downloads/](https://lubuntu.me/downloads/)) I don't see any ALTERNATE ISO offered (*there hasn't been for year+*), so I'd check where you downloaded it from, as google will offer *fan & fake* sites as well as the legitimate site for Lubuntu downloads (*depending on your language used in search*).  It's up to the user of google to detect which are which (*though I've noted some security extensions warn when going to a illegitimate Lubuntu site*).

Did you use an official Ubuntu site?  or a Lubuntu site?  (*I suspect not!*).

If you want to a *fan* site, they usually don't do the download themselves (*saving bandwidth costs*), but point your download from a Canonical/Ubuntu site; so I'd check that's where it was from. If you used a *fake* site, I'd check where it was from, and what you actually installed.  I'm mentioning this due to what I suspect is an EOL release being used given the *alternate *ISO hasn't been supported by Lubuntu more than a year.

> **oldfred said:**
> UEFI or BIOS install?
What version? 22.04?
You probably are missing the nVidia driver. Not sure about Lubuntu but Ubuntu has Safe boot and you also choose to install optional restricted drives which would then include the nVidia driver.
Can you boot to grub menu. If only one system, you have to press escape key just after vendor logo, but before grub menu. Or if BIOS, press & hold shift key until grub menu appears.
Then can you boot recovery mode or second line in grub menu.

Turn on Internet & install nVidia driver.
[https://ubuntuforums.org/showthread.php?t=2380061](https://ubuntuforums.org/showthread.php?t=2380061)

Install nVidia If you just want default version - recommended one
sudo ubuntu-drivers autoinstall

Or:
# should show newest versions available in addition
ubuntu-drivers devices
You then can manually choose any in list.
sudo apt-get install nvidia-XXX




Thank you both for your replies, I will try to answer to everything.

Regarding the release, I found the .iso file of the OS at this link [https://lubuntu.net/downloads/](https://lubuntu.net/downloads/) and since the
[h=1][SIZE=3]**[COLOR=#0068c8]"[Download Latest lubuntu Version 19.04]("http://cdimage.ubuntu.com/lubuntu/releases/19.04/release/lubuntu-19.04-desktop-amd64.iso")"[/COLOR]**[/SIZE][/h]download button didn't work I went for the alternate version below.
Don't know if it is any good or too old, I found it just looking for linux distros and trying to understand which one was best for my needings. There was some kind of little quiz to select the best fitting distro at the previous page [https://www.linux.it/distro/](https://www.linux.it/distro/) but this is an italian site so I don't think there is any chance you know it.

Regarding the BIOS version I can't understand which are the correct numbers I should provide you so I attach a screenshot of the BIOS page:
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291712&stc=1[/IMG]
hope you can see it clearly.

Anyway, I can get to what I think is a GRUB menu and activate the recovery mode and also enable the network, but i don't understand how to download drivers and install them in this kind of interface, sorry it is the very first time I'm handling this system and I don't know what are the basics input commands.

---

### Post by ne29914 on 2023-02-05
This is where it went wrong.
The official site is lubuntu.me, not .net.
The latest LTS is 22.04, 20.04 LTS is active until April. 19.04 is ancient.

Good Luck.

---

### Post by alexis0b on 2023-02-05
Thanks!!
I'm going with a clean install of the newer version.
Thanks everyone

---

### Post by ajgreeny on 2023-02-05
Lubuntu 19.04 which you installed was supported for nine months only, so it lost any further support in or about January 2020, three years ago.

I have no information I can offer about nvidia drivers but my certainty is that it will be very unsafe for you to connect to the web with an unsupported OS which is now 3 years out of date and has received no updates in those 3 years.

The most recent long term support version of Lubuntu, 22.04, supported until April 2025, uses the same Desktop Environment (LXQt) as the version you have so will probably look very similar, but it's not an OS that I have used very much except to simply have a look at it as a Virtual Machine, so I can not tell you much about it.
However, I recommend that you download and try that version if you wish to stick with Lubuntu, which you can get from [https://cdimage.ubuntu.com/lubuntu/releases/22.04.1/release/lubuntu-22.04.1-desktop-amd64.iso](https://cdimage.ubuntu.com/lubuntu/releases/22.04.1/release/lubuntu-22.04.1-desktop-amd64.iso)

Good luck, but please, please do not continue using your 19.04 version particularly if you connect to the web as it is dangerous, not only for you but also for all other connected users, as your machine could potentially be hacked and turned into a bot, passing goodness knows what malware to others.

---

### Post by alexis0b on 2023-02-05
> **ajgreeny said:**
> Lubuntu 19.04 which you installed was supported for nine months only, so it lost any further support in or about January 2020, three years ago.

I have no information I can offer about nvidia drivers but my certainty is that it will be very unsafe for you to connect to the web with an unsupported OS which is now 3 years out of date and has received no updates in those 3 years.

The most recent long term support version of Lubuntu, 22.04, supported until April 2025, uses the same Desktop Environment (LXQt) as the version you have so will probably look very similar, but it's not an OS that I have used very much except to simply have a look at it as a Virtual Machine, so I can not tell you much about it.
However, I recommend that you download and try that version if you wish to stick with Lubuntu, which you can get from [https://cdimage.ubuntu.com/lubuntu/releases/22.04.1/release/lubuntu-22.04.1-desktop-amd64.iso](https://cdimage.ubuntu.com/lubuntu/releases/22.04.1/release/lubuntu-22.04.1-desktop-amd64.iso)

Good luck, but please, please do not continue using your 19.04 version particularly if you connect to the web as it is dangerous, not only for you but also for all other connected users, as your machine could potentially be hacked and turned into a bot, passing goodness knows what malware to others.

Thank you for your advice!
Actually, after previous recommendations in this thread, I've dowloaded the 22.04 version and installed it on the machine.
I've also installed the NVIDIA drivers for my graphic card through the root tool, but yet, after BIOS I can't get any video output.
What could I do?

---

### Post by alexis0b on 2023-02-06
Just to Resolve this thread:

In the end the solution was to
1) firstly install latest version of Lubuntu (22.04) with kernel 5.15
2) with Update software (Other drivers tab) install NVIDIA drivers for graphic card
3) 1920x1080 resolution was automatically set as default and video output restored

TO BE NOTICED:

After this process I started experiencing ethernet malfunction, for which the connection to the network cannot be established.
For this I'm opening a new thread in the corresponding category of this forum, since I couldn't find any solution online.

---

### Post by ajgreeny on 2023-02-07
Great!

I'm glad this us now sorted for you so please use the **Thread Tools** menu up top to mark this thread as SOLVED.

It is a great help to other users searching thefirum.

---

