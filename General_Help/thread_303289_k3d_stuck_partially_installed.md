---
title: "k3d stuck partially installed"
date: 2006-11-20
forum: General Help
---

### Post by AndrewG on 2006-11-20
I upgraded to Edgy from Dapper earlier today with a bumpy ride. I'm left with k3d complaining that it's partially installed - this happens every time I use Synaptic/apt-get/aptitude. There's a heap of things that aptitude is wanting to do, but this is stopping it from doing so.

> $ sudo apt-get install -f
Password:
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up k3d (0.5.12.0-1ubuntu2) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1348, in ?
    main()
  File "/usr/bin/pycentral", line 1342, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 865, in run
    pkg.read_version_info()
  File "/usr/bin/pycentral", line 535, in read_version_info
    raise PyCentralError, "package has no field Python-Version"
__main__.PyCentralError: package has no field Python-Version
dpkg: error processing k3d (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 k3d
E: Sub-process /usr/bin/dpkg returned an error code (1)Any help greatly appreciated.

---

### Post by HereInOz on 2006-11-20
Hi Andrew,  have you tried going to Synaptic and marking it for a complete removal?  You probably have, but if not, it is worth a go, and then perhaps have another go at it.

Seems like there may be something that is just going back to old corrupt data each time you try to install it.  Have a look in the directory where the error is reporting - usr/bin/pycentral - and see if anything is of use there.  

This has not happened to me, so I have no solution - merely guesses as to where to look next.

---

### Post by AndrewG on 2006-11-20
Doing that gives this error: "E: k3d: subprocess pre-removal script returned error exit status 1"

Thanks anyway.

---

### Post by HereInOz on 2006-11-20
Can you open a terminal and type in "aptitude" and see if you can get that to uninstall it.  Sometimes works better in these situations than Synaptic or apt-get.  If that doesn't work Andrew, it will need a far better person than I to sort it out.

---

### Post by AndrewG on 2006-11-20
> root@sonata:/home/andrew# aptitude remove k3d
Reading package lists... Done
Building dependency tree... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages are unused and will be REMOVED:
  libgts-0.7-5 
The following packages will be REMOVED:
  k3d 
0 packages upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 45.0MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 284080 files and directories currently installed.)
Removing k3d ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1348, in ?
    main()
  File "/usr/bin/pycentral", line 1342, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 932, in run
    pkg.read_version_info()
  File "/usr/bin/pycentral", line 535, in read_version_info
    raise PyCentralError, "package has no field Python-Version"
__main__.PyCentralError: package has no field Python-Version
dpkg: error processing k3d (--remove):
 subprocess pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1348, in ?
    main()
  File "/usr/bin/pycentral", line 1342, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 865, in run
    pkg.read_version_info()
  File "/usr/bin/pycentral", line 535, in read_version_info
    raise PyCentralError, "package has no field Python-Version"
__main__.PyCentralError: package has no field Python-Version
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Removing libgts-0.7-5 ...
Errors were encountered while processing:
 k3d
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
root@sonata:/home/andrew# 

:(

---

### Post by HereInOz on 2006-11-20
Oh dear, perhaps someone of great knowledge will spot this and find a way around it.  Sorry I can't be of more help.

---

### Post by AndrewG on 2006-11-20
Thanks for trying.

EDIT: I could give an Ubuntu developer (one of the well-known ones) the root password to log in with SSH and fix the problem if necessary.

---

### Post by HereInOz on 2006-11-20
That you could, were they willing to do that.  Possibly the only way to get around it.

Good luck - I will stay with my friendly Dapper for a while yet :-)

---

### Post by Hairy_Palms on 2006-11-20
dont know how safe this is ive only tried it with dpkg installed debs i made, delete all the files by hand then apt-get lets you remove it

---

### Post by AndrewG on 2006-11-21
BUMP

Can anybody help?

---

### Post by mcrandello on 2006-11-22
> **AndrewG said:**
> :(
Here's the workaround I got from the IRC channel:

You have to edit the 
/var/lib/dpkg/status file with something like```
sudo pico /var/lib/dpkg/status
```or```
gksudo gedit /var/lib/dpkg/status
```here will be a section like this in there:
```
Package: k3d
Status: deinstall ok installed
Priority: optional
Section: graphics
Installed-Size: 43492
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Architecture: i386
Version: 0.5.12.0-1ubuntu2
Depends: libatk1.0-0 (>= 1.12.1), libboost-date-time1.33.1, libboost-filesystem1.33.1, li$
Suggests: aqsis
Description: 3D modeling and animation system
 K-3D is designed from-the-ground-up to generate motion-picture-quality
<snip>
  - Plugin support through its architecture in ANSI C++ and GTK+.
Original-Maintainer: David Martínez Moreno <ender@debian.org>
Python-Versions: current
```

To fix this simply change the last line in that section to read ```
Python-Version: current
```taking the "s" off of "Python-Versions". Don't make any other changes to the file. In fact I would back it up first just in case. This was a problem with python-central in Edgy, and is fixed in Feisty.

Thanks to crimsun and joejaxx in #ubuntu!

---

### Post by AndrewG on 2006-11-23
You've made my day. Thank you very much.

:)

