---
title: "Configuring Gnome Desktop"
date: 2023-05-05
forum: General Help
---

### Post by Quarkrad on 2023-05-05
I have a neighbour who has asked me to make her (ubuntu-mate) Desktop look as much like Windows as I can.  My experience is using ubuntu-mate but with the help of various youtubes and web pages I am just about there.  Essentially installing the gnome Desktop and mainly use the *Dash to Panel* extension to configure the Desktop to look similar to Windows.  As said, at this point I am happy with the result. But ..... on a number of *other* (ubuntu-mate) Desktops, including my own, I utilise a number of scripts that I have written to do various tasks.  I action these .sh scripts by creating a custom launcher on the top panel and where necessary choose the 'Application in Terminal' option to run the script.  For example, I might have a .sh script in /usr/bin/ and in the customer launcher have the Command **sh /usr/bin/xxx.sh**   I would like to be able to have these custom launchers in my neighbours gnome environment but I'm struggling as I have never used Gnome in anger.   In ubuntu-mate it is simply a case of right clicking on the top panel and creating a Customer Launcher.   But I now have a gnome Desktop, using the *Dash to Panel* extension, and struggling to find out how, if it is possible, to add a Cusomer Launcher (in this case in the bottom panel) to run a script in a terminal.  (Played with creating Desktop files but so far nothing has worked.  Any help appreciated).

---

### Post by Claus7 on 2023-05-05
Hello,

go to ~/.local/share/applications and create an xxx.desktop file. The contents of the file can be something like:
> [Desktop Entry]
Name="whatever name you like without the quotes"
Exec="provide path of your script here without the double quotes"
StartupNotify=true
Terminal=false
Type=Application
Icon="give path of an icon of your script without quotes"

if you do so up to this point, then a new application will appear under your gnome shell applications. If you want a panel like experience then install the frippery panel favorites extension and add from the shell this new application to your favorites. It will appear on the top panel of your gnome box.

Regards!

---

### Post by MAFoElffen on 2023-05-07
My recommends: Look at KDE Plasma as a Desktop and see if installing KDE would be a better starting point.

There are also some desktop themes that get close. WindowsFX is a Desktop theme that emulates the look and feel of Windows 11. It is built on the KDE desktop. Articles on it say it has other features that make it emulate some other features to act like Windows. (I don't know that 'that' is a good thing. LOL) I don't know much else about it, so I can't personally endorse it... Look slike the fll version is non-free. But there is a free version.
RE: [https://computingforgeeks.com/install-windowsfx-step-by-step-with-screenshots/](https://computingforgeeks.com/install-windowsfx-step-by-step-with-screenshots/)

---

