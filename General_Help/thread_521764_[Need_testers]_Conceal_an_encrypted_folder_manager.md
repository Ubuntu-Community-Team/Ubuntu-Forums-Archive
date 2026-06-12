---
title: "[Need testers] Conceal: an encrypted folder manager for Linux"
date: 2007-08-09
forum: General Help
---

### Post by keyes on 2007-08-09
Hi,
a public version of my Summer of Code Project is available.

It's a set of tools to encrypt directories on Linux and especially
Ubuntu. It includes:
- a Python module
- a command line tool
- a GTK interface
- a highly experimental KDE interface

I need feedbacks to debug, stabilize this software :)

You can get source, Ubuntu packages and a more detailed article on my blog :
[http://life.lapin-blanc.net/blog/keyes/2007/08/09/conceal-encrypted-folder-manager](http://life.lapin-blanc.net/blog/keyes/2007/08/09/conceal-encrypted-folder-manager)

Thanks.

(Conceal was previously named crypt-manager).

---

### Post by oomingmak on 2007-08-09
Looks interesting.

:)

---

### Post by eternalsunshine on 2007-08-10
Hi,
Nice project.I want to define each stage in order to be helpful
1.There is no problem on installation.
2.I executed the program from console writing conceal-gtk
3.I chose a directory in my home folder and encrypted.
4.The directory turned into a file like shape and when i click it says it is not accessible
5.I wrote conceal to console to decrypt.And it returned,
> 
Open    Path
Yes     /home/burhan/Conceal

But didnt decrypt the directory.
6.I wrote conceal-gtk to console to decrypt.From GUI i chose decrypt file.And it returned(actually it went into an infinite loop),Finally i interrupted it by keyboard ctrl-c.
> 
Unmounting...
Exception in thread Thread-1:
Traceback (most recent call last):
  File "threading.py", line 460, in __bootstrap
    self.run()
  File "/usr/bin/conceal-gtk", line 574, in run
    conceal.Manage(folder).decrypt(self.password)
  File "/usr/lib/python2.5/site-packages/conceal.py", line 420, in decrypt
    self.unmount()
  File "/usr/lib/python2.5/site-packages/conceal.py", line 410, in unmount
    self.encfs.unmount()
  File "/usr/lib/python2.5/site-packages/conceal.py", line 301, in unmount
    subprocess.Popen([FUSERMOUNT, "-z", "-u", self.folder.path])
  File "subprocess.py", line 593, in __init__
    errread, errwrite)
  File "subprocess.py", line 1135, in _execute_child
    raise child_exception
OSError: [Errno 2] No such file or directory

Traceback (most recent call last):
  File "/usr/bin/conceal-gtk", line 740, in <module>
    main()
  File "/usr/bin/conceal-gtk", line 736, in main
    gtk.main()
KeyboardInterrupt

7.I also looked into the folder /tmp/conceal/aDigestWithManyLetter and it was empty.

Good Luck...

---

### Post by yopnono on 2007-08-10
Ok, so this is the new thread to post in?

The nautilus entry works, however I think it's better to have the context name renamed, to 'Decrypt' instead of just 'Open', and something like 'Close Decrypted Folder' instead of close.

Have you removed the gnome menu entry's totally?

Still see the broken image in the Decrypt dialog.
Other small thing: make the space between the right text and the border a bit more. If you look at the IDLE you see it's just on the edgy, same for the password entry box and the dropdown menu.

---

### Post by yopnono on 2007-08-10
Ok more stuff.
Why not add an icon in the nautilus context menu for decrypt/encrypt, like fileroller etc,etc.

Also it's adding an emblem to the encrypted folder good, but.. if I decrypt and remove the folder from the conceal manager it still have the emblem.

EDIT: The emblem does get removed after logoff/logon.

---

### Post by keyes on 2007-08-13
eternalsunshine> Ok. Can you attach me a TAR archive (compressed with gzip or bzip2) of the folder you try to encrypt please ?

