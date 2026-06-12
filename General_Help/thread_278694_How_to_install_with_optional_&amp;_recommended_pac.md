---
title: "How to install with optional &amp; recommended packages from terminal"
date: 2006-10-16
forum: General Help
---

### Post by calvinthomas on 2006-10-16
I am trying to write a script for if I ever need to reinstall, its not a very advanced script (it opens a text document for some things that are harder to script), installs software, upgrades computer, runs automatix and restarts, however what i'd really like to do is install the software with all its recommended packages and/or all optional packages, is there a way to do this from the terminal?

Calv

---

### Post by PriceChild on 2006-10-16
There's a command to list all installed packages, which you could just copy and paste after "sudo apt-get install" to do the job for you.

Trying to find it...

Check out this: [http://www.arsgeek.com/?p=564](http://www.arsgeek.com/?p=564)

---

### Post by moore.bryan on 2006-10-16
[I]```
sudo aptitude install --with-recommends PACKAGE_NAME
sudo aptitude install --with-suggests PACKAGE_NAME
```[/I]

---

### Post by calvinthomas on 2006-10-17
Thanks but the --with-suggests command doesn't work, also, would something like this work:

```
sudo aptitude install --with-recommends <package 1> <package 2> <package 3>....
```

Would that do the recommended for all of the packages or just the first package.

Finally could I do:

```
sudo aptitude install --with-recommends --with-suggests <package 1> <package 2> .....
```

To install all recommended and all suggested for all the packages? Obviously with the with suggests command corrected.

Calv

---

### Post by moore.bryan on 2006-10-17
> **calvinthomas said:**
> Thanks but the --with-suggests command doesn't work,
*really?  does it give you an error?*
> also, would something like this work:
```
sudo aptitude install --with-recommends <package 1> <package 2> <package 3>....
```Would that do the recommended for all of the packages or just the first package.
*that would handle all of the packages...*
> Finally could I do:
```
sudo aptitude install --with-recommends --with-suggests <package 1> <package 2> .....
```
To install all recommended and all suggested for all the packages? Obviously with the with suggests command corrected.
[I]as far as i know that should work...
i'm also a little confused why --with-suggests doesn't work... did you try it on a program you know has suggested packages?  it could be when there are no suggested packages, it just stops.
[/I]

---

### Post by calvinthomas on 2006-10-17
see next post

Calv

---

### Post by calvinthomas on 2006-10-17
The actual error I get from --with-suggests is:

```
calvin@Calvin:~$ sudo aptitude install --with-suggests kile
aptitude: unrecognized option `--with-suggests'
aptitude 0.4.1
Usage: aptitude [-S fname] [-u|-i]
       aptitude [options] <action> ...
  Actions (if none is specified, aptitude will enter interactive mode):

 install      - Install/upgrade packages
 remove       - Remove packages
 purge        - Remove packages and their configuration files
 hold         - Place packages on hold
 unhold       - Cancel a hold command for a package
 markauto     - Mark packages as having been automatically installed
 unmarkauto   - Mark packages as having been manually installed
 forbid-version - Forbid aptitude from upgrading to a specific package version.
 update       - Download lists of new/upgradable packages
 upgrade      - Perform a safe upgrade
 dist-upgrade - Perform an upgrade, possibly installing and removing packages
 forget-new   - Forget what packages are "new"
 search       - Search for a package by name and/or expression
 show         - Display detailed information about a package
 clean        - Erase downloaded package files
 autoclean    - Erase old downloaded package files
 changelog    - View a package's changelog
 download     - Download the .deb file for a package
 reinstall    - Download and (possibly) reinstall a currently installed package

  Options:
 -h             This help text
 -s             Simulate actions, but do not actually perform them.
 -d             Only download packages, do not install or remove anything.
 -P             Always prompt for confirmation or actions
 -y             Assume that the answer to simple yes/no questions is 'yes'
 -F format      Specify a format for displaying search results; see the manual
 -O order       Specify how search results should be sorted; see the manual
 -w width       Specify the display width for formatting search results
 -f             Aggressively try to fix broken packages.
 -V             Show which versions of packages are to be installed.
 -D             Show the dependencies of automatically changed packages.
 -Z                 Show the change in installed size of each package.
 -v             Display extra information. (may be supplied multiple times)
 -t [release]   Set the release from which packages should be installed
 -q             In command-line mode, suppress the incremental progress indicators.
 -o key=val     Directly set the configuration option named 'key'
 --with(out)-recommends Specify whether or not to treat recommends as
                strong dependencies
 -S fname: Read the aptitude extended status info from fname.
 -u      : Download new package lists on startup.
 -i      : Perform an install run on startup.

                  This aptitude does not have Super Cow Powers.

```

Could edgy be the problem?

Calv

---

### Post by moore.bryan on 2006-10-17
> **calvinthomas said:**
> Could edgy be the problem?
*i can't imagine it is... aptitude's man is pretty specific about the commands you can call.  my suggestion would be to uninstall aptitude and then reinstall it.  both --with-recommends and --with-suggests are listed as options in the man.  if all else fails, though, blame edgy... ;-)*

---

### Post by calvinthomas on 2006-10-17
Still doesn't seem to work, its not a big problem really, with recommends is more useful, still until I know better I'll blame edgy!

Calv

---

### Post by moore.bryan on 2006-10-17
*launchpad has some aptitude-edgy bugs; one suggestion was to grab apt_0.6.45 from the debian unstable repos and that seemed to fix some issues.  don't know if it'll help, though.  have you gotten --with-recommends to work?*

---

### Post by calvinthomas on 2006-10-17
> **moore.bryan said:**
> *launchpad has some aptitude-edgy bugs; one suggestion was to grab apt_0.6.45 from the debian unstable repos and that seemed to fix some issues.  don't know if it'll help, though.  have you gotten --with-recommends to work?*

Yes with recommends is working perfectly! That was just me being stupid and typing:

```
sudo apt-get install --with-recommends
```

instead of

```
sudo aptitude install --with-recommends
```

---

### Post by calvinthomas on 2006-10-17
> **PriceChild said:**
> There's a command to list all installed packages, which you could just copy and paste after "sudo apt-get install" to do the job for you.

Trying to find it...

Check out this: [http://www.arsgeek.com/?p=564](http://www.arsgeek.com/?p=564)

Thanks for the link, that looks really really good! I've got two different methods now, just in case one of them happens not to work! I'll use this method as the first though as its, neater, tidier and better!

Calv

---

