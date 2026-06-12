---
title: "Help with Knoppix and Ubuntu"
date: 2008-03-08
forum: General Help
---

### Post by UK-Wobbie on 2008-03-08
Where to start lol
My Ubuntu as stopped booting up so i have got some boot files from a Ubuntu live CD,
And now i loaded Knoppix to deleted the old files and put the new ones.
But the only thing is it will not yet me login as root, It needs root permissions!


I know how to login as root in Terminal in Knoppix , But i do not know how to work it ..To move the new files to the boot folder :confused:


I need some line code so i can move files in root,
And hopping that moving the new boot files will fix my problem.

Thanks

---

### Post by taurus on 2008-03-08
From Ubuntu LiveCD, open a terminal and run

Applications -> Accessories -> Terminal
```
gksudo nautilus
```
That would give you a root privilege.  No need to use Knoppix.

---

### Post by UK-Wobbie on 2008-03-08
> **taurus said:**
> From Ubuntu LiveCD, open a terminal and run

Applications -> Accessories -> Terminal
```
gksudo nautilus
```
That would give you a root privilege.  No need to use Knoppix.

I give it a go thanks :)
Anything to fix this lol

---

### Post by UK-Wobbie on 2008-03-08
> **taurus said:**
> From Ubuntu LiveCD, open a terminal and run

Applications -> Accessories -> Terminal
```
gksudo nautilus
```
That would give you a root privilege.  No need to use Knoppix.

I have had a go using Ubuntu but it was not showing my home folder and all my work.
Using Knoppix  is showing my work and my home folder, And Ubuntu files.

What i am having a go doing as my Ubuntu will not boot up any more is to  re put all the boot files back in to the boot folder.
As i have got the boot files from a Ubuntu live CD, So putting it back in to the boot folder may fix my problem i hope :(

I need a way to chaen premissons from the Knoppix live CD, From Terminal to root.
So i can chaen the boot folder  premissons and put the new boot files in to the boot folder.
And then i can chaen the premissons back.

Thanks

---

### Post by Irony on 2008-03-08
If gksudo nautilus isn't showing your home folder it is because you are looking in the wrong place - note you'll have to go to file system and down to home.

In knoppix just type su then the password (which I assume is 'root')

---

### Post by taurus on 2008-03-08
Or perhaps you need to mount your harddrive first before you can access it.  Ubuntu doesn't mount your harddrive automatically but Knopix does from the LiveCD.  Maybe that is why you couldn't see your $HOME on the harddrive in Ubuntu.

```
sudo fdisk -l
```

---

### Post by louieb on 2008-03-08
Knoppix uses sudo so prefix you copy command with it.

```
sudo cp whatever whereever
```

---

