---
title: "How Do I Load Open Office 4.0?"
date: 2013-07-30
forum: General Help
---

### Post by Smallwheels on 2013-07-30
Open Office 4.0 is now available. It looks great. Libre Office is giving me problems with loading a very large file. I'm accustomed to using Open Office 3 and I like it. So I've decided to give the newest version a try with the hope that it does better than Libre Office. 

At the Open Office site the new version is ready for downloading. I did that. This caused one immediate problem. It downloaded it to my root folder. In a way that seems like no big deal except for some strange reason my Ubuntu 13.04 new installation won't let me access that folder. I am the only user. I have the only password yet it gives me a message saying I'm not the owner and can't get to it. Help me with this first hurdle and then I'll ask the next question I have about installing it. 

Thank you.

---

### Post by GwL3eNC on 2013-07-30
Hi!

Normaly you can download the deb file from Open Office Homepage. Cant you change the download destination? If not,
you can open a terminal window. Type 

sudo su

and give the password.
From now the terminal has root access and you can access any folder.
Go to the download folder using 

cd 

Command. type cd --help for more info.
If you arrive there type

dpkg -i packetname

to install the Open Office deb Package.

---

### Post by marcpare on 2013-07-30
Feel free to leave a note on the LibreOffice mailing list for help with the file[1], or if you want, you can send me the file and I can see if I can help out. We also have the newest version of LibreOffice 4.1.0 that was just released last week and the problem you have with the large file may be gone.

Cheers,

Marc Paré
Marketing team member
[email]marc@marcpare.com[/email]

[1] 
* you can join the users list here: [https://www.libreoffice.org/get-help/mailing-lists/](https://www.libreoffice.org/get-help/mailing-lists/) -- you will want to join the "users" list

* or you can also use the same mailing list with a "forums look" on our Nabble site - [http://nabble.documentfoundation.org/Users-f1639498.html](http://nabble.documentfoundation.org/Users-f1639498.html) (same as the mailing list but the display looks more like that of a forums

---

### Post by Smallwheels on 2013-07-31
The folder that Open Office went to is named EN-US if my memory is right. I wanted to choose where it was to go but when I downloaded it there was no ability for me to choose the location. It just went there. So how do I access the root folder without using the terminal? I'll be happy to use the terminal but I really shouldn't be prevented from accessing that folder in the first place. I can understand if it asked me for my password when clicking on the folder, but just refusing permission and saying I'm not the owner is just some type of bug. 

I don't know the package name so I can't do that with the terminal. I'm too new with Linux to know where to go and what to do. In time the forums will teach me what I need to know. So how can I first access that folder? 

I cannot send the file anywhere because it is confidential. I appreciate the offer marcpare. I will attempt to update Libre Office and see what happens.

---

### Post by GwL3eNC on 2013-07-31
You can try sudo dolphin, or sudo nautilus but therefore you also need the terminal once. If you do that, dolphin has root privilegs, you can
go everywhere and you can evtl. use a right click on the deb file and install it with software center or something like that.

Hope that helps you.

Some other info: If you type ls -l in the terminal you see the current directory. something like that

 drwxr-xr-x 2 fidel fidel 4096 Jul 11 18:29 Arbeitsfläche
drwxr-xr-x 2 fidel fidel 4096 Jul 11 17:54 Bilder
drwxr-xr-x 7 fidel fidel 4096 Jul 24 13:33 Dokumente
drwxr-xr-x 2 fidel fidel 4096 Jul 29 16:11 Downloads


you see the name fidel. The first one means the owner of the file or folder, the second fidel is
the group. It ist possible, that there is something wrong with this in the  EN-US folder or the
given rights on the left (drwxr-xr-x). In the terminal you can use chown and chgrp command
to change that.

for a directory i think sudo chown -r yourusername directorytochange

---

### Post by mastablasta on 2013-07-31
> **Smallwheels said:**
> The folder that Open Office went to is named EN-US if my memory is right. I wanted to choose where it was to go but when I downloaded it there was no ability for me to choose the location. It just went there. So how do I access the root folder without using the terminal? I'll be happy to use the terminal but I really shouldn't be prevented from accessing that folder in the first place. I can understand if it asked me for my password when clicking on the folder, but just refusing permission and saying I'm not the owner is just some type of bug. 

I don't know the package name so I can't do that with the terminal. I'm too new with Linux to know where to go and what to do. In time the forums will teach me what I need to know. So how can I first access that folder? 

.

are you saying that the whole folder is in root? as in the paths is  /EN-US  ? normally downloads go under /home/downloads

you are not the only user btw. there is also a "root user" (aka Admin) on the computer. you can't access it. but then again you dont' need to as you can temporarilly gain super user powers.

otherwise you need to open your file manager with root privileges. if there is no launcher/shortcut for that then the faster way to do it is to run ```
gksu nautilus 
```in gnome (ubuntu) or ```
kdesudo dolphin 
```in KDE (kubuntu). you will need to enter your password and after that you are root. temporarilly. so be careful. you can then move the folder with .deb file to your home and right clicking it should give you properties options. you can then set permissions to it. for exmaple that your user can access and run the file.

kdesudo and gksu give temporary root privileges to graphical/non terminal based applications.

---

### Post by speartip on 2013-08-01
Hi smallwheels,

This is how I installed OO4.
1st install a program called nautilus-open-terminal, it will be useful.
```
sudo apt-get-install nautilus-open-terminal
```
Logout & back in again.
Then download OO4 from here, use Firefox & make sure downloads are set to download to your Desktop 1st.
[http://www.openoffice.org/download/other.html#aoo](http://www.openoffice.org/download/other.html#aoo)
Pick the one correct for your architecture of course (either the INTEL deb for 32bit or the x86-64 deb for 64bit)
Then go to your desktop to the downloaded file, Right Click & Extract Here.
You should then have a Folder en-GB (or whatever your language).
 Enter the folder, the enter the DEBS folder. Click file & open in terminal. in the terminal type:
```
sudo dpkg -i *.deb
``` & enter password.
All the DEBS should now install.
 When finished, go back into the DEBS folder & enter the desktop-integration folder. Click file & open in terminal again.
Type the above command again.
Thats it, log out & back in, you should now have a working copy of openoffice.

---

### Post by gordintoronto on 2013-08-01
Did you use Firefox to download the package? There is a setting in Firefox to specify where downloads should go. Edit/Preferences, and it's right on the first tab.

---

