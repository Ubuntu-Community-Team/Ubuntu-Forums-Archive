---
title: "DXVK: It worked yesterday"
date: 2024-04-13
forum: General Help
---

### Post by nicolasdentremont on 2024-04-13
Hello everyone. I always wanted to get into using Linux (I have messed around with it many years ago) but never really had the courage to really make the jump from Windows. Last week I decided to give it another go.

My computer specification are:

Laptop Acer Nitro AN515-54
OS: Ubuntu 22.04.4 LTS 64-bit
Memory: 12.0 GiB
Processor: Intel® Core™ i5-9300H CPU @ 2.40GHz × 8
Graphics: NVIDIA Corporation GP107M [GeForce GTX 1050 3 GB Max-Q]
Graphics Driver: Nvidia driver 535

I've been trying to optimize a game called Entropia Universe with Wine 9.0

The game runs fairly well right out of the box just by installing it with Wine with one annoying exception. Every minute or so the screen flashes black randomly like a strobe light. Otherwise the game runs better that it did on Windows.

While reading some forum posts about running this game on Linux, one of the people said that it worked much better after installing DXVK so I tried it myself. I got it from [https://github.com/doitsujin/dxvk](https://github.com/doitsujin/dxvk) and followed the instructions there.

 The game launcher had a message saying that my video card may not be able to run the game but I launched it and it worked fine and that flashing stopped happening.

Anyway I ended up messing up something else on my computer yesterday and reinstalled Ubuntu. Now when I install the .dll files from DXVK it gives me the following errors while trying to launch the game.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293610&stc=1[/IMG]

and then this

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293611&stc=1[/IMG]

Anyway that's where I'm stuck at. I can remove the .dll files and use the command ```
wineboot -u
``` to go back to running the game with that annoying flashing but I can't seem to figure out how to fix it.

As far as I know, I installed Wine, the game and DXVK the same way as before.

Any help would be appreciated.

---

### Post by hyperlinxe on 2024-04-13
Can you add how you are installing(generally) your system, and setting up your graphics drivers, as well as your desktop environment? Also please add, how you are installing the game, and attempting to run it please. Thank you.

---

### Post by nicolasdentremont on 2024-04-13
> **hyperlinxe said:**
> Can you add how you are installing(generally) your system, and setting up your graphics drivers, as well as your desktop environment? Also please add, how you are installing the game, and attempting to run it please. Thank you.

Sure, I installed the OS using the ISO from the Ubuntu website written to a USB flash drive. I just used the regular installer that comes up when you boot it. The desktop environment is Gnome 42.9 installed by default with Ubuntu. The graphics drivers were installed along with the OS using the option to do so during the initial setup.

I installed wine using the instructions on their website, by adding their repository and installing through there rather that the Ubuntu Software application.

From there I just downloaded the regular game installer from the game website and ran it using the wine command. The installer itself runs just like on Windows. Once it's installed, I just run it with the shortcut in my applications list.

---

### Post by hyperlinxe on 2024-04-13
Using wine manually requires some significant effort generally to get many games working, so on linux we use tools like playonlinux, steam (proton), and lutris to help deal with that problem.

Generally you want to search for guides to help you install games correctly. 

Here I just did a quick lookup on lutris.org, and found that someone has already made a script to help install your game, and configure wine to work with it, 

[https://lutris.net/games/entropia-universe/](https://lutris.net/games/entropia-universe/)

So if you had lutris installed, you could click the link on that page, and the script would install the game, and configure wine to work with it, and you could be up and running in the amount of time it takes to install the game.

The website for entropia recommends the use of a virtual machine(a vm) or a dual boot to get it working, and doesn't give instructions for using wine. It's likely that you can find instructions for using/configuring wine, on the internet with your game as well.

To use lutris you have to add 32 bit library support, and install lutris like this...

sudo dpkg --add-architecture i386
sudo apt update
sudo apt install lutris

And actually for ubuntu stable, jammy jellyfish, the lutris in the apt repositories is old right now and wont function properly, so after following the steps above, then you have to grab the latest .deb package for lutris from their github website which is here...

[https://github.com/lutris/lutris/releases](https://github.com/lutris/lutris/releases)

You want to first install lutris from the apt repository after updating apt with 32 bit support, in order to pull in some dependencies for it. 
then after you grab the latest lutris.deb package from the lutris github site you install it like this...from inside the folder it's in.

(the first command installs dependencies of the lutris .deb)
sudo apt install vulkan-tools python3-gi-cairo
sudo dpkg -i lutris.deb

Like I said, using lutris, or steam with proton, is the easy method to play games right now. If you want to do more manual configuration, it's going to take more effort, and for that you can work with the tools built in to lutris or for steam-proton or playonlinux to make life easier as well.

So lutris will have it's own custom wine package, to use with entropia after you install it, but you want to use version 9 of wine, to see how it alters the situation, and you can do that within lutris, but then you will have to configure it in order to work appropriately. (so you can install it via lutris, and then switch to wine 9, configure it, and run the game typically)

Generally just grabbing all the wild dependencies from installing the graphics driver, lutris, steam, and wine, and after intially adding 32 bit library support will make your life easier, because they include a lot of different packages that will help you generally. 

If you can't install the game after installing lutris then you will need to follow the instructions here...

[https://github.com/lutris/docs/blob/master/InstallingDrivers.md](https://github.com/lutris/docs/blob/master/InstallingDrivers.md)

Which if you have your graphics driver installed already are boiled down to this..

sudo apt install libvulkan1 libvulkan1:i386

The last consideration is whether or not you are using wayland as your display server instead of x11, which will give you the worst performance with gaming, and will not work properly without manual configuration of your system. To change display servers log out, and select the other option from the drop down menu in the login screen besides ubuntu wayland...I can't remember what it's called there, might be gnome session, or ubuntu session or something like that.
(whatever you select will then become the default option every time you restart your computer)

editt...also if you want to get it working with just wine itself, again, like I said, that is going to take a lot more effort than using prescribed methods mentioned above. But the easy way is to use the app playonlinux, to help you manage wine, and your game, with a gui. If you found guides for doing so online it would make your life easier...it's kind of difficult to explain every detail about all of this madness briefly on the forum for you...

Also literally searching "how to play *insert game name here* on linux" will help you tremendously

edit#2:Your main problem other than configuring wine, and installing/running the game properly is this...
> The graphics drivers were installed along with the OS
because you installed your drivers initially, but without 32 bit library support included, which is fine, except for using all of these gaming programs I'm talking about. When you want to do gaming with linux the best way, is to install the system normally, without proprietary drivers, using nomodeset on the kernel command line through grub for uefi, and ubuntu wayland systems even, to initially login, then sudo dpkg --add-architecture i386 && sudo apt update ( to add 32 bit library support) then installing your graphics drivers so that you pull in the 32bit libraries with your graphics driver install. You should be able to avoid worrying about it though if you follow the instructions from the lutris page on installing drivers: sudo apt install libvulkan1 libvulkan1:i386
that command might not even work for you though, you can find lots of weird problems trying to get all this stuff to work, if things aren't done in the appropriate order of operations...

---

### Post by nicolasdentremont on 2024-04-13
Thanks a bunch for all that information it's been very helpful! I installed Lutris and ran the script to install the game. That didn't actually work but it may just be because it was made a few years ago and the game has changed since then. So instead I just used Lutris to run the installer.exe for the game and it installed without issue, the game is up and running now and it runs great, way better than on Windows. I've been used to playing through the lag for so long that it actually looks weird to watch the game happen at proper FPS.

I heard Lutris referenced online but didn't really know much about it, I also have Steam and have played a couple games with proton, Maybe I can work on getting some more to work.

Thanks again for your help.

---

### Post by MAFoElffen on 2024-04-14
Have you seen this DXVK Guide?
[https://linuxconfig.org/improve-your-wine-gaming-on-linux-with-dxvk](https://linuxconfig.org/improve-your-wine-gaming-on-linux-with-dxvk)

---

