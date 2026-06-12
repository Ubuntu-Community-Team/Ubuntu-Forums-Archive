---
title: "USB removeable memory stick as extention of harddrive"
date: 2008-03-24
forum: General Help
---

### Post by slaabrockband on 2008-03-24
hi forum

 I have 2,5 Gb left on my primary harddrive /dev/sda1. WINE is installed here.
I want to install a game via WINE, that demands 3 Gb space.

I have one 4 Gb USB removeable stick, fat32.

Now, is it possible to make this stick work together with my primary harddrive, so that I can install the
windows game?

Probably I could find out, how to format fat32 to ext3 and mount the USB stick -

But, how do you control the installation of programs, when you have to harddrives to choose between ?

---

### Post by Sam Lars on 2008-03-24
If you install in Wine, it should give you an option of where you want to install it.
Ubuntu should mount the drive, and Wine should be able to find that.
You can't really "add" it to your hard drive, because drives like to be constant, and I don't think it would take it well if 4GB of itself suddenly disappeared. :)

---

### Post by slaabrockband on 2008-03-24
You're clear enough for me - thanks for your answer !    ;)

---

### Post by chemist109 on 2008-03-24
Wine normally stores programs and registry entries in the .wine directory in your home directory.  However, you can tell wine to create a brand new windows "drive" anywhere and then can install programs to it.

Simply create a directory on your removable disk and then run in the console:
```

wineprefixcreate --prefix "/path/to/install/directory"
```

This will create wine's fake registries and directory structures.  Next, you need to set the environment variable WINEPREFIX
```

export WINEPREFIX="/path/to/install/directory"
```

Now, you can configure the environment for that "drive" using:

```
winecfg
```

Finally, run the installer for the game:

```
wine "/path/to/installationprogram.exe"
```

When you are finished installing the program you can run it with:

```
wine "/path/to/executable.exe"
```

You MUST set the WINEPREFIX variable every time you want to run the program.  I usually create a shell script to set all that up and then create a launcher for that script.  Here's an example script for MS Word 2003:

```
!/usr/bin/env bash
# script to start MS Word 2003

cd
export WINEPREFIX="/home/username/msoffice2003"
wine "/home/username/msoffice2003/drive_c/Program Files/Microsoft Office/OFFICE11/WINWORD.EXE"
```

An added bonus is that your removeable drive will work with any Linux machine with wine installed.  Just plug in the drive, set the WINEPREFIX variable to point to the install directory on the drive and then run the executable using wine.

---

