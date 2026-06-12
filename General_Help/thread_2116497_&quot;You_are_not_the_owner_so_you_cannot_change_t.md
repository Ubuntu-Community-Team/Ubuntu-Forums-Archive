---
title: "&quot;You are not the owner so you cannot change these permissions&quot; for png files?"
date: 2013-02-15
forum: General Help
---

### Post by grubbles444 on 2013-02-15
I recently went ten rounds with the scanner part of my canon scanner/printer that ended with me be able to open scangearmp only by using 'sudo scangearmp'.

So I have to assume that my problem is being caused by running the program using root. 

I can scan the images no problem, save them no problem, but when I attempt to view or import the files it says I do not have permission. when I go to the permissions tab pf the properties of the image  I cannot change the permissions because I do not own the files, root does.

So my Questions are:

1. Is it dangerous for me to be running scangearmp using sudo?

2. Is there are "...for dummies" explanation as to how I can gain ownership of these files as my user.

3. if 2 is a no, how can I use the files using sudo. 

You guys are all quite brilliant and I appreciate the work you do. Thanks,

---

### Post by 3rdalbum on 2013-02-16
> **grubbles444 said:**
> I recently went ten rounds with the scanner part of my canon scanner/printer that ended with me be able to open scangearmp only by using 'sudo scangearmp'.

So I have to assume that my problem is being caused by running the program using root. 

[QUOTE]when I go to the permissions tab pf the properties of the image  I cannot change the permissions because I do not own the files, root does.

Run the file browser as root:

```
gksudo nautilus
```

and you can change them.

If you like to tinker around and learn command-line, you can check out the "chown" and "chmod" commands; they change the owner and the permission of files respectively. Once again, you'd need to run them as root to change the permissions/ownership of root-owned files.

(An aside; there's a guy who works next to me whose name is Bob Chown, but he's never used Unix so he doesn't know the other meaning of his surname!)

---

### Post by grubbles444 on 2013-02-16
Ha, you should tell him you just just bought a car and you need help transferring ownership. 

Bad jokes aside, when I run the above command it opens the file browser so I click on desktop (which is the only option in the browser under home) and it is blank. is it possible that because the files are on my desktop that even though they belong to root I have to open the file browser under my user to access the files? I don't know how that would differ from actually clicking on my home folder, but thats why I'm here.

---

### Post by pdc on 2013-02-16
hi grubbles;

I left some comments on the previous thread you had initiated:

........seems to me.......better to be a member of the group that owns the scanner: and thus you can access files the scanner generates........

(than change file ownership each time);


.......... above you say..........

> when I run the above command it opens the file browser so I click on desktop (which is the only option in the browser under home) [COLOR="Magenta"]and it is blank[/COLOR].

......I think that is because you have opened as root...........and its desktop is blank........root is the supreme lord..............from the root entry you need to drill down; and find the grubbles entry and get into that; and the grubbles desktop;
.

---

### Post by MrsUser on 2013-02-16
Try this:


```
sudo adduser $USER scanner
```and

```
sudo adduser $USER lp
```Then log out and in again to bring the change in effect. You should now be able to use scangearmp without sudo and access the files you scan without sudo. However, those you scanned already (under sudo) can't be accessed unless you change permissions for those files.

> [...] 6. Your scanner is parallel port and you are not a member of the scanner  group. The device /dev/parport0 (or whichever parallel port your scanner  is connected to) by default is only readable and writable by user lp  and group scanner.
Source: [https://help.ubuntu.com/community/ScanningHowTo#A.22No_device_available.22_-_what_to_do.3F](https://help.ubuntu.com/community/ScanningHowTo#A.22No_device_available.22_-_what_to_do.3F)

---

### Post by 3rdalbum on 2013-02-16
> **grubbles444 said:**
> Bad jokes aside, when I run the above command it opens the file browser so I click on desktop (which is the only option in the browser under home) and it is blank. is it possible that because the files are on my desktop that even though they belong to root I have to open the file browser under my user to access the files? I don't know how that would differ from actually clicking on my home folder, but thats why I'm here.

It's because when you open the root file browser and click Desktop, you're actually viewing root's desktop.

In the root file browser, go to Filesystem, then the "home" icon in the main part of the window (NOT on the left pane), and then your username, and then Desktop.

---

### Post by Yellow Pasque on 2013-02-16
```
cd ~/Desktop  #or wherever you have the files
sudo chown username:username *.png
```

---

### Post by rnerwein on 2013-02-16
> **grubbles444 said:**
> Ha, you should tell him you just just bought a car and you need help transferring ownership. 

Bad jokes aside, when I run the above command it opens the file browser so I click on desktop (which is the only option in the browser under home) and it is blank. is it possible that because the files are on my desktop that even though they belong to root I have to open the file browser under my user to access the files? I don't know how that would differ from actually clicking on my home folder, but thats why I'm here.
hi
the filebrowser should mostely open as your own user and to run your scanner don't use sudo ('sudo scangearmp).
if you run scangearmp from inside of a terminal just run: scangearmp (i guess you have the permission, the program is in your PATH and the name of the program is scangearmp). just try it. and - open your browser without "sudo" !
ciao

---

