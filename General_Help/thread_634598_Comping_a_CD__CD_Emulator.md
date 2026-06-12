---
title: "Comping a CD / CD Emulator"
date: 2007-12-07
forum: General Help
---

### Post by dethredic on 2007-12-07
So, as the title says, what is some good software that will let me
a) Copy a CD
b) Mount an .iso (Like deamon tools)

---

### Post by Happy_Man on 2007-12-07
To Copy a CD, I suggest Brasero for GNOME, and K3b if you are on KDE. As for B, I think that you can mount it as you would any other drive in Linux, though I'm not completely sure about this, as I've never really had to.

---

### Post by DirtDart on 2007-12-08
> **dethredic said:**
> So, as the title says, what is some good software that will let me
b) Mount an .iso (Like deamon tools)

I use (and recommend) AcetoneISO2.

AcetoneISO2 bills itself as "The CD/DVD image manipulator for Linux"

[http://www.acetoneteam.org/central.html]("http://www.acetoneteam.org/central.html")


To see what it looks like: [http://www.kde-apps.org/content/show.php/AcetoneISO2?content=44805]("http://www.kde-apps.org/content/show.php/AcetoneISO2?content=44805")

---

### Post by CatKiller on 2007-12-08
I've had no problem at all with the default cd burner that comes with GNOME - just right-click on the cd icon on your Desktop - and I just use the well-known **mount** command to mount cd images where I want. But then I'm not very fussy.

Edit: And if I'm making a compilation, I generally use Rhythmbox, which also comes with GNOME.

---

### Post by bulletxt on 2007-12-08
Yeah if you need to work with different image formats AcetoneISO2 is the best solution. it just works ;)

for burning of course k3b is the best solution as it has the most features. of course brasero is also ok for a "normal" user.

---

### Post by dethredic on 2007-12-08
Ok, I installed AcetoneISO2, and it let me easily copy the CD, but how do i mount it?

What is the mount command?

---

### Post by bulletxt on 2007-12-08
how? with AcetoneISO2! just open it the first tab has the mount function!

---

### Post by dethredic on 2007-12-08
*doh* Thanks,

Can I make wine recognize this somehow? So I can play my games on wine with no CD?

---

### Post by UK-Wobbie on 2007-12-08
> **dethredic said:**
> *doh* Thanks,

Can I make wine recognize this somehow? So I can play my games on wine with no CD?

I can give you a good ISO Mount tool what will Mount any ISO.. ;)
Like DVD/CD.

You need to download two files what is called "[Mount]("http://www.debianadmin.com/images/iso/mount.sh")" and "[Unmout]("http://www.debianadmin.com/images/iso/unmount.sh")" Put the two files on to your desktop! 

(Open Terminal - Put in scripts)

Then you need the two link script codes :)

1st
```

sudo chmod +x /home/user/Desktop/mount.sh
sudo chmod +x /home/user/Desktop/unmount.sh

```


2st
```

sudo mv /home/user/Desktop/mount.sh ~/.gnome2/nautilus-scripts/
sudo mv /home/user/Desktop/unmount.sh ~/.gnome2/nautilus-scripts/

```


Put in your Username in to "User" :guitar:
When you are done on all this.. Go to a ISO image and right click on it and go to "scripts"
You will have the "Mount" and "Unmount"

Click on Mount and it will ask you for your Password put it in!
It will now Mount the ISO and make a drive for it.. 
Click on the drive on your Desktop and your files will be inside it!

I say you now know on how to unmount :lolflag:;)](*,):mrgreen:

---

### Post by CatKiller on 2007-12-09
> **dethredic said:**
> Can I make wine recognize this somehow? So I can play my games on wine with no CD?

Go into the Drives tab and point a drive at where you've mounted your image.

---

### Post by dethredic on 2007-12-09
Neither of the above two posts will let me play in will let me play in wine. I set the drives to CD, but that doesn't help

---

