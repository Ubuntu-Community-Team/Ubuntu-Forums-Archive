---
title: "How to create desktop launcher"
date: 2016-01-03
forum: General Help
---

### Post by Otto-C on 2016-01-03
Lubuntu 14.04 fully up to date.

Have installed Wine and it runs great.

How to create a desktop launcher?

tia
otto-c

---

### Post by Dennis N on 2016-01-03
Find the application in the Lubuntu Main Menu. Right-click on the menu entry and select "add to Desktop". Done.

---

### Post by Otto-C on 2016-01-03
Nothing to do with Wine appears in the Lubuntu Main Menu. 
The command I wish to execute from a launcher is $ wine program.exe.
tia
otto-c

---

### Post by brian-mccumber on 2016-01-03
Usually when you install a program or game using Wine it creates a .desktop file to launch the program on your desktop. But if you need to create your own here is a sample of a desktop file that launches Fallout 3 on my computer that was made when I installed it using Wine. The only way I found to edit .desktop files is to drag and drop them into an open gedit window. You can take an existing .desktop file and modify it and save it as another .desktop file which I have done on numerous occasions for scripts that I wrote or games that I installed manually. Don't forget to save them as soAndso.desktop and then in their properties you want to make sure the Allow executing as a program checkbox is ticked in the permissions tab.

```

[Desktop Entry]
Name=Fallout 3
Exec=env WINEPREFIX="/home/brian/.wine" wine C:\\\\windows\\\\command\\\\start.exe /Unix /home/brian/.wine/dosdevices/c:/users/Public/Start\\ Menu/Programs/Bethesda\\ Softworks/Fallout\\ 3/Fallout\\ 3.lnk
Type=Application
StartupNotify=true
Path=/home/brian/.wine/dosdevices/c:/Program Files/Bethesda Softworks/Fallout 3
Icon=0E92_FalloutLauncher.0

```

Alot of apps that are installed create a .desktop launcher but do not place them on the desktop. Since this is Wine the desktop launcher will need a different exec line sorta like the example I posted. If you install a Linux program and no launcher appears on the desktop but you can search the program in dash and find it, you can most likely find the launcher in /usr/share/applications but this is not for Wine programs. I have always made a copy of them from there then pasted to my desired folder but after you paste the copy of the launcher you wanted to use you have to right click, select properties, then the permissions tab, and check the allow executing as a program checkbox. Wine should make it's own launchers and put them on the desktop after you install the game sorta like a program putting a shortcut on the desktop in Windows as it's being installed.  I got tired of opening the dash and searching for a program to run it so I hunted around till I found where the launchers were. Then I wanted to edit the icon for them or make my own program launchers so on a hunch I drug one from the file browser and dropped it into an open gedit window and there was the code for it.

---

### Post by brian-mccumber on 2016-01-03
A faster way to run Win programs in Wine if you don't want to create a custom launcher for them is goto your /home drive or the first directory that appears when you click Files from the launcher, show hidden files, then goto the .wine directory then drive_c dir then Program Files dir and locate the directory your program is installed in. You can then right click the exe for your program or game and choose open with wine windows program loader.

Personally I like the .desktop procedure, you only have to make it once if it is not automatically made for you, then you can put it in a folder and/or pin it to your launcher if you want.

---

### Post by Dennis N on 2016-01-04
> **Otto-C said:**
> Nothing to do with Wine appears in the Lubuntu Main Menu. 
The command I wish to execute from a launcher is $ wine program.exe.
tia
otto-c
Credits to Brian for his explanation - his methods will work. But I wanted to look further into Wine with Lubuntu.

I didn't have Wine installed in my Lubuntu 14.04 - I do have Wine installed on Xubuntu and there it provides a Wine category in it's menu, so I decided to install Wine in Lubuntu to explore ways to deal with this. I like my programs to appear in the main menu!

I used the version in the repository. But after the installation and rebooting, I see there is indeed a Wine category in Lubuntu 14.04. I attach a screen shot. Do you not have this? 

Once I have a main menu entry for the program I want to launch, the simple step in post #2 will give me the desktop launcher. 

Next step would be to install a Windows program under Wine and see if it generates an entry for that. I hope to do that in some break time later.

---

### Post by Dennis N on 2016-01-04
> Next step would be to install a Windows program under Wine and see if it generates an entry for that.

I have installed a Windows program, Across Lite, and found that Wine, running the program's Windows installer, created an entry in the Lubuntu menu under the Wine category (see screen shot). Right-click on that entry offers to "add to Desktop", and that works too. I have only a few programs running under Wine, but those that I do have all created menu entries. 

I haven't seen it happen with Wine, but there are times you won't get a menu entry automatically. DosBox games are an example. In those situations, you can create .desktop files as described by Brian, or you can use a menu editor to manually create a Lubuntu menu entry. Lubuntu 14.04 doesn't include a menu editor by default, but menulibre can be installed and used.

Even with no Windows programs installed, you should still see the Wine category in the Lubuntu menu after installing the Wine package from the repositories. If not, then you may have installed Wine from outside the Ubuntu repositories, and whatever way it was done did not create a menu entry.

---

### Post by Otto-C on 2016-01-05
Using fully updated Lubuntu 14.04.
I installed Wine from directions on winehq site, see below.

sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update
sudo apt-get install --install-recommends winehq-devel

wine --version
wine-1.8
No entry made to start menu. Will try to work way through the helpful information provided.
Thanks

---