---

### Post by ZephyrXero on 2006-11-26
After doing what post #11 said, I got this error message:

```
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
```

After just deleting Python-version: current that was there all together, it worked again.

---

### Post by john-the-dodo on 2006-12-01
there is a typo in /var/lib/dpkg/status. Search for a line containing "Python-Versions" and change it to "Python-Version" (i.e. without the S)

Cheers, John

---

### Post by rcasha on 2006-12-19
Here's what I have discovered:

the script /usr/bin/pycentral executes the command "dpkg -s k3d", and then searches through the result for the line "Python-Version:", but the k3d package instead contains the line "Python-Version[COLOR="Red"]s[/COLOR]:"

**[COLOR="Blue"]A quickie solution is this:[/COLOR]**

Using a text-editor, as root, edit the file [FONT="Courier New"]/usr/bin/pycentral[/FONT] (after taking a backup)
Go to line 530, it should say:
[FONT="Courier New"]if line.startswith("Python-Version:"):[/FONT]
If not, look for that line somewhere near this position.

Remove the colon within the string, so that it says:
[FONT="Courier New"]if line.startswith("Python-Version"):[/FONT]

With this change, it should work - you should be able to upgrade/fix k3d. Once that happens, make sure you set the script back to what it was before.

---

### Post by akak8ty on 2006-12-21
I am having the same issue- and the same error scripts as you. I have tried synaptic, aptitude- every command I could find- 
Nothing- nada, zero- zilch.
Stuck on K3d and no sound ](*,)
back to the drawing board

---

### Post by bbarrons on 2006-12-22
I also had the same problem this morning. Thanks for the answer... it fixed it....

---

### Post by akak8ty on 2006-12-22
When I tried that I got I was able to in a round about way get the version- but nothing further. several errors, etc but eventually I got it just  not in the exact manner as indicated.
Last night I went back into aptitude- started reinstalling again at admin
I woke up at 5:00 with prompts to follow (not being very coherent) I followed them- at the end I noted "k3d removed" Good enough. :cool: 

Part A-okay

Now to address my /dev/sequencer which seems to be jammed up. I have been getting the error message:

[B]Could not open /dev/sequencer.
Probably there is another program using it. [/B]

I don't know what could be using it- I've not had sound for a week now. I use mostly KDE for everything (Edgyeft)
I had sound in Konquerer, but not Firefox. 
I've not gotten much help on KDE websites or Kubuntu forums.

---

### Post by alrwseitz on 2006-12-25
If you can go to a terminal prompt and type k3d and run the application.

I had the same problem, But I could run the program from a terminal. 

If all you want to do is get rid of the annoying error. then I would just go to the;

/var/lib/dpkg/status

file and manually remove the section for k3d. This will get rid of the install error everytime you run any of your package managers synapetic, apt-get, aptitude.

Just a reminder you need to do this as root,

I would type gksudo gedit /var/lib/dpkg/status

This worked for me.

---

### Post by akak8ty on 2006-12-25
Thank you- 
I'll be mindful of that in the future. I was having way too many errors, and since I was still running off the 6.06 disk, decided to upgrade and reinstall 6.10
All is well now. :biggrin: 

Vlelen dank

---

### Post by Tyche on 2007-03-10
> **mcrandello said:**
> Here's the workaround I got from the IRC channel:

You have to edit the 
/var/lib/dpkg/status file with something like```
sudo pico /var/lib/dpkg/status
```or```
gksudo gedit /var/lib/dpkg/status
```here will be a section like this in there:
```
Package: k3d
Status: deinstall ok installed
Priority: optional
Section: graphics
Installed-Size: 43492
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Architecture: i386
Version: 0.5.12.0-1ubuntu2
Depends: libatk1.0-0 (>= 1.12.1), libboost-date-time1.33.1, libboost-filesystem1.33.1, li$
Suggests: aqsis
Description: 3D modeling and animation system
 K-3D is designed from-the-ground-up to generate motion-picture-quality
<snip>
  - Plugin support through its architecture in ANSI C++ and GTK+.
Original-Maintainer: David Martínez Moreno <ender@debian.org>
Python-Versions: current
```

To fix this simply change the last line in that section to read ```
Python-Version: current
```taking the "s" off of "Python-Versions". Don't make any other changes to the file. In fact I would back it up first just in case. This was a problem with python-central in Edgy, and is fixed in Feisty.

Thanks to crimsun and joejaxx in #ubuntu!

THANKS!!!!
I've been bugged by this problem and only stumbled on this solution by searching the entire forum for "k3d".  Problem solved and Synaptic is back to behaving itself.  Thanks again.

---

