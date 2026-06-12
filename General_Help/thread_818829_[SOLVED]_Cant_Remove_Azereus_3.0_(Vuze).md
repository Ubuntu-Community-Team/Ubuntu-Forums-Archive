---
title: "[SOLVED] Cant Remove Azereus 3.0 (Vuze)"
date: 2008-06-04
forum: General Help
---

### Post by shinde on 2008-06-04
i need some help.  i installed vuze awhile ago.  i want to uninstall it now.  i cant find it in SPM anywhere.  ill prob have to do it in terminal.  any suggestions?

this is how i installed vuze

[INDENT][INDENT]1. Make sure you have sun Java 1.5 or 1.6 installed and working. To see if what your Java version is set by default type: java -version in the terminal.

2. Download Azureus 3.0 (Vuze) linux version: Here. Save it to your Desktop.

3. Open up for the terminal:

```
cd Desktop
sudo tar jxvf Azureus_3_0_linux.tar.bz2 -C /opt/
sudo chown -R <username>:<username> /opt/azureus/
```

4. Now we need a launcher from the Application tab, fire up the terminal again:
```

sudo nano /usr/share/applications/Azureus.desktop
```

add:

> [Desktop Entry]
Name=Azureus
Comment=P2P Client
Exec=/opt/azureus/azureus
Icon=/opt/azureus/Azureus.png
Terminal=false
Type=Application
Categories=Application;Network;

5. This is optional. If you want azureus to launch from a command in the terminal:

```
sudo nano /usr/bin/azureus
```

add:

> #!/bin/sh

/opt/azureus/azureus "$*"

save it and close it.
Now the last thing in the terminal:

```

sudo chmod +x /usr/bin/azureus
azureus
```

Now get the any updates and plugins you need. After that exit Azureus (so there aren't any azureus tray icon). Then;

```
sudo chown -R root:root /opt/azureus/
```
[/INDENT][/INDENT]

thnx for help in advanced.

-shinde

---

### Post by shinde on 2008-06-04
i figured it out.  sorry to waste forum space.

---

### Post by BuffaloBill on 2008-12-03
Hi!

I would rather enjoy to see your solution.

Thanks!

---

### Post by BuffaloBill on 2008-12-03
Ok, to remove Vuze, you have to go in the synaptic package and simply remove the Azureus package, which will ask you to remove Vuze.

---

### Post by kbtarl on 2008-12-15
I'll try that. Ever since I installed Vuze 4.0, my internet for my whole network has been screwy. Now I've had it shut down internet access through my router for the whole network. I've got it back up but everytime I try to run Vuze it references something about UPNP and something not released then the internet shuts down again. I've got all my network back to normal except the unbuntu station. It has local access only...no internet. Think unistalling azereus (vuze) will fix it? I can not even get internet booting from a live CD.

---

### Post by spike_naples on 2009-03-27
I hate Vuze for Ubuntu.

I would recommend KTorrent or Deluge.

Vuze doesnt even uninstall correctly. To uninstall go to SPM and search for Azureus then choose to completely uninstall all packages to get rid of the remnants of Vuze.

---

### Post by greylander on 2009-04-13
I have had same problem.  I am not sure that I have completely uninstalled it, but here is what I found.

In Nautilus file browser (or use "find" in a terminal window if you know how, see the man page)... navigate to /usr and search "vuze" then search "asureus" and delete whatever you find -- unless of course you find something you believe has those words in the file/directory name but is somehow unrelated to vuze.

Next, do the same in opt (specifically, there was the directory /vuze/opt).

Likewise search for and delte anything with vuze or azureus in the file/directory name that is in your home directory(ies).

I think this pretty much gets rid of it.  If you try vuze from the command line, it says not installed and suggests using apt-get to install it, so that is a good sign.

What I am particularly uncertain of is whether this gets rid of all references to vuze, such as in mimetypes files for file associations and default apps.  I am not sure where to look for such things.

I have to agree with all who hate Vuze... it looks like something that belongs on windows or Mac... social networking? recommendations?  looks and feels like adware, bloatware... not sure if it is, never looked that close.

I recommend utorrent under Wine.  Works great!

---

