---
title: "Installing Electrum Wallet"
date: 2020-09-01
forum: General Help
---

### Post by rbscairns on 2020-09-01
I recently replaced my 12yo PC (32 bit 1GB RAM, Lubuntu 18.04) with a new 64 bit PC with 8GB RAM. It came with Windows 10 per-installed and, after a bit of learning, I was able to replace Windows 10 with Lubuntu 20.04. Now I am trying to install the Electrum BTC wallet 4.0.2 on my new PC. I have downloaded both electrum-4.0.2-x86_64.AppImage and Electrum-4.0.2.tar.gz and verified their signatures.

I have extracted all the files in the .tar.gz file into ~/Downloads/Electrum-4.0.2. The Appimage file was also saved in ~/Downloads and I have:
```
cd ~/Downsloads
chmod +x electrum-4.0.2-x86_64.AppImage
./electrum-4.0.2-x86_64.AppImage
```
This got the electrum wallet running.

What I would like is to have an icon on my desktop so that all I have to do is double click the icon to open the electrum wallet. It would also be nice to have Electrum Wallet included in my Application Menu. How do I go about this?

---

### Post by rbscairns on 2020-10-10
OK, I am starting again. For various reasons not related to Electrum Wallet, I had to reinstall Lubuntu 20.04. I am now trying to install Electrum Wallet again. Here is what I have done:

First I installed the necessary python tools required to build the program and install it through the built-in Python package installer.
```
sudo apt install python3-setuptools python3-pyqt5 python3-pip
```
I then used the Python 3 Pip tool to install Electrum 4.0.3.
```
sudo pip3 install https://download.electrum.org/4.0.3/Electrum-4.0.3.tar.gz
```
The /usr/local/bin directory contains the file "electrum". I then used the Touch command to make a new, blank electrum shortcut file on the desktop.
```
touch ~/Desktop/electrum.desktop
```
I then opened up the new file to add code to allow Electrum to run directly from the shortcut icon.
```
nano ~/Desktop/electrum.desktop
```
and inserted and saved the following into that code.
```
[Desktop Entry]

Name=Electrum

Comment=Lightweight Bitcoin Wallet.

GenericName=Bitcoin Wallet.

Exec=/usr/local/bin/electrum

Icon=/opt/electrum/electrum-icon.png

Type=Application
```
The wget tool was then used to download a new icon for Electrum.
```
cd /opt/
sudo mkdir -p electrum
cd electrum
sudo wget http://icons.iconarchive.com/icons/alecive/flatwoken/256/Apps-Electrum-icon.png
sudo mv Apps-Electrum-icon.png electrum-icon.png
```
What I thought would be the final step was to update the shortcut's permissions and including the shortcut in my app-menu.
```
chmod +x ~/Desktop/electrum.desktop
sudo cp ~/Desktop/electrum.desktop /usr/share/applications/
```

Now the problems that I need help with:

[LIST]
[*]The icon image (electrum-icon.png) does not appear on the desktop. The .png file is in /opt/electrum and can be opened to show the image.
[*]I have marked the image-less desktop "Trust this exe4cutable". When I click on the icon nothing happens.
[*]The shortcut also appears in my app-menu (with the electrum-icon.png image) but when I click on it again nothing happens.
[/LIST]
Any guidance on where I went wrong would be appreciated.

---

### Post by ajgreeny on 2020-10-10
The Exec= line in your desktop file needs to point to the executable appimage file, wherever that is. The .desktop file can sit on the desktop, assuming that is possible in Lubuntu with the  Lxqt DE, which I have hardly looked at.
You can use any icon you like for the launcher on the desktop by simply pointing to it in the desktop file, using its full pathway.

I have no appimages on my system at the moment but when I have in the past it was very easy to add to the menu system in Xubuntu by placing the desktop file in ~/home/username/.local/share/applications folder.
I don't use launchers on the desktop of my system but I do not see why this should be too difficult to do.

---

