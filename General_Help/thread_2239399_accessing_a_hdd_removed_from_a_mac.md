---
title: "accessing a hdd removed from a mac"
date: 2014-08-13
forum: General Help
---

### Post by youdoofus on 2014-08-13
Ok, so a coworker who is also a friend of mine had bis only sister pass away not too terribly long ago and she had a mac. Well, he removed the hdd from the mac and put it into an external casing and asked me if I would be able to get the stuff from the hdd onto something else like a flash drive etc etc. Well, I knew that windows wouldnt even recognize it, so I pulled out the trusty xps thats tribooted with windows 7, 8 and the ever reliable Ubuntu.  Viola, I can see the drive but when I go into the user folders, or any folder really, it gives me a permissions error. I saw somewhere a few lines of code to enter in terminal that should allow me access, but im admittedly a little green in the ways of command line entering in Linux.  Could someone be so kind as to help me help a friend to retrieve his deceased sisters stuff?

---

### Post by coffeecat on 2014-08-13
I'm so sorry to hear about your friend's loss.

Copying from a Mac drive - this is a common problem. The drive will be formatted with the journalled version of HFS+ which Ubuntu can mount read only. Which would be OK except that the UID ownership of the Mac files will be different from the UID of the Ubuntu account you are using and permissions in some folders will prevent you from accessing them. That would be OK if you could adjust the permissions but as the drive is mounted read-only, you can't.

Easy workaround with one slight complication. You need to use a root owned file browser. As you haven't said whether you are using Ubuntu or one of the derivatives and which release, I'll have to make some assumptions. First of all, plug the drive in and mount it from the file browser by clicking on where it appears in the left pane. Now open a terminal and:

```
gksu nautilus /media
```

Do you get an error? Then you are running one of the recent releases of Ubuntu where gksu is not included in a default install. So...

```
sudo apt-get install gksu
```

Let that complete. Now:

```
gksu nautilus /media
```

A root nautilus will open in the media directory. Depending on the version of Ubuntu you are running, there will be a subfolder with the name of the Mac drive, or a subfolder with your Ubuntu account name inside which will be the folder with the Mac drive. Drill down into the mountpoint of the Mac drive and from there you will be able to browse the Mac filesystem.

Practical tip. If you copy the Mac files with the root file browser to a Linux filesystem, such as your Ubuntu home folder, I'm not sure what the ownership and permissions of the copied files will end up with, to be honest. To circumvent any potential problems, simply plug in a second external HD formatted with a Microsoft filesystem such as FAT32 or preferably NTFS, and copy to that. That will neatly skip around ownership and permission problems and will put the files on a drive that your friend will probably find more convenient anyway. You may come across one or two files that have filename characters that are illegal in Windows, such as certain punctuation characters. Ubuntu will copy them but Windows will refuse to touch them. If that happens, simply rename them on the NTFS drive with Ubuntu and then you should be OK.

---

### Post by youdoofus on 2014-08-13
You are the man, man! Yes, im using Ubuntu x86 14 lts. Im gonna give that a whirl right now. Your quick and helpful reply is one of the things that makes Ubuntu so great. Ill letcha know what the outcome is :) thanks again!!

---

### Post by youdoofus on 2014-08-13
Ok, so i tried this and the nautilus window tries to open then quickly closes. I realized that i was in terminal with elevated privileges and that wasnt part of the instructions so i backed out and tried it again. It then asked me for my administrative password, which i obviously know since i was in terminal with elevated priveleges, so i entered that pw. It said that it was incorrect. I tried my other password i use for my user account (the general pw used at the lockscreen) and it failed... Im kinda confused because i then went back into terminal, typed "su" and enter, it asked me for my SU pw, which i entered and then gave me the # level of access... im confused lol

---

### Post by coffeecat on 2014-08-13
It sounds as though you have a non-standard installation if you have a su password, which confuses things. Don't try to get a root terminal. Do it the Ubuntu way.

Have you installed gksu? If so, run this in the terminal:

```
gksu-properties 
```

Make sure authentication mode is set to sudo.

---

### Post by youdoofus on 2014-08-13
Yeah, i installed it and it said tha tit completed successfully, i even tried to install it again just to make sure, and it went thru an update instead of the install

below is what happens when i type the command

dug@dug-XPS-M1530:~$ gksu nautilus /media

(gksu:3945): dconf-CRITICAL **: unable to create file '/run/user/1000/dconf/user': Permission denied.  dconf will not work properly.

(gksu:3945): dconf-CRITICAL **: unable to create file '/run/user/1000/dconf/user': Permission denied.  dconf will not work properly.

(gksu:3945): dconf-CRITICAL **: unable to create file '/run/user/1000/dconf/user': Permission denied.  dconf will not work properly.

(gksu:3945): dconf-CRITICAL **: unable to create file '/run/user/1000/dconf/user': Permission denied.  dconf will not work properly.

