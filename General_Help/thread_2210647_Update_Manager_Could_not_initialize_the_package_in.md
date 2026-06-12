---
title: "Update Manager Could not initialize the package information"
date: 2014-03-11
forum: General Help
---

### Post by sspauld1 on 2014-03-11
Hello and thank you for any help in this matter.

I have ubuntu 12.04 LTS, i recentlly installed xojo (which runs) however i get the following error every time update manger runs.

Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:The package xojo2013r41 needs to be reinstalled, but I can't find an archive for it.'

When i run ubuntu-bug xojo2013r41 i get the following

a@a:~$ ubuntu-bug xojo2013r41

(apport-gtk:2862): Gtk-CRITICAL **: gtk_main_quit: assertion `main_loops != NULL' failed


I can update through the command line (at least i get no errors, i do not see progress with % for downloading and installing) with sudo apt-get update and sudo apt-get upgrade

I tried to remove the software with sudo apt-get remove ...
a:~$ sudo apt-get remove xojo
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package xojo2013r41 needs to be reinstalled, but I can't find an archive for it.
a@a:~$ sudo apt-get remove xojo2013r41
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package xojo2013r41 needs to be reinstalled, but I can't find an archive for it.
a@a:~$ 

i have tried the fixes on the following help's
[http://ubuntuforums.org/showthread.php?t=2210311](http://ubuntuforums.org/showthread.php?t=2210311)

and

[http://ubuntuforums.org/showthread.php?t=2112029](http://ubuntuforums.org/showthread.php?t=2112029)

any suggestions would be appreciated!

Thanks

---

### Post by ian-weisser on 2014-03-11
The system needs data from the actual package you downloaded (or a newly downloaded copy) so it can install, reinstall, or uninstall the proper files.
There are workarounds, but those have costs in inconvenience or leaving bits of installed-but-forgetten code cluttering your system.

Where, exactly, did you get the package from?

---

### Post by sspauld1 on 2014-03-11
I got the package from:
[http://www.xojo.com/](http://www.xojo.com/)

---

### Post by ibjsb4 on 2014-03-12
```
sudo dpkg --purge xojo
```

Will probably clean it up enough, but dpkg will not remove the dependencies that were installed.  To remove leftover packages.

```
sudo apt-get autoremove
```

Autoremove can at times remove needed packages, check what is being removed.

And then clean the cache.

```
sudo apt-get autoclean
```

---

### Post by ian-weisser on 2014-03-12
> **sspauld1 said:**
> I got the package from:
[http://www.xojo.com/](http://www.xojo.com/)

Well, that explains why your system couldn't find it in the Ubuntu Repositories.
And the error means you likely cleaned or autocleaned it from your /var/cache/apt/archive.

ibjsb4's procedure to uninstall is -as usual- excellent and simple.
If dpkg errors on the uninstall, then download the package again. Even for an uninstall. Then try ibjsb4's procedure again.

---

