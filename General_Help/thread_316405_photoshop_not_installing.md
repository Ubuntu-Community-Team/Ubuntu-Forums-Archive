---
title: "photoshop not installing"
date: 2006-12-09
forum: General Help
---

### Post by Magiczero on 2006-12-09
hi

I am trying to get photoshop 7 on ubuntu using wine but when i click on setup.exe on the cd i get this error:

> The filename "Setup.exe" indicates that this file is of type "executable". The contents of the file indicate that the file is of type "DOS/Windows executable". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "DOS/Windows executable", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file. 

how do I install it on my system?

Do I need to type stuff in terminal?

Thanks

---

### Post by meng on 2006-12-09
Go to terminal:
cd /media/cdrom
wine Setup.exe

BUT
don't be surprised if photoshop 7 doesn't run too well in wine. Works for some I think, but others have problems installing/running.

---

### Post by bugz0r on 2006-12-10
Why does it not work. Imageready opens and works fairly well, but Photoshop itself is not even opening.

---

### Post by meng on 2006-12-10
> **bugz0r said:**
> Why does it not work. Imageready opens and works fairly well, but Photoshop itself is not even opening.
The easy answer to this question is that wine is not Windows. Not everything that works in Windows will work with wine. If you're heavily dependent on Photoshop, I suggest a free trial of Crossover Office with a view to paying subsequently if it works.

---

### Post by sadalmelik57 on 2006-12-10
Photoshop is a fine program, to be sure, but have you tried GIMP?  The free photo editor that comes with Ubuntu is powerful, but truthfully users who are accustomed to Photoshop often don't like the interface.  For them there is a GimpShop interface that makes it seem more like Photoshop.  You can find more about it in these forums by searching for GimpShop.

---

### Post by Magiczero on 2006-12-10
hi

When i type >  cd ~
wine /media/cdrom/Setup.exe I am getting an error that says:  you don't have enough disk space, I am trying to run photoshop 7.  Can anyone help me here?

Thanks

---

### Post by taurus on 2006-12-10
You don't have enough disk space!!!  Do you have enough disk space and by the way, you are not running it; you are trying to install it.  Therefore, you probably need to run it with sudo though...

```
df -h  <-- to view your disk space
sudo wine /media/cdrom/Setup.exe  <-- to install it
```

---

### Post by Shay Stephens on 2006-12-10
> **Magiczero said:**
> hi

When i type  I am getting an error that says:  you don't have enough disk space, I am trying to run photoshop 7.  Can anyone help me here?

Thanks

I install it more directly with (no sudo needed to install by the way):

```
wine /media/cdrom0/Photoshop/Setup.exe
```

I have noticed two things that make a difference in running PS7 once it is installed.  Edit your xorg.conf file to comment out the wacom tablet info if you don't have a tablet.  

```
gksudo gedit /etc/X11/xorg.conf
```

And getting the save for web to work by running PS7 this way (with back slashes):

```
wine "c:\program files\adobe\Photoshop 7.0\Photoshop.exe"
```

Now having said that, do make sure you have enough disk space to install PS7.

---

### Post by Rodneyck on 2006-12-12
Also, look for a fork called Photoshop (comes with Imageready) CS2 portable. It works under WINE. There is also Illustrator CS2 portable...enough said.

---

