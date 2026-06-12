---
title: "Running Shell script from Desktop Icon"
date: 2013-12-17
forum: General Help
---

### Post by AlexHudghton on 2013-12-17
Ubuntu 12.04

I have created 2 scripts from the command line, which run quite happily in Terminal to launch 2 java applications ( DirSyncPro and Accountz 2012). 

Basically the scripts cd to the relevant directory and then load the java program

One application directs it's background output to the open Terminal Window, the other just has a few headers.

What I would like to do is just click a desktop icon and have these applications start.

There is obviously something I'm not doing as they don't work from the desktop.

Any insight please?

---

### Post by Lars Noodén on 2013-12-17
You'll need a small file for your icon.  In ~/Desktop/ make a file ending in .desktop, such as *myscript.desktop*.  Put something like the following inside it.

```

[Desktop Entry]
Encoding=UTF-8
Name=My Script
Comment=Launch DirSyncPro
Exec=gnome-terminal -e /usr/local/bin/myscript
Icon=utilities-terminal
Type=Application

```

Of course, adjust the details.  

Once the file is in place in the Desktop folder, there will be an icon on your desktop.  If you have Icon= and Exec= set correctly, it should show as an icon and launch your script when you click on it.

---

### Post by jimmyh1972 on 2013-12-17
Yeah...first of all make sure they are placed on your desktop and has executable permissions (sudo chmod +x )
if your Ubuntu is 13 version you should config dconf to allow desktop run bash scripts
[COLOR=#333333][FONT=UbuntuRegular]Hit Alt+F2, type dconf-editor and hit Enter.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]In dconfg-editor goto: org &#10148; gnome &#10148; nautilus &#10148; preferences
[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Click on executable-text-activation and from drop down menu select:[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]**launch**: to launch scripts as programs.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]OR[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]**ask**: to ask what to do via a dialog.[/FONT][/COLOR]

---

### Post by ajgreeny on 2013-12-17
You may not even need to open the script in gnome-terminal, but it depends on what exactly you want.

Here's the TOL.desktop contents I use for Transfer-on-lan which is a java utility for quick file transfers from computer to computer on the same network, and which I highly recommend.
[http://code.google.com/p/transfer-on-lan/](http://code.google.com/p/transfer-on-lan/)
```

[Desktop Entry]
Version=1.0
Type=Application
Name=TOL
Comment=Transfer files over LAN
Exec=/home/*username*/Downloads/TransferOnLAN-0.6.1/TransferOnLAN.sh
Icon=emblem-dropbox-syncing
Path=
Terminal=false
StartupNotify=false

```
Note that in my case the script is run direct without using a terminal.  If you need specific terminal output, you will need to use the Exec= line as shown above.

---

### Post by AlexHudghton on 2013-12-20
Thanks all for the quick replies :)

I now have one working (DirSyncPro) and the other not (Accountz 2012)

Here is my working file

[Desktop Entry] 
Encoding=UTF-8 
Name=DirSyncPro 
Comment=Launch DirSyncPro 
Exec=java -jar /home/alex/Downloads/DirSyncPro-1.46-Linux/dirsyncpro.jar 
Icon=utilities-terminal 
Type=Application


As I said up there ^ Accountz needs the terminal to write output to, while the program is in use

I tried this

[Desktop Entry] 
Encoding=UTF-8 
Name=Accountz 
Comment=Launch Accountz 
Exec=gnome-terminal -e java -jar /opt/Home_Accountz_2012/launcher.jar 
Icon=utilities-terminal 
Type=Application

but it does nothing

Any clues please?

---

### Post by Lars Noodén on 2013-12-20
I would try it with the action quoted:

```

 Exec=gnome-terminal -e "java -jar /opt/Home_Accountz_2012/launcher.jar" 

```

Maybe you also have to have the full path to java as well, /usr/bin/java

---

### Post by AlexHudghton on 2013-12-22
I tried that (this time putting in the quotes that I forgot!), but it now brings up a terminal window and closes it again. I've sent an email to the application developers to see if they can help

Once again thanks for the help - I think I may be getting close now

---

### Post by AlexHudghton on 2013-12-24
Solution found :D

Link to /opt/Home_Accountz_2012/Home Accountz

Run in terminal

All works fine

---