(gksu:3945): dconf-CRITICAL **: unable to create file '/run/user/1000/dconf/user': Permission denied.  dconf will not work properly.

(gksu:3945): dconf-CRITICAL **: unable to create file '/run/user/1000/dconf/user': Permission denied.  dconf will not work properly.

(gksu:3945): dconf-CRITICAL **: unable to create file '/run/user/1000/dconf/user': Permission denied.  dconf will not work properly.

(gksu:3945): dconf-CRITICAL **: unable to create file '/run/user/1000/dconf/user': Permission denied.  dconf will not work properly.
GNOME_SUDO_PASS
sudo: 1 incorrect password attempt

(nautilus:3954): GLib-GObject-WARNING **: invalid cast from 'GtkMessageDialog' to 'NautilusWindow'
**
ERROR:nautilus-window.c:2116:nautilus_window_get_slots: assertion failed: (NAUTILUS_IS_WINDOW (window))
dug@dug-XPS-M1530:~$

---

### Post by coffeecat on 2014-08-13
> **youdoofus said:**
> 
below is what happens when i type the command

But did a nautilus window open?

Never mind. You must really have a problem on your system because that should not happen. Try this:

```
sudo -H nautilus /media
```

Although you normally shouldn't use sudo with a graphical app, the -H option makes this OK.

---

### Post by youdoofus on 2014-08-13
Hmmmm, now i get this... if its likely a system issue, i can easily go to another computer in the house that has Ubuntu on it, altho i think that its the 12 edition (not that, that should really matter methinks) lemme go do that quick


dug@dug-XPS-M1530:~$ sudo -H nautilus /media

(nautilus:6018): Gtk-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

(nautilus:6018): GLib-GObject-WARNING **: invalid cast from 'GtkMessageDialog' to 'NautilusWindow'
**
ERROR:nautilus-window.c:2116:nautilus_window_get_slots: assertion failed: (NAUTILUS_IS_WINDOW (window))

---

### Post by coffeecat on 2014-08-13
The best thing would be to use a live CD or live USB. All of those commands work just fine on my system. So as not to have to install gksu in the live session, simply use this to get a root nautilus:

```
sudo -H nautilus /media
```

You will get something like this:

```
(nautilus:8446): Gtk-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
```

Ignore it.

---

### Post by youdoofus on 2014-08-13
weird... it has to be something with the computer... Im now on a different computer (thank God i have 4 in the house hold, 3 of which have some sort of distro of Ubuntu on it. This one just so happens to be Zorin) and the first command at the very top of your replies worked without issue. Thanks again man! My friend should be pumped to get his sisters stuff back!!

---

### Post by youdoofus on 2014-08-13
UGH!!! now i can see the stuff, but i cant drag and drop the very same stuff to an external :/

---

### Post by youdoofus on 2014-08-13
Now what? LoLI even tried the sudo version you mentioned when i was on the other computer :(

---

### Post by youdoofus on 2014-08-13
> **coffeecat said:**
> The best thing would be to use a live CD or live USB. All of those commands work just fine on my system. So as not to have to install gksu in the live session, simply use this to get a root nautilus:

```
sudo -H nautilus /media
```

You will get something like this:

```
(nautilus:8446): Gtk-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
```

Ignore it.

while on the other computer, i can see the files, even open them, but when i try to move them, im getting permissions errors. Any thoughts?

---

### Post by coffeecat on 2014-08-13
Where are you trying to move them to? What are the error messages?

---

### Post by youdoofus on 2014-08-13
> **coffeecat said:**
> Where are you trying to move them to? What are the error messages?

a fat formatted 32 GB flashdrive

error im getting is 

Error while copying "iPhoto Library".
There was an error copying the file into /media/New Volume
Error opening file: Permission denied



It cant be the flash drive because i could copy stuff from the public folder

---

### Post by coffeecat on 2014-08-13
> **youdoofus said:**
> 
Error opening file: Permission denied


The Mac must have set up something odd if a root file browser can't open it, but it's too late in the evening for me to think about this.

Is "iPhoto Library" a file or folder? If a file it could be just an index of images. The important thing would be to copy the images themselves. So one option might be to simply skip this one.

**Edit**: Since you can't write to the partition from Ubuntu, which means you can't change permissions, if a root file browser can't open a file or folder, then you're stuck - at least with that file or folder - and the only option would be to use another Apple Mac.

---

### Post by youdoofus on 2014-08-13
ok, thanks for the help so far man! I just went into the properties of the drive itself and the file access field was blank, i changed it to read and write. Lets hope thats the trick :)

---

### Post by youdoofus on 2014-08-15
Well, chmodding 777 to -r rw didnt work, so I contacted a good friend who is a unix admin for EROS and had him teamviewer remote into my system and her got it for me. Watching him flip between terminal tabs fast as lightning was truly humbling. But end result is he got it done. Ended up unmounting and remountingas rw and moved all files to a flash drive. All privileges working. I had to call in the big guns, but got it done :D thanks again man!

---

