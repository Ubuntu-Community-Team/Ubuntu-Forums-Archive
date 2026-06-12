---
title: "[SOLVED] Changing Permissions in Gnome"
date: 2008-06-10
forum: General Help
---

### Post by Spaceman9 on 2008-06-10
Is there a file browser for Ubuntu 8.04 Gnome that can change file permissions? I used to use krusader in KDE but I hate to install a KDE file browser into Gnome.

I know I can type commands into a terminal but I'm looking for an easy push button way to change permissions on data files on my backup drive. Thankx for any help.

---

### Post by hal8000 on 2008-06-10
At this moment I'm not on my Ubuntu system, but believe you can right click any file, permissions and adjust properties that way, providing you own the file of course.

Have a look at this as well,
[http://www.ubuntugeek.com/enable-the-advanced-file-permissions-dialog-in-nautilus-the-gui-way.html](http://www.ubuntugeek.com/enable-the-advanced-file-permissions-dialog-in-nautilus-the-gui-way.html)

but its quicker to use chmod from a terminal
e,g chmod 644 myfile etc

---

### Post by drs305 on 2008-06-10
> **Spaceman9 said:**
> Is there a file browser for Ubuntu 8.04 Gnome that can change file permissions? I used to use krusader in KDE but I hate to install a KDE file browser into Gnome.

I know I can type commands into a terminal but I'm looking for an easy push button way to change permissions on data files on my backup drive. Thankx for any help.

You can change them (individually or by highlight groups of files) in nautilus with a right click, Properties, then Permissions. Open nautilus with the following command to allow root privileges:
```
gksudo nautilus
```

You might be interested in this blog. It came out last week and discusses advanced permission-setting via nautilus. You can run this command to enable this feature, and change the value to 'false' to change it back if you don't like it. It is nothing ground-breaking - it just displays the permissions instead of using drop-down menus.

The blog:
[Enable the Advanced File Permissions Dialog in Nautilus]("http://tombuntu.com/index.php/2008/05/30/enable-the-advanced-file-permissions-dialog-in-nautilus/")

The command:
```
gconftool-2 --type bool --set /apps/nautilus/preferences/show_advanced_permissions True
```

---

### Post by Spaceman9 on 2008-06-10
Hal8000 and drs305 I used gconf-editor and ticked show_advanced_permissions, but it didn't help.  So I typed in gconftool-2 --type bool --set /apps/nautilus/preferences/show_advanced_permissions True
 but it didn't help. 

I don't know much yet about commands. Can one of you tell me exactly what I have to type to change permissions on a file and permissions on a folder? How would I change permissions on all the files in a folder? Thankx for your help.

---

### Post by Spaceman9 on 2008-06-10
I think I found an answer for changing permissions in Gnome that I can live with that can pretty much replace krusader from KDE.

Editing Files that Belong to Root [http://www.psychocats.net/ubuntu/permissions#gui](http://www.psychocats.net/ubuntu/permissions#gui)

If you're using Ubuntu (Gnome), press Alt-F2 and type 
gksudo nautilus
then click on Run

This will open the nautilus file browser in root mode. Then you can change permissions on files or an entire folder.

I only use this for changing the permissions of my data files on my backup drive because I have 2 different distros installed. I NEVER use it for system files.

---

