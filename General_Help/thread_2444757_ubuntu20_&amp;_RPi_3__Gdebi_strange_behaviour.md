---
title: "ubuntu20 &amp; RPi 3 : Gdebi strange behaviour"
date: 2020-06-03
forum: General Help
---

### Post by richard-g8jvm2 on 2020-06-03
Hi
I package a Ham software application for a friend
4 varieties , amd64 for ubuntu and linuxMint, armhf for ubuntu on Harkernel Odroids , arm64 for RPi 3 & 4 running ubuntu20 & a mess for raspberry PI's runing raspbian.
I've newly configure a RPI3B with Ubuntu 20 today and compiled the program and packaged it as a .deb
At the moment I'm using a Mate desktop
Strange behaviour I havn't seen before, 
I've FTP'd the .deb up to the home dir and there are two deps, pulseaudio and fftw3
pulse is installed by default 
but when you click on install with gdebi to load fftw3 , it disappears, then you get the password request, then it disappears again.
You have to click on the top panel to get it to reappear, and then it say install failed as another installation in progress.
so shut it down and open a terminal
try to manually load fftw3 with apt, and you get the message
run dpkg --configure -a
so run it, after about 5 mins back to normal and manually run apt install fftw3
that installs
back to the desktop and run gdebi and the wanted file installs, in to /usr/local/sbin
the program runs OK from CLI

However, nothing appears in the menu, even though the desktop icon has been loaded in to /usr/share/applications/
I admit I'm new to running ubuntu on a RPi, I normally use linux mint on both PC's and ubuntu18 on both of the hardkernel odroids (ARM SBCs)
I'm already developing feelings of hate and destruction towards raspberry PIs, I only borrowed this one to try and sort out a raspbian bug,
 only one of the contacts in the SD Card connector was bent, and to keep the peace I've replaced the RPI with a new one, and repaired the one with a new SD 
Card connector.

Is this normal behaviour for a RPI running Ubuntu20  ?, my other ARM SBCs are odroids and runing ubuntu18, without problems, and with Mate desktops.
it seems very underpowered, its nearly as bad as the early computers when I started with Redhat 4, when building a kernel ,.go to bed and hope it finished by the morning.
yep I'm ancient as well !

---

### Post by richard-g8jvm2 on 2020-06-04
Looks like I'm not going to get any help as I mentioned I use linux mint !
But in case
I've reinstalled on the RPI3B and selected Lubuntu desktop

It runs OK, but I need some help with packaging an application that can be installed by anyone using Lubuntu
At the moment my package app in .deb format is ignored by the KDE version of synaptic
selecting downloaded apps just ignores the .deb file
I loaded Gdebi , that finds the .deb file, but it shows correctly that there are two dependent files (fftw3)
clicking on install files and Gdebi crashes

using apt install <my_package>.deb works, but shows errors where I have a line in the postinst file to kill Gdebi, thats to stop the click happy mouse users from reinstalling

dpkg -i <my_package>.deb works , BUT is dpkg installed by default with Lubuntu , or was it installed when I installed Gdebi ????

I used to just supply the binary file and support files as a tar file to be installed in the users home directory.
But I had many users complaining they didn't understand how to use either tar or unzip , and wanted something they could just click on and it installs
Hence the reason for use the debian package manager and provide a .deb file for them to click on.

That works fine in ubuntu and all the distros that use ubuntu libs and on ARM based SBCs  that use ubuntu
the headach is the RaspberryPi, which since raspian buster was introduced has been a nightmare with QT5, which the app I package for a friend
uses and no longer works. I've given up with raspbery pi os,  as the application for Ham radio Use, MSHV, works well on a raspberry PI B both 3 & 4
when using Ubuntu.
I've tried and tested on both the Mate-desktop and lubuntu-desktop
I load MSHV in to /usr/local/sbin  so the user can type MSHV on the CLI from any directory,

I also load MSHV.desktop into /usr/share/applications   so the app appears in the main menu

[Desktop Entry]
Name=MSHV
Exec=/usr/local/sbin/MSHV
Comment=
Terminal=false
Icon=/usr/local/sbin/settings/resources/ms_ico.png
Type=Application
Name[en_GB]=MSHV

Which on both Mate and Lubuntu desktops start the application

Can someone please help with how I can get my .deb file to be recogised by Synaptic and Muon  
 if the user selects "add downloaded packages" from the file menu on either the package can be installed graphically

thanks

---

