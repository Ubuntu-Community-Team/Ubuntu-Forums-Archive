---
title: "Installed apps not able to be located"
date: 2014-02-21
forum: General Help
---

### Post by ibates on 2014-02-21
Ubuntu 12.04 LTS updated.

Recently, following failure of an earlier 12.04 LTS updated system, I have installed the latest versions of 12.04 LTS on a separate HDD from which I now manually boot whilst awaiting the stable release of 14.04 LTS in April.

All previous problems have gone, but a new one has developed.

Some, but not all, apps which I am installing, such as my Canon MP640 Printer/Scanner Debian package (which is not available through either Synaptic or the Ubuntu Software Centre, but which was nonetheless installed using the Ubuntu Software Centre), appears to have been installed, but I cannot find it - anywhere.  Even reverting back to the Ubuntu Software Centre (USC), it is not shown as being installed.  Neither is it in Synaptic.  But it is installed, because I can select it and it runs perfectly, from terminal.  Luckily I remebered the command name to run it

There are a few other examples as well.  All have been installed either in Synaptic, or in the USC, but there is no sign of them thereafter.

Perhaps they are able to be run from terminal, but I have no idea what the installed command is to run them.  In any event, to have to revert to terminal to run installed apps seems a very retrograde step, particularly when hitherto, there was always an app icon requiring a single click to run the app.

Any solutions please?

---

### Post by Impavidus on 2014-02-21
To get the name of a package that provided a known command:```
dpkg --search $(which command)
```Example:```
$ dpkg --search $(which convert)
imagemagick: /usr/bin/convert
``` tells us the convert command is located in /usr/bin/convert and is provided by the package imagemagick. Works for any installed .deb. Software centre may be a little difficult to use here, but synaptic should list the package if you installed it.

---

### Post by buzzingrobot on 2014-02-21
Well, that's a bit confusing.  Applications that weren't installed were installed but you can't find them but you can run them.

OK.

Programs like Synaptic and Ubuntu Software Center have no packages "in" them.  They are front ends to access the Ubuntu repositories, i.e., servers.

Programs for Ubuntu that want to create an icon that will be available to the user need to place what's called a .desktop file in /usr/share/applications.  If they do not do this, the icon won't be displayed.

Meanwhile, the actual executable file -- the file that runs -- is probably in /usr/bin.  That directory is in your path and that's why it runs when you enter its name in a terminal.

That said, user apps from Ubuntu repositories typically create .desktop files.  You can also install "foreign" apps from other sources, like third-party printer packages, with Software Center or Synaptic. But, if the developers of that package did not include code to create a .desktop file, there won't be one.

---

### Post by Dennis N on 2014-02-21
An easy way find the path to a program's executable file, or the path to a script, is to use the **type** or **which** command:

Three examples. The third one is a custom script.

```
dmn@Sydney:~$ type firefox
firefox is /usr/bin/firefox
dmn@Sydney:~$ which firefox
/usr/bin/firefox
dmn@Sydney:~$ type audacious
audacious is /usr/bin/audacious
dmn@Sydney:~$ type mount-lubuntu
mount-lubuntu is /home/dmn/bin/mount-lubuntu
dmn@Sydney:~$ which mount-lubuntu 
/home/dmn/bin/mount-lubuntu

```

---

### Post by ibates on 2014-02-21
Thanks for that Buzz....  You reckon that sounds confusing, try it from this end.

But what it says is correct.  I had the Deb package which I clicked on to install.  The dialogue came up to the effect, "open in Ubuntu Software Centre" which i clicked on.  Up came the USC with a short description of the package, and an "install" button.  Clicked on that and program was "installed".  I then went to Dash to use the program, and no icon.  Darn it!  It musn't have insatalled properly, so back to USC to reinstall.  You guessed it, nowhere to be found.

The same happened with a couple of other program installations in Synaptic also.

I know that at least one of them, my Canon MP640 Scanner has been installed, because I remember that the command line to use in terminal was *scangearmp* which, upon entering in terminal ran the program beautifully.

File system search also finds various places where bits of the program appear to be installed, but I do not know what bit is which, and so that doesn't help very much.

I guess that is the problem with being a user and not an expert.

But I certainly will re-read what you have written and see if I can sort something out from that.

Thanks again.

---

### Post by ibates on 2014-02-22
G'day Dennis.  I will give that a go.  But it does seem rather a retrograde step to have to revert to command line code to run a program in a modern system with an otherwise excellent GUI, particularly when the system which failed on me just a month ago had all the progam icons without my having had to do anything.  With the same packages installed I might add.  I had them all backed up so simply used them again - but - well you know the problem.

---

### Post by ibates on 2014-02-22
OK.  I have had a re-read and checked the /ur/share/application/.desktop.  Plenty of icons there, but not for the "missing" programs.  In all cases, previous installations by exactly the same methods, in 12.04 LTS updated, have yielded icons in Dash first time every time.  But not in this recent installation.

As I said before.  Same packages, merely different installation procedure.  As I recall previously, there was a Debian Install option when clicking on the package, but not any more, despite my having installed *Debian installer*.

I just don't understand what is or is not going on.

---

### Post by Dennis N on 2014-02-22
> I had them all backed up so simply used them again - but - well you know the problem. 

If these were .deb files you saved from the earlier 12.04, you might try uninstalling one of the problem ones if right clicking on the .deb gives that option. Then install with Synaptic from the repositories instead.  I don't know if this would make a difference, but may be worth a try on one of them if you are given the option. Certainly something strange going on.

(If you installed with gdebi, right click and opening the .deb shows an uninstall button. Sounds like you didn't use it, however. If you used the software center, I am not familiar how it would be done in that case. Sorry.)

Good luck.

---

### Post by Impavidus on 2014-02-22
In synaptic, click "status", then "installed (obsolete or manually installed)". It should list your installed .debs not coming from a repository.

---

### Post by ibates on 2014-02-24
Unfortunately, the installed apps were not listed in either Synaptic or Ubuntu Software Centre.

However, all is now solved, thank you all.  Installing Gdebi Installer fixed the problem, and all I had to do was install that app and reinstall the apps and vilola!  There they all were.

---

### Post by buzzingrobot on 2014-02-24
> **ibates said:**
> Unfortunately, the installed apps were not listed in either Synaptic or Ubuntu Software Centre.

However, all is now solved, thank you all.  Installing Gdebi Installer fixed the problem, and all I had to do was install that app and reinstall the apps and vilola!  There they all were.

The packages were probably not installed correctly or completely the first time. (This -- "...which is not available through either Synaptic or the Ubuntu Software  Centre, but which was nonetheless installed using the Ubuntu Software  Centr.." -- suggests it was a package from somewhere other than the Ubuntu repos, which opens, at least, the possibility of a fault in the package.

---