yopnono> I've renamed context entries, fixed missing images and increased the border size :) The entry in the GNOME menu (System -> Preferences) is still active.

For the icon, I'm looking for one, if you know something of free... or if you want to do something in the Pango / Tango style send it me :)

For the emblem, there is no way to remove it "on the fly" in Nautilus :(

---

### Post by yopnono on 2007-08-13
> The entry in the GNOME menu (System -> Preferences) is still active.
I did not get that in the 002 version.

> For the icon, I'm looking for one, if you know something of free... or if you want to do something in the Pango / Tango style send it me

Are you talking about the context menu icons?
Why not just use the standard gtk icon "gtk-dialog-authentication"

---

### Post by keyes on 2007-08-16
> **yopnono said:**
> I did not get that in the 002 version.


:|

Are you talking about the context menu icons?
Why not just use the standard gtk icon "gtk-dialog-authentication"

I use this icon.

Conceal 0.0.3 released : [http://life.lapin-blanc.net/blog/keyes/2007/08/16/conceal-003-2](http://life.lapin-blanc.net/blog/keyes/2007/08/16/conceal-003-2)

Have you still the menu bug ?

---

### Post by yopnono on 2007-08-17
> **keyes said:**
> Have you still the menu bug ?

Yes since the installer don't have the  /usr/share/applications/*.desktop file

Also you should not hardcode the path to the icons, better to use the the icon theme icons.
That way the icon follow the icon theme style.

ICON = "/usr/share/conceal/locked.png"
ICON = "gtk-dialog-authentication"

Also if you like to use your own custom icons then it's better to place them in /usr/share/pixmaps
and name them after some name you like IE: the main icon is now called "icon.png" but if you put the icon in pixmaps and call it... conceal.png, then the icon theme creaters can and there own icon that follows their icon style.

Qustion: Why not place the menu entry in application-accessories? 

```
[Desktop Entry]
Name=Encrypted directories
Name[fr]=Dossiers chiffrés
Comment=Add and manage encrypted directories
Comment[fr]=Ajouter et gérer les dossiers chiffrés
Exec=conceal-gtk
Icon=conceal
Terminal=false
Type=Application
Categories=GNOME;GTK;Utility;
StartupNotify=true
X-KDE-SubstituteUID=true
Encoding=UTF-8
```

//Mike


Other small thing, the property dialog need some more space between the border and buttons.

---

### Post by yopnono on 2007-08-17
Naa it's probably better to have the menu in system submenus like now.

---

### Post by keyes on 2007-08-17
Ok I've applyed your advises for the icons it's fixed in SVN.
I've corrected the installer to add the desktop file in the good place...

The border in the properties window was already fixed in SVN :)

Thanks for the reports.

---

### Post by mdurham on 2007-08-17
Should the checkbox that has "Remind my password"  be "Remember my password"?

---

### Post by keyes on 2007-08-19
Thanks mdurham, fixed in 0.0.4 available on [Code'N'Roll]("http://life.lapin-blanc.net/blog/keyes/tag/Conceal") !

---

### Post by yopnono on 2007-08-20
> **keyes said:**
> Thanks mdurham, fixed in 0.0.4 available on [Code'N'Roll]("http://life.lapin-blanc.net/blog/keyes/tag/Conceal") !

It all looks ok, the only thing that I miss is the open to remember the "always auto unmount after XXmin"
Like you have in the Cryptkeeper. 

Is it not possible to set a value for all folder? And also the possibility to override a specific folder.

---

### Post by keyes on 2007-08-22
> Is it not possible to set a value for all folder? And also the possibility to override a specific folder.

I'll work on that.

New version (see my blog for the changelog): [http://life.lapin-blanc.net/blog/keyes/2007/08/22/conceal-005](http://life.lapin-blanc.net/blog/keyes/2007/08/22/conceal-005)

---

### Post by yopnono on 2007-08-26
One thing. I still get the conceal-gtk zombie process sometimes.

---

### Post by scottevan on 2007-09-21
Attempting to install "conceal-gtk_0.0.5-0ubuntu1_all" under Feisty Fawn, I get "Error: Dependency is not satisfiable: conceal". Any suggestions?

---

### Post by panthyr on 2007-11-16
From the GUI (I don't know commands for terminal) when I try to decrypt I get this in my terminal:
alinuxuser:~$ conceal-gtk
Mounting...
Unmounting...
Exception in thread Thread-1:
Traceback (most recent call last):
  File "threading.py", line 460, in __bootstrap
    self.run()
  File "/usr/bin/conceal-gtk", line 593, in run
    conceal.Manage(folder).decrypt(self.password)
  File "/usr/lib/python2.5/site-packages/conceal.py", line 438, in decrypt
    self.unmount()
  File "/usr/lib/python2.5/site-packages/conceal.py", line 418, in unmount
    self.encfs.unmount()
  File "/usr/lib/python2.5/site-packages/conceal.py", line 309, in unmount
    subprocess.Popen([FUSERMOUNT, "-z", "-u", self.folder.path])
  File "subprocess.py", line 593, in __init__
    errread, errwrite)
  File "subprocess.py", line 1135, in _execute_child
    raise child_exception
OSError: [Errno 2] No such file or directory

this happens every time and the program (GUI at least) gets caught in an infinite loop that closing the terminal window seems to stop.

Also at one point Conceal wouldn't take my (CORRECT) passwords (while trying to decrypt) until I rebooted.

I experimented with one folder and deleted it while it was closed and encrypted and it didn't effect Conceal in any way I have seen (the folder is still there for Conceal and on reboot). I also made other test folders I did not delete.

Also, I don't know how to uninstall Conceal and Conceal-GTK. If I have to reinstall Linux and start over is there a package manager that will handle this programs un-install?

THANKS!
Panther

---

### Post by lngndvs on 2008-06-16
I see this thread is about defunct.  I am using Hardy, AMD64.  I installed from ubuntu debs as linked at [http://linux-tutor.org/?q=en/node/11](http://linux-tutor.org/?q=en/node/11) .  I am frustrated.  A friend followed my lead and locked up his data: he can no longer access it.  All of the links I see are getting old, so I fear this project has dropped off the edge.  

I have tried many things.  Yesterday it worked briefly, then I don't know what I did that hosed the whole thing.  I was able at that time to encrypt a directory, then, after logging out and in, to open and see the files that were otherwise invisible (concealed).  Then I may have done something, I don't know, like kill a process that was hanging (decrypt was hanging) or reboot in the middle of something.  Or maybe nothing.  Today, it doesn't work.  Reboot.  Log out and in.  Remove (dpkg --purge) the three packages, then reinstall.  Remove the packages, download source, and try to install.  Nothing works.  

The common thread: the following messages are always found when running conceal from the command line, indicating something wrong with either the python code or the setup.  Perhaps encfs?  Here are the messages:

> 
eclectico@moseley:~$ conceal -c enc3
Unmounting...
Traceback (most recent call last):
  File "/usr/bin/conceal", line 224, in <module>
    Main()
  File "/usr/bin/conceal", line 78, in __init__
    self.close()
  File "/usr/bin/conceal", line 165, in close
    folder = conceal.Manage(folder).unmount()
  File "/usr/lib/python2.5/site-packages/conceal.py", line 418, in unmount
    self.encfs.unmount()
  File "/usr/lib/python2.5/site-packages/conceal.py", line 309, in unmount
    subprocess.Popen([FUSERMOUNT, "-z", "-u", self.folder.path])
  File "/usr/lib/python2.5/subprocess.py", line 594, in __init__
    errread, errwrite)
  File "/usr/lib/python2.5/subprocess.py", line 1147, in _execute_child
    raise child_exception
OSError: [Errno 2] No such file or directory

I don't know ANY python.  Does this suggest anything to anyone?  Is this thread permanently dead?

Thanks for any suggestions.  

Alan

---

