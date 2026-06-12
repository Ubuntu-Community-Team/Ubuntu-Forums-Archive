---
title: "MenuLibre - Attempting launcher for MInecraft - Parsing Error"
date: 2021-12-12
forum: General Help
---

### Post by makem2 on 2021-12-12
I am attempting to place a launcher in the Ubuntu Applications Menu to start Minecraft in a Terminal.

I used MenuLibre to do this and it produced the below .desktop entry:

[Desktop Entry]
Version=1.1
Type=Application
Name=Minecraft
Comment=MC Startup
Icon=applications-other
Exec=/media/terabyte/minecraft/paper-1.17.1-399.jar
Path=/media/terabyte/minecraft
Terminal=true
Actions=
Categories=X-XFCE;X-Xfce-Toplevel;
StartupNotify=true

The entry is placed in the games folder of the Applications Menu. However when I select this entry the Terminal opens and I get the following error:

Failed to execute child

Failed to execute child process "/media/terabyte/minecraft/paper-1.17.1-399.jar": Failed to execvw: Permission denied. The terminal stays open but is unusable after closing the error message.

When I open MenuLibre, the new entry is not there and there is an error:

Invalid desktop files! Please see details. Selecting Details shows:

Parsing Errors

The following desktop files have failed parsing by the underlying library, and will therefore not show up in MenuLibre. Please investigate these problems with the associated package manager.

/home/makem/.local/share/applications/menulibre-new-launcher.desktop
Unknown error. Desktop file appears to be are valid.

When I right click on the entry in the Applications Menu to edit it I get the following:

Name: Minecraft
Comment: MC Startup
Command: /media/terabyte/minecraft/paper-1.17.1-399.jar
Working Directory: /media/terabyte/minecraft

Icon: There is an Icon
Options: Use startup notification (checked)
Run in terminal (checked)

Can anyone point me to the error cause?

---

### Post by makem2 on 2021-12-12
The problem was that .jar file are not executable. They have to be opened with something, in this case java.

so:

Exec=/media/terabyte/minecraft/paper-1.17.1-399.jar becomes Exec=java -jar /media/terabyte/minecraft/paper-1.17.1-399.jar

The menu item then works and the Terminal stays open allowing the server to be managed.

---

### Post by Holger_Gehrke on 2021-12-12
If the 'META-INF/MANIFEST.MF' inside the jar (a jar is just a zip file with the .class-files and any resources they need ...) gives a class to run, then you can just make the jar file executable and the system should be able to run it. That's the job of the kernel module binfmt_misc. Since that's installed on my system and I didn't do so myself, I think it's installed by default.

Holger

---

