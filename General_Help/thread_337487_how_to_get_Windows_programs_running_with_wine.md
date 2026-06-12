---
title: "how to get Windows programs running with wine?"
date: 2007-01-13
forum: General Help
---

### Post by presbp on 2007-01-13
I installed wine and the wine-dev packages and went to winecfg.  I went to program files (I have the Windows partition mounted as read-only under home/media/windows) and chose the quicktimeplayer.exe set it to Xp applied and then hit ok.  I didn't see any quicktime icons or anything so I went to program files to click on the quicktimeplayer.exe and when I did it says there isn't a suitable application to handle this type of file..  How do I get Windows programs working right?

---

### Post by alecjw on 2007-01-13
To run wine, the command is wine <filename> eg wine "/windows/Program Files/QuickTime/quicktime.exe"

I think you might need the wine pacakge as well as wine-dev, and the hard drive will proably need to be RW.

Also bear in mind that not all programs run in wine. if you arent sure, check on [http://appdb.winehq.org](http://appdb.winehq.org)

---

### Post by Edho on 2007-01-13
No specialist, try to help.

Lets think wine is good installed...
Now there is a fake-windows-envirmont in the linux-system.

You have downoaded a freeware program let us say.... Iview-install.exe

In a terminal give the command :

wine Iview-install.exe

Follow the install-instructions like you do in Windows...
When the install was a succes , the program.exe is in your directory you choosed

Now you can make a launcher with the command:

wine fullpath-to-the-target
Example
 wine /home/eddy/.wine/drive_c/windows/programfiles/iview/i_view32.exe

---------------------
Wine will also work with some allready installed programs in the real windows-envirmont..

Then you can directly make a launcher ...wine fullpath-to-it

But keep in mind that it will not work good if the program needs to write to its .Ini-file for example keeping settings.
Because your ntfs-drive is read-only.

---

### Post by Enverex on 2007-01-13
> **Edho said:**
> No specialist, try to help.

Lets think wine is good installed...
Now there is a fake-windows-envirmont in the linux-system.

You have downoaded a freeware program let us say.... Iview-install.exe

In a terminal give the command :

wine Iview-install.exe

Follow the install-instructions like you do in Windows...
When the install was a succes , the program.exe is in your directory you choosed

Now you can make a launcher with the command:

wine fullpath-to-the-target
Example
 wine /home/eddy/.wine/drive_c/windows/programfiles/iview/i_view32.exe

---------------------
Wine will also work with some allready installed programs in the real windows-envirmont..

Then you can directly make a launcher ...wine fullpath-to-it

But keep in mind that it will not work good if the program needs to write to its .Ini-file for example keeping settings.
Because your ntfs-drive is read-only.

Grrr. Don't do that. If you're going to make a link then you need to use a path like:
wine "C:\Program Files\iview\i_view32.exe"
(C: is your ~/.wine/drive_c folder)
as running with the full Unix path doesn't always work and normally programs tend to bail due to not finding files (this applies to installers with auxiliary files too).

The application list in wincfg isn't for running applications, it's for setting a specific windows version and/or DLL overrides, so that wasn't what you wanted.

Also note that applications are considerably less likely to work when run from a Windows install rather than installed in Wine itself and even further unlikely to work if the drive isn't writable.

---

### Post by Fitzy_oz on 2007-01-18
> **presbp said:**
> I installed wine and the wine-dev packages and went to winecfg.  I went to program files (I have the Windows partition mounted as read-only under home/media/windows) and chose the quicktimeplayer.exe set it to Xp applied and then hit ok.  I didn't see any quicktime icons or anything so I went to program files to click on the quicktimeplayer.exe and when I did it says there isn't a suitable application to handle this type of file..  How do I get Windows programs working right?

For starters the version thats bundled with edgy is now out of date by 7 releases, First and foremost goto winehq.org and follow the instructions for getting the latest version.  As for starting programs, you should be able to just right click on them and say open with wine.  Thi should do it.  As for the quicktime player, same applies, use the right click and open with wine function to start the installer and install it as you would under windows.

---

