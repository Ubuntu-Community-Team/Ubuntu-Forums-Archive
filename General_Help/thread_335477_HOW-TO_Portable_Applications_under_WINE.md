---
title: "HOW-TO: Portable Applications under WINE"
date: 2007-01-10
forum: General Help
---

### Post by MoebusNet on 2007-01-10
This is an unsupported How-To because I'm just a newby. I don't know enough about linux to offer any fixes, I just wanted to make the community aware of Portable Applications that run from a USB flash drive under Ubuntu. Please feel free to offer constructive critiques, corrections or to post better ways to do this entirely under linux. I used windows xp to make this work first, then found it worked under WINE.

WINDOWS
On a windows xp machine go to [http://Portableapps.com](http://Portableapps.com) and download the Portable Applications Suite Base Edition to your hard drive. Install the Base edition to your USB flash drive (about 1MB.) Depending on the size of your flash drive, download your desired portable applications that you want to your hard drive so that you can use the Base Edition Portable Apps menu to install them to your flash drive. The list of available apps is on the web site but goes from Open Office to Suduko. Once you have everything installed and running from your flash drive under windows, it is time to try Ubuntu.

UBUNTU
If you haven't already, install WINE. You will need to find a good how-to; it has been long enough that I've forgotten where I found the one I used. You will probably need to enable universe and multiverse repositories if you haven't already done so.

Once WINE runs on your machine, plug in your USB flash drive. Open a terminal window and at the prompt type in "wine /media/FLASHDRIVENAME/StartPortableApps.exe" where FLASHDRIVENAME is what you have named your flash drive (oddly enough.)

The Portable Apps menu should appear on your desktop and should display any Portable Apps you have installed. Just click on the one you want and it should start. Once you close the application, to select another click on the Portable Apps Menu icon on the lower right of the desktop on the task bar to display the menu again.

IMPORTANT NOTE - BEFORE YOU UNPLUG THE USB FLASH DRIVE
Close the Portable Application(s) you were using. Click on the Portable Apps menu icon to open the menu. Click the "X" button at the bottom of the menu to close the Portable Apps Menu, otherwise it is just minimized. If you don't, you can corrupt the Portable Applications Menu.

NOTES
I am currently running Portable Firefox 2.0 under WINE 0.9.28~winehq0~ubuntu~6.10-1 on Kubuntu. I have not tried any of the other Portable Apps under WINE yet. I have not yet attempted a linux-only download and install. I hope that some of you will write a HOW-TO that describes that.

---

