---
title: "Shortcuts in Ubuntu"
date: 2006-11-23
forum: General Help
---

### Post by telovoyagarcar on 2006-11-23
OK... easy..
how do i create shortcuts here?!!!

I managed to add a line in the fstab file that will mount the windows partition each time the computer starts (ubuntu)... so now i would like to have a shortcut on the desktop or the quick launch bar on top to that drive..

I tried to drag and drop the folder but this will copy the whole folder..
if i right click on it, there is a "Make Link" option but it is greyed so i can't do it..
I know this should be easy..

And another question about shortcuts...
For example, i installed xfce4 graphical mount tool using synaptic and a few others that i forgot now with apt.
The programs install successfuly... but then where do i find the shortcuts to use them? 
then i had to do a research on google to find that i had to type "xfce4-panel" in the CLI to run the application :-| 

Automatix instead, created a shortcut in the applications menu... like it happens in windows when you install programs.

So is there any way to indicate the installers to create shortcuts in the desktop or whatever place, or each program will be different and will not be found until i read the documentation?
I mean... the purpose of xfce4 mount tool is to be a graphical tool to make things easier for us, noobs, so why then should i be doing research to find the right command to execute it? :-k 

Thanks...

---

### Post by Dr Small on 2006-11-23
To create a shortcut to a folder or program, right click on the desktop, and select "Create Launcher".

Name the shortcut, and browse for the program / folder.
If it is an Program, select Application below.
If it is a folder, select Link.

(I learned all this from expirence :))

Dr Small

---

### Post by altaaa on 2006-11-23
You can also do it on the console.

- open up a terminal
- make a symlink using the command [FONT="Courier New"]ln[/FONT], ie. [FONT="Courier New"]ln -s <path-to-mountpoint> <name-for-symlink>[/FONT]. I have mounted my ntfs partition to [FONT="Courier New"]/media/hdd[/FONT], so if I would make a symlink called [FONT="Courier New"]windows[/FONT], I would type the following:

```
ln -s /media/hdd ~/Desktop/windows
```

---

### Post by telovoyagarcar on 2006-11-23
> **Dr Small said:**
> To create a shortcut to a folder or program, right click on the desktop, and select "Create Launcher".

Name the shortcut, and browse for the program / folder.
If it is an Program, select Application below.
If it is a folder, select Link.

(I learned all this from expirence :))

Dr Small

Ok... i would like to do it the GUI way... like you say.. but..
i have these 3 options in the create launcher box:  type: "Application" - "Application in terminal" or "file"...
so none of these will let me select a an entire "folder".. instead it opens the folders trying to find a file.
Why don't i have the "link" option ? im using edgy...

---

### Post by thetoolmandar on 2007-08-16
> **telovoyagarcar said:**
> Ok... i would like to do it the GUI way... like you say.. but..
i have these 3 options in the create launcher box:  type: "Application" - "Application in terminal" or "file"...
so none of these will let me select a an entire "folder".. instead it opens the folders trying to find a file.
Why don't i have the "link" option ? im using edgy...
I experienced just the same thing. If rather than "Browse" and select the folder you want to point to you simply type in the path in the given box, the link will open the whole folder rather than a single file.

---

