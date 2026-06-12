---
title: "Gedit Cannot Save Files!"
date: 2008-06-25
forum: General Help
---

### Post by FlyingIsFun1217 on 2008-06-25
Hello!

Seems Gedit can no longer save files. I noticed this after opening up a file that I needed to edit (which I did), and Gedit could not save the new one. After starting it up cold (not opening a document), any changes to a new document it can't save either. Whats going on here?!?!

Thanks!
FlyingIsFun1217

---

### Post by Ryklou on 2008-06-25
Only thing that i think that is gone wrong is that you  dont have write privileges. or something, try another txt editor and tell me if it still does'nt let you save.   ... this is weird (oh before this happened what did you install,, deleate, or change?)

---

### Post by dexter.deepak on 2008-06-25
is it for "one particlular" file or all files ?
see if you have changed the permissions of the file you try editing.

also give the exact error msgs.(if they are being given to you !!)

---

### Post by dopple on 2008-06-25
does it work when you use sudo before i.e.
```
sudo gedit file.txt
```
then save

---

### Post by FlyingIsFun1217 on 2008-06-25
Yes, using root lets me write, but all else is read-only.

No over-ftp/ssh-connections, just straight, right to the disk writing. Not to mention files in my home directory which I definitely own.

No error is given other than the save button being grayed out, along with the same item in the file menu.

Most I can think of was that I recently created a guest account, but that shouldn't have changed anything for me.

FlyingIsFun1217

---

### Post by dexter.deepak on 2008-06-25
may be you are logged into the "guest" account, and are trying to write to "your" home ?

---

### Post by FlyingIsFun1217 on 2008-06-25
Nope, I'm on my account (as the terminal is showing me).

FlyingIsFun1217

---

### Post by FlyingIsFun1217 on 2008-06-25
Does anybody have any ideas why I can write files using root accounts, but not my own (only in Gedit, for that matter)?

FlyingIsFun1217

---

### Post by drs305 on 2008-06-25
Run the following commands. The first shows the users. The second which groups you belong to. You should see your name in both, as the user you expect.
```
users
groups
```

Next open a file manager as a normal user (e.g. nautilus). Make a folder on your desktop (untitled folder). Make a file in that folder (new file). Now right click on the file, select 'open with' gedit, and try to edit and save the file. Can you do it?

---

### Post by FlyingIsFun1217 on 2008-06-25
> **drs305 said:**
> Run the following commands. The first shows the users. The second which groups you belong to. You should see your name in both, as the user you expect.
```
users
groups
```

Next open a file manager as a normal user (e.g. nautilus). Make a folder on your desktop (untitled folder). Make a file in that folder (new file). Now right click on the file, select 'open with' gedit, and try to edit and save the file. Can you do it?

I know that it can't be user permissions, because other apps CAN save files (so it's a Gedit-specific thing). That, and I did try it, so...

FlyingIsFun1217

---

### Post by iaculallad on 2008-06-25
> **dopple said:**
> does it work when you use sudo before i.e.
```
sudo gedit file.txt
```
then save

When accessing graphical applications that needed privileges, try to use gksudo instead. When using terminal commands that needs privilege, stick with sudo.

On using gedit:

```
gksudo gedit /path/your_path/file.ext
```

On using vi or nano:

```
sudo vi /path/your_path/file.ext
sudu nano /path/your_path/file.ext
```

As for the explanation: Try reading this page on [Running Sudo Graphically]("http://www.psychocats.net/ubuntu/graphicalsudo")

---

### Post by drs305 on 2008-06-25
Have you tried using synaptic to 'mark for complete removal' and uninstall it? There isn't much in a gedit configuration file and it would be simple to reinstall. 

First copy the ~/.gconf/apps/gedit-2 folder or rename it. Then uninstall and reinstall it. If that doesn't fix it, you can delete the new gedit-2 folder and restore the original.

---

### Post by FlyingIsFun1217 on 2008-06-26
Nope; I had previously just tried a reinstall, but even the clean install gives me a gedit that cannot save anything under my user account.

This is getting... REALLY odd...

Thanks!
FlyingIsFun1217

---

### Post by FlyingIsFun1217 on 2008-06-26
Is there maybe a certain config file that is not rewritten in a clean install?

FlyingIsFun1217

---

### Post by drs305 on 2008-06-26
> **FlyingIsFun1217 said:**
> Is there maybe a certain config file that is not rewritten in a clean install?

FlyingIsFun1217

I did a complete removal of gedit and gedit-common and found these files still on my machine. Also, I had to mark gedit-common separately for removal; gedit alone didn't remove gedit-common. 
```

/home/username/.gconf/apps/gedit-2
/home/username/.gconf/apps/gnome-settings/gedit
/home/username/.gnome2/gedit
/usr/lib/gedit-2
/root/.gconf/apps/gnome-settings/gedit
/root/.gconf/apps/gedit-2

```

---

### Post by FlyingIsFun1217 on 2008-06-27
Well, nothing in those directories led me to believe that any of their contents would keep me from saving.

Is there any sort of permission that my user might have set on gedit to keep it from being able to write to the file system?

Thanks again!
FlyingIsFun1217

---

### Post by jakupl on 2008-06-27
...
well please try this, just to make sure, and also to clarify.

right click your Desktop.
Click "Create Document" ---> "Empty file".

open it with gedit and try to write something into it.

save.

Does this not work?

---

### Post by FlyingIsFun1217 on 2008-06-28
Trust me when I say by now, that DOES NOT work.

FlyingIsFun1217

---

### Post by FlyingIsFun1217 on 2008-06-28
Seems my other account (the 'guest' account) has write-access to the drive.

FlyingIsFun1217

---

### Post by FlyingIsFun1217 on 2008-07-15
As crazy as this problem was, it was fixed by simply reinstalling linux (I didn't reinstall just because of this though, I needed to reinstall vista too :/).

FlyingIsFun1217

---

### Post by Hackbert's Celine on 2009-03-27
I have the same issue and its not true that its a gedit related one. I can edit a file when i first create it in nautilus. The same thing with OpenOffice, so is there any lib wich is used by both for creating files? With nano or vi there are no problems so maybe also x related? 

btw why didnt you try it Flyingisfun?

---

### Post by Hackbert's Celine on 2009-03-31
After checking a few bug reports i solved the Problem by deleting all content of my .gtkboomarks file in my home folder. Its a bug in gnome-vfs described here [http://bugzilla.gnome.org/show_bug.cgi?id=514843](http://bugzilla.gnome.org/show_bug.cgi?id=514843).

---

