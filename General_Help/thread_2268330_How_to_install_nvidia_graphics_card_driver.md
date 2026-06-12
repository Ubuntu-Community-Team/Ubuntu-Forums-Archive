---
title: "How to install nvidia graphics card driver"
date: 2015-03-07
forum: General Help
---

### Post by newbie14 on 2015-03-07
My Ubuntu computer's specification:
Does not have any internet connection.
Graphics card type: NVIDIA GeForce GT 520 2 GB
I have done these steps but it failed:
1. I downloaded "NVIDIA-Linux-x86-346.47.run" file from [[http://www.nvidia.com/content/DriverDownload-March2009/confirmation.php?url=/XFree86/Linux-x86/346.47/NVIDIA-Linux-x86-346.47.run&lang=us&type=GeForce]](http://www.nvidia.com/content/DriverDownload-March2009/confirmation.php?url=/XFree86/Linux-x86/346.47/NVIDIA-Linux-x86-346.47.run&lang=us&type=GeForce]). I downloaded it from a computer rental 10 kilometers away from my home.
2. I copied the [NVIDIA-Linux-x86-346.47.run] file to my USB Flashdisk. And I went home.
3. I turned my ubuntu computer on.
4. I plugged in my USB Flashdisk to my ubuntu computer.
5. I copied the [NVIDIA-Linux-x86-346.47.run] file from my USB flashdisk.
6. I pasted the [NVIDIA-Linux-x86-346.47.run] file to my [downloads] folder in my ubuntu computer.
7. I highlited / select the [NVIDIA-Linux-x86-346.47.run] file in the [downloads] folder like this
[http://i.imgur.com/Kb7L4yI.png](http://i.imgur.com/Kb7L4yI.png)
8. I pressed the [enter] button on my keyboard.
9. A text editor appears and inside it there is a progress bar running.
10. After 35 minutes, the progress bar completes and a warning appears and said [there was a problem opening the file /home/yggdrasil/download...lDlA-Linux-x86-346.47.run. The file you opened has some invalid characters. If you continue editing this file you could corrupt this document. You can also choose another encoding and try again.]. It appears like this.
[http://i.imgur.com/08jEa5R.png](http://i.imgur.com/08jEa5R.png)
11. At this point. I think the installation failed. There are 4 options: a: choose character encoding. b: retry. c: edit anyway d: cancel.
12. I clicked the [cancel] option.

My question are: 
1. Is there some thing or some step i missed?
2. Is the [NVIDIA-Linux-x86-346.47.run] file broken?
3. What should I do to Instal my graphics card to my ubuntu computer?

---

### Post by carl4926 on 2015-03-08
Take it to an internet connection
Update it first and reboot it

Then open a terminal and do

```
sudo apt-get install nvidia-current
```

---

### Post by newbie14 on 2015-03-08
It is impossible to connect my ubuntu computer to the internet. My ubuntu computer is in my home located in a very remote area.
The nearest internet connection available is 10 kilometers away from my ubuntu computer, the computer internet rental. While I am now at the rental;
what installer should i download and copy to my USB flashdisk and what is the u.r.l for the offline installer?
Is there any possible way for an ubuntu computer to install graphics driver without internet connection?

---

### Post by carl4926 on 2015-03-08
Problem is there are build requires that are needed to run the nvidia blob
I'm pretty sure they are not there by default

Can we see the output from a terminal for the following:

```
lspci -nnk
```

From that we can establish exactly what hardware you have.
Most computers will run pretty well now with the nouveau driver, which is what your system is likely using now.
Unless you have a hybrid setup. Which we will see when you post the requested info

---

### Post by newbie14 on 2015-03-08
I have typed the:
lspci -nnk
code in the terminal. and the terminal displays this:

yggdrasil@Fulani:~$ lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation 2nd Generation Core Processor Family DRAM Controller [8086:0100] (rev 09)
00:01.0 PCI bridge [0604]: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port [8086:0101] (rev 09)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:16.0 Communication controller [0780]: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 [8086:1c3a] (rev 04)
	Subsystem: Giga-byte Technology Device [1458:1c3a]
	Kernel driver in use: mei
	Kernel modules: mei
00:1a.0 USB controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 [8086:1c2d] (rev 05)
	Subsystem: Giga-byte Technology Device [1458:5006]
	Kernel driver in use: ehci_hcd
00:1b.0 Audio device [0403]: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller [8086:1c20] (rev 05)
	Subsystem: Giga-byte Technology Device [1458:a002]
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 [8086:1c10] (rev b5)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.4 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 [8086:1c18] (rev b5)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1d.0 USB controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 [8086:1c26] (rev 05)
	Subsystem: Giga-byte Technology Device [1458:5006]
	Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev a5)
00:1f.0 ISA bridge [0601]: Intel Corporation H61 Express Chipset Family LPC Controller [8086:1c5c] (rev 05)
	Subsystem: Giga-byte Technology Device [1458:5001]
	Kernel driver in use: lpc_ich
	Kernel modules: lpc_ich
00:1f.2 IDE interface [0101]: Intel Corporation 6 Series/C200 Series Chipset Family 4 port SATA IDE Controller [8086:1c00] (rev 05)
	Subsystem: Giga-byte Technology Device [1458:b002]
	Kernel driver in use: ata_piix
00:1f.3 SMBus [0c05]: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller [8086:1c22] (rev 05)
	Subsystem: Giga-byte Technology Device [1458:5001]
	Kernel modules: i2c-i801
00:1f.5 IDE interface [0101]: Intel Corporation 6 Series/C200 Series Chipset Family 2 port SATA IDE Controller [8086:1c08] (rev 05)
	Subsystem: Giga-byte Technology Device [1458:b002]
	Kernel driver in use: ata_piix
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF119 [GeForce GT 520] [10de:1040] (rev a1)
	Kernel driver in use: nouveau
	Kernel modules: nouveau, nvidiafb
01:00.1 Audio device [0403]: NVIDIA Corporation GF119 HDMI Audio Controller [10de:0e08] (rev a1)
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
	Subsystem: Giga-byte Technology GA-EP45-DS5/GA-EG45M-DS2H Motherboard [1458:e000]
	Kernel driver in use: r8169
	Kernel modules: r8169
yggdrasil@Fulani:~$

My setup is:
A motherboard with processor, the motherboard connected to a graphics card. And the motherboard connected to a USB flashdisk 32GB. And the motherboard has 1 more working USB Slot.
The 32 GB USB flashdisk is where the ubuntu installed. And the motherboard boots the ubuntu from this 32 GB USB Flashdisk.
The Graphics Card is connected to the monitor.
The remaining 1 USB slot is the only the ubuntu computer's way of obtaining an offline installer or programs from my 16 GB USB Flashdisk.

---

### Post by dino99 on 2015-03-08
i think you will need to be connected to the net to repair/reinstall the needed driver.
Before doing some more task, purge the actual driver: sudo apt-get purge nvidia*
The easiest way is to first: install synaptic, then install nvidia-346 (from synaptic) ; or if you still have some issue with nvidia, you then can install 'nouveau' instead.

---

### Post by oldfred on 2015-03-08
You may want to look into apt-offline. Link is older, but apt-off line is still in repository. 

       Apt-offline in repository for offline updates
[http://www.debian-administration.org/article/648/Offline_Package_Management_for_APT](http://www.debian-administration.org/article/648/Offline_Package_Management_for_APT)

> apt-offline can fully update and upgrade an APT based distribution without
connecting to the network, all of it transparent to apt


---

### Post by carl4926 on 2015-03-12
As stated in post #2
Get access to the internet and update and then run the command given

---

### Post by newbie14 on 2015-03-13
> **carl4926 said:**
> As stated in post #2
Get access to the internet and update and then run the command given

It is impossible to connect my ubuntu computer to the internet. Getting My ubuntu computer any access to internet is also impossible.
Is there any possible way for an ubuntu computer to install graphics card driver without internet connection?
Or it is impossible for an ubuntu computer to install graphics crad driver without internet connection?

> **9d9 said:**
> i think you will need to be connected to the net to repair/reinstall the needed driver.
Before doing some more task, purge the actual driver: sudo apt-get purge nvidia*
The easiest way is to first: install synaptic, then install nvidia-346 (from synaptic) ; or if you still have some issue with nvidia, you then can install 'nouveau' instead.


It is impossible to connect my ubuntu computer to the internet. Myubuntu computer is in my home located in a very remote area. Thenearest internet connection available is 10 kilometers away from myubuntu computer, the computer internet rental.

however, I have had typed in the

```
sudo apt-get purge nvidia*

```

code in the terminal replies with:

```
yggdrasil@Fulani:~$ sudo apt-get purge nvidia* 
[sudo] password for yggdrasil: 
Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
Note, selecting 'nvidia-common' for regex 'nvidia*' 
Note, selecting 'libgl1-nvidia-alternatives' for regex 'nvidia*' 
Package 'libgl1-nvidia-alternatives' is not installed, so not removed
Note, selecting 'ubuntu-drivers-common' instead of 'nvidia-common' 
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 
yggdrasil@Fulani:~$

```

at the sixth line, it was written:
```
Package 'libgl1-nvidia-alternatives' is not installed, so not removed
```
So I think, my very first installation attempt in installing the nvidia graphics card driver is a complete, utter failure.

This ubuntu computer relies heavily on internet connection to install a program.
So I might as well try to instal [COLOR=#000000][FONT=Ubuntubeta]installsynaptic,[/FONT][/COLOR] [COLOR=#000000][FONT=Ubuntubeta]theninstall nvidia-346 (from synaptic)[/FONT][/COLOR], then [COLOR=#000000][FONT=Ubuntubeta]install'nouveau'. But I don't know how to do any of this.
But I am willing to learn.
I guess I must start 3 new general help or question threads titled:
1. How to install synaptic on an ubuntu computer without any internet connection.
2. How to install nvidia-346 using synaptic on an ubuntu computer without any internet connection.
3. How to install 'noveau' on an ubuntu computer without any internet connection.

wish me luck.
[/FONT][/COLOR]

---

### Post by oldfred on 2015-03-13
Did you see post #7?

---

### Post by newbie14 on 2015-03-13
```
[SIZE=3]**[FONT=franklin gothic medium][COLOR=#000000]I guess I must start 3 new general help or question threads titled:[/COLOR][/FONT]**[/SIZE]
```

not 3, but 4. the fourth is:

 How to check whether or not my ubuntu computer has already hadsynaptics installed?

> **oldfred said:**
> Did you see post #7?

Yes, I am currently surfing the "Offline Package Manger for APT" web page.
1. There are 6 main hyperlink at the top of the page, they are: "about", "archive", "contribute", "FAQ", "search", and "tags".
2. I am single-left-clicking the "archive" hyperlink.
3. There are hyperlinks for every archive from year 2004 to year 2015.
4. I am trying to use the "nvidia" keyword to search for something, using my internet browser's search feature.
5. I am starting to search from the "2004" hyperlink/page.

I do not know how to do any of this, but I am willing to learn.
wish me luck.

> **oldfred said:**
> Did you see post #7?

I found 6 hyperlinks inside the "Offline Package Manager for APT" website containing the keyword "nvidia" and tagged "nvidia". they are:

first hyperlink: [http://www.debian-administration.org/article/11/How_do_I_setup_Nvidia_Drivers_under_Debian](http://www.debian-administration.org/article/11/How_do_I_setup_Nvidia_Drivers_under_Debian)

second hyperlink:   [http://www.debian-administration.org/article/493/Using_the_nvidia_binary_driver_with_Xen_on_Debian_etch](http://www.debian-administration.org/article/493/Using_the_nvidia_binary_driver_with_Xen_on_Debian_etch)

third hyperlink:  [http://www.debian-administration.org/article/645/Getting_emacs23_for_Lenny](http://www.debian-administration.org/article/645/Getting_emacs23_for_Lenny)

fourth hyperlink:  [http://www.debian-administration.org/users/ajt/weblog/28](http://www.debian-administration.org/users/ajt/weblog/28)

fifth hyperlink:  [http://www.debian-administration.org/users/eric/weblog/14](http://www.debian-administration.org/users/eric/weblog/14)


sixth hyperlink: [http://www.debian-administration.org/users/ericrox/weblog/2](http://www.debian-administration.org/users/ericrox/weblog/2)

I will try to find any clue starting from the first hyperlink.

wish me luck.

my forum signature, please ignore:_______________________________________________________
I think I am starting to get lost and drifted far away from my main objective.
day 5 and still not a single clue how to install an offline driver.
Now I know why linux or ubuntu is very very uncommon among people.
without internet connection, linux or ubuntu is very difficult for an application to be installed upon.
But I am willing to learn.
I am willing go through everything to master the techniques of installing programs in linux or ubuntu without internet connection.
every mouse click, every keyboard tuts press. every single step.
Is there any possible way for an ubuntu computer to install graphics card driver without internet connection?
Or it is impossible for an ubuntu computer to install graphics crad driver without internet connection?
my stamina is decreasing, my will is depleting.
But I am willing to learn.

First hyperlink contains another hyperlink:

[http://home.comcast.net/~andrex/Debian-nVidia/](http://home.comcast.net/~andrex/Debian-nVidia/)

this hyperlink is a broken hyperlink.
I will try to find another clue at the second hyperlink.

[COLOR=#000000]my forum signature, please ignore:___________________________________________ ____________[/COLOR]
[COLOR=#000000]I think I am starting to get lost and drifted far away from my main objective.[/COLOR]
[COLOR=#000000]day 5 and still not a single clue how to install an offline driver.[/COLOR]
[COLOR=#000000]Now I know why linux or ubuntu is very very uncommon among people.[/COLOR]
[COLOR=#000000]without internet connection, linux or ubuntu is very difficult for an application to be installed upon.[/COLOR]
[COLOR=#000000]But I am willing to learn.[/COLOR]
[COLOR=#000000]I am willing go through everything to master the techniques of installing programs in linux or ubuntu without internet connection.[/COLOR]
[COLOR=#000000]every mouse click, every keyboard tuts press. every single step.[/COLOR]
[COLOR=#000000]Is there any possible way for an ubuntu computer to install graphics card driver without internet connection?[/COLOR]
[COLOR=#000000]Or it is impossible for an ubuntu computer to install graphics crad driver without internet connection?[/COLOR]
[COLOR=#000000]my stamina is decreasing, my will is depleting. Oh the pain. Oh the suffering.[/COLOR]
[COLOR=#000000]But I am willing to learn.[/COLOR]

---

### Post by oldfred on 2015-03-13
I was referring in Post #7 to the off-line apt. You probably have to download it and copy it into your computer that has no Internet. Then run it to create the list of things that need updating or installing. Then take that on a flash drive to a computer with Internet and update. Then return those files to the off-line computer & update.

Trying to download an app without Internet gets you back to the old days where you may have dependencies that then also need updating. 

This is a newer thread:
[https://cortman.wordpress.com/2012/07/08/download-packages-with-windows/](https://cortman.wordpress.com/2012/07/08/download-packages-with-windows/)
But newer versions of Ubuntu do not have synaptic as standard, it has to be downloaded. Ubuntu switch from synaptic as default to Software Center, so they could also sell software.

 [https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository)
[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)
[https://help.ubuntu.com/community/LocalAptGetRepository](https://help.ubuntu.com/community/LocalAptGetRepository)

---

### Post by newbie14 on 2015-03-14
I have tried the first hyperlink;

I typed the u.r.l addres of

[https://cortman.wordpress.com/2012/07/08/download-packages-with-windows/](https://cortman.wordpress.com/2012/07/08/download-packages-with-windows/)

in the address bar in the internet browser program at the internet rental computer.

the web page in that address suggest me to install download and install "wassail" so I did these steps:

At the online windows computer:
1. I clicked the hyperlink containing the addres to a source forge website.
2. In the source forge website, I left clicked the green download with a text "Download wassail.zip" button.
3. The website page shows a countdown timer for 5 seconds so I waited.
4. After the countdown reaches zero, a dialog box appeared.
5. In the dialog box, in the directory tree, I selected the path to my usb flash disk.
6. In the dialog box, I clicked "OK"
7. I opened windows explorer.
8. I clicked the icon of my usb flash disk on the directory tree path sidebar of the windows explorer.
9. A 16 kilobyte .zip file with the name "Wassail" appeared.
10. I double clicked the Wassail.zip file.
11. A 7zip window appeared.
12. There is one .exe file inside the 7zip window, the name of the file is "wassail.exe".
13. I pointed my mouse cursor on the Wassail.exe
14. I left clicked the Wassail.exe file and keep pressing the left mouse button.
15. I dragged my mouse cursor to my USB flash disk directory.
16. I released the left mouse button.
17. an .exe file named "Wassail" appeared on my USB flash disk directory.
18. I left clicked the Wassail.exe file once, essentially highlighting the wassail.exe file.
19. I pressed "enter" button on the keyboard.
20. A Wassail window appeared.
21. I left clicked the "Select Dowload Script"
22. A dialog box appeared.
23. I do not have the script file required yet, I clicked cancel.
24. I re-read the [https://cortman.wordpress.com/2012/07/08/download-packages-with-windows/](https://cortman.wordpress.com/2012/07/08/download-packages-with-windows/) web page.
25. There is an instruction that said: "On offline Ubuntu machine: Open a terminal with Control+Alt+t and type "synaptic".
26. I went home to my offline ubuntu computer.
27. I pressed the Ctrl, alt and T on the keyboard of my offline ubuntu computer.
28. A terminal window appeared.
29. I typed 
```
synaptic
```
inside the terminal.
30. The terminal replied with this:
```
The program 'synaptic' is currently not installed. You can install it by typing: 
sudo apt-get install synaptic 
yggdrasil@Fulani:~$

```
31. It appears that my ubuntu computer does not have the "synaptic" program yet. Because the next instruction contradicts with the result I got from typing the "synaptic" code.
32. It appears that according to Mister Cortman's guide, I have to install "synaptic" on my ubuntu computer first.
34. I went back to the windows internet computer rental 10 kilometers away from my ubuntu computer.
35. I posted a new question thread on this ubuntu forum, under the "Installation & Upgrades" topic.
This is the hyperlink of the thread requesting help, guidance, assistance of how to install synaptic on an offline ubuntu computer.
[http://ubuntuforums.org/showthread.php?t=2269294&p=13245719&highlight=#post13245719](http://ubuntuforums.org/showthread.php?t=2269294&p=13245719&highlight=#post13245719)

36. While I wait for any clues or answer from the [http://ubuntuforums.org/showthread.php?t=2269294&p=13245719&highlight=#post13245719](http://ubuntuforums.org/showthread.php?t=2269294&p=13245719&highlight=#post13245719) thread, I am trying to seek / search some more information on how to install nvidia graphics driver on an offline ubuntu computer at the second u.r.l hyperlink you have provided:

[https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository)

wish me luck.

---

### Post by oldfred on 2015-03-15
Is the computer you are connecting to Internet Windows only or have you set it up as dual boot with Ubuntu. Much easier if you can download with Ubuntu on that computer.
Are you running 32 bit or 64 bit?


   But why do you really want nVidia driver. The default open source driver now is good enough for most uses with your nVidia card. I have a slightly newer GT620 and have been somewhat surprised how well the open source driver works with it. I have normally installed nVidia drivers.

   When I look on nVidia's site it says you now have a legacy driver. Your originally downloaded the 64 bit current driver which is only for newer nVidia cards.
nVidia says your driver is the 340.xx series which is now a legacy driver. 
This is the 64 bit version:
[http://www.nvidia.com/Download/driverResults.aspx/81761/en-us](http://www.nvidia.com/Download/driverResults.aspx/81761/en-us)

   Ubuntu repository's do not usually have to most current version, depending on which version of Ubuntu it may download a 331.xx or similar version.

Are you going to want to install other software from Ubuntu repository. Is so we need to get an offline method working. The synaptic file list is a wget bash command. But you can manually create those commands.

[http://askubuntu.com/questions/168352/how-do-i-generate-a-package-download-list](http://askubuntu.com/questions/168352/how-do-i-generate-a-package-download-list)

---

### Post by Kenneth_Benson on 2015-03-30
Newbie14, another thing you can do is do a google search for "Ubuntu repository dvd". There are at least a couple places that sell the entire repository on about 15 dvd disks. Not sure how much it would be.

---

### Post by kirby2ig on 2015-03-30
Let's see if I can remember how to do this correctly.

Note: probably a good idea to write these steps down or view them on another device as we will be closing the desktop.

First, you will need to get to the console. Press Ctrl+Alt+F1 on your keyboard and log in with your username and password.
Next, run the command "sudo service lightdm stop" to close the desktop.
After that, navigate to the location where the file is stored using the cd command.
Once there, run chmod +x NVIDIA-Linux-x86-346.47.run
Then run sudo ./NVIDIA-Linux-x86-346.47.run
After that is finished, reboot the computer with the command sudo reboot.

Hopefully, the driver should be installed after this.

---

### Post by newbie14 on 2015-04-06
Thanks a lot man, this is exactly what I need; A direct, simple, technical instruction. I have done the steps You instructed, but installation failed. But even when it was failed, now I know how to install a .run file without internet connection in ubuntu linux. Most importantly, Your instruction made me know how to open the terminal program using keyboard shortcut, and what command to type in the terminal. What I must do now is to find the correct .run file in the internet. Thank You [COLOR=#000000]kirby2ig.[/COLOR]

---