### Post by T6&amp;sfpER35% on 2020-10-10
not sure if this would help for lubuntu,i'm on xubuntu and have a few appimages saved in downloads folder.(/home/o14/Downloads/AppImages)
if i want to have an icon on desktop for it ,i would right click on the appimage and choose **send to desktop(create link)**

---

### Post by rbscairns on 2020-10-10
> **ajgreeny said:**
> The Exec= line in your desktop file needs to point to the executable appimage file, wherever that is. The .desktop file can sit on the desktop, assuming that is possible in Lubuntu with the  Lxqt DE, which I have hardly looked at.
You can use any icon you like for the launcher on the desktop by simply pointing to it in the desktop file, using its full pathway.

I have no appimages on my system at the moment but when I have in the past it was very easy to add to the menu system in Xubuntu by placing the desktop file in ~/home/username/.local/applications folder.
I don't use launchers on the desktop of my system but I do not see why this should be too difficult to do.

Following your asdvice as best as I can, I downloaded electrum-4.0.3-x86_64.AppImage and copied it to /home/richard/. I then edited /home/richard/Desktop/electrum (although it is called electrum.desktop in the file editor) to read:
```
Name=Electrum

Comment=Lightweight Bitcoin Wallet.

GenericName=Bitcoin Wallet.

Exec=/home/richard/electrum-4.0.3-x86_64.AppImage

Icon=/opt/electrum/electrum-icon.png

Type=Application
```

The Exec= now points to where the electrum-4.0.3-x86_64.AppImage file is.

The Icon= is already pointing to the .png image file that I would like to use.

With that done, all problems persist. When I double click on the still image-less desktop icon I get the error message "Invalid desktop entry file: '/home/richard/Desktop/electrum.desktop'". The file in /home/richard/Desktop/ is named "electrum" not "electrum.desktop". I don't understand what is happening here.

---

### Post by ajgreeny on 2020-10-10
I can not see why it is not working, assuming the electrum.desktop file on your Desktop is executable or has had the "Trust" enabled as you did before. What happens if you double click on the appimage itself in the file-manager?  That should open up the application; if it doesn't do so then maybe the appimage is not excutable or is corrupt in some way.

I do not know enough about Kubuntu 12.04 nor about Lxqt to be sure that  they are both capable of using desktop launchers, so I will leave this to others who may know more.

---

### Post by rbscairns on 2020-10-10
> **ajgreeny said:**
> I can not see why it is not working, assuming the electrum.desktop file on your Desktop is executable or has had the "Trust" enabled as you did before. What happens if you double click on the appimage itself in the file-manager?  That should open up the application; if it doesn't do so then maybe the appimage is not excutable or is corrupt in some way.

I do not know enough about Kubuntu 12.04 nor about Lxqt to be sure that  they are both capable of using desktop launchers, so I will leave this to others who may know more.
You were right. I had to make electrum-4.0.3-x86_64.AppImage executable. Now the image-less desktop icon for Electum works.

Next is to get the app-menu entry working and getting the .png image to display in the desktop icon.

---

### Post by ajgreeny on 2020-10-10
No idea why the .png image is not working for your launcher icon, assuming it also is not faulty or corrupt in some way; can you open it successfully in your image viewer, whetever that is in Lubuntu.

To get the item to show in your menu system simply add a line containing ***Categories=Application;*** then copy the .desktop file into ~/.local/share/applications.
You may need to logout and in again before the new menu item appears in the menu.

---

### Post by ActionParsnip on 2020-10-10
Make sure your user has read access to the icon file.
Yes LXDE can have desktop icons
Make sure the desktop file is marked as executable

---

### Post by rbscairns on 2020-10-10
I don't know what was causing the problem with the desktop icon image. I copied the image file to my /Pictures/ directory and edited the electrum.desktop file to point to the new location. Now I have the image in the desktop icon.

Going to sleep now. Will work on the main menu entry tomorrow. Thank you all for your help. I just hope that one day I will be knowledgeable enough to provide similar assistance to others.

---

### Post by ajgreeny on 2020-10-10
Great news! 

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

