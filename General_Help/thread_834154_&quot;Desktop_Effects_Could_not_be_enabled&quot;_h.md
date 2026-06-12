---
title: "&quot;Desktop Effects Could not be enabled&quot; help"
date: 2008-06-19
forum: General Help
---

### Post by lotrkev on 2008-06-19
I have tried to Enable Desktop Effects on the latest Ubuntu (8.04), and it tells me that Desktop Effects could not be enabled. I have an "**_NVIDIA RIVA TNT2 Model 64/ Model 64 PRO_**"I went to find help and downloaded a driver, yet it wont open the driver installation.

---

### Post by Exsecrabilus on 2008-06-19
Did you try Envy?
```
sudo aptitude install envyng-gtk
```
*Applications -> System Tools -> EnvyNG*.

---

### Post by lotrkev on 2008-06-19
Envy did work, but now when I try to change the Desktop Effects, it says the following: "The Composite extension is not available".  But it _doesn't_ tell me that "Desktop Effects could not be enabled", so that's a good thing.

---

### Post by Exsecrabilus on 2008-06-19
In Gutsy, I used to tell people to install the package called *xserver-xgl*.
But I don't know now, because in Hardy, effects are enabled _for me_ without that package (I used to need it.)

You could still try it, because the description in Synaptic says "fast transformation of windows." It might boost Compiz.

---

### Post by lotrkev on 2008-06-19
Ok, I'll try it. How do I install it?

---

### Post by Exsecrabilus on 2008-06-19
```
sudo aptitude install xserver-xgl
```

Log out and log in.

---

### Post by lotrkev on 2008-06-19
I installed it, now my graphics are REALLY messed up. is there a way to undo it?

---

### Post by Exsecrabilus on 2008-06-19
```
sudo aptitude uninstall xserver-xgl
```

Restart, then post output (in Terminal) when you run Compiz-Check:

```
wget http://blogage.de/files/4304/download -O compiz-check
```
```
chmod +x compiz-check
```
Post everything written in Terminal after this command:
```
./compiz-check
```

---

### Post by lotrkev on 2008-06-19
When I run the first code, it says: "Unknown command "uninstall"
aptitude 0.4.9
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
 safe-upgrade - Perform a safe upgrade
 full-upgrade - Perform an upgrade, possibly installing and removing packages
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
 -Z             Show the change in installed size of each package.
 -v             Display extra information. (may be supplied multiple times)
 -t [release]   Set the release from which packages should be installed
 -q             In command-line mode, suppress the incremental progress indicators.
 -o key=val     Directly set the configuration option named 'key'
 --with(out)-recommends	Specify whether or not to treat recommends as
                strong dependencies
 -S fname       Read the aptitude extended status info from fname.
 -u             Download new package lists on startup.
 -i             Perform an install run on startup.

                  This aptitude does not have Super Cow Powers.
"

---

### Post by Happy_Man on 2008-06-19
The command should be ```
sudo aptitude remove xserver-xgl
```

---

### Post by lotrkev on 2008-06-19
k. It is uninstalled. Now I ran the second code, and this is what the output was: "--10:58:57--  [http://blogage.de/files/4304/download](http://blogage.de/files/4304/download)
           => `compiz-check'
Resolving blogage.de... 78.46.34.206
Connecting to blogage.de|78.46.34.206|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 27,639 (27K) [application/force-download]

100%[====================================>] 27,639        57.51K/s             

10:58:58 (57.37 KB/s) - `compiz-check' saved [27639/27639]
"

---

### Post by lotrkev on 2008-06-19
I ran the last code, and this was the output:

Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [FAIL]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [FAIL]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Composite manually disabled 

Would you like to know more? (Y/n)

--------------------------------------------
Now after saying yes, it said this:

"It has been detected that the "Composite" option of your /etc/X11/xorg.conf
 has been set to "Disable" 

 Open the file being root and change "Disable" to "Enable"
 Then restart X and try again. "

---

### Post by Exsecrabilus on 2008-06-19
Ehh, sorry, the command should have been:

```
sudo aptitude purge xserver-xgl
```

And for your current problem, I'm not really sure, not a big fan of *xorg.conf*. Sorry. ^_^;;

---

### Post by Forlong on 2008-06-21
I'm sorry but your graphics chip is simply too old.
It's not possible to run Compiz on that at all.

---

