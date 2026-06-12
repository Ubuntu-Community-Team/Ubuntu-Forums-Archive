---
title: "Can't get rid of broken packages"
date: 2006-08-25
forum: General Help
---

### Post by WhizCas on 2006-08-25
I was trying to install XGl + Compiz for my ati card. The installation guide told me to get compiz and so I did. But when in tried to install compiz vanilla after that it went wrong. When trying to fix it I get these errors:

--------------------------------
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  compiz-vanilla-aiglx: Depends: compiz-vanilla (>= 0.0.12) but it is not going to be installed
                        Depends: compiz-vanilla-gnome (>= 0.0.12) but it is not going to be installed
  libglitz-glx1: Depends: libglitz1 (>= 0.5.1+cvs20060213) but it is not going t o be installed
  xserver-xgl: Depends: libglitz1 (>= 0.5.1+cvs20060213) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a s olution).
-----------------------
after 'apt-get -f install' =

------------------------
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  compiz-vanilla compiz-vanilla-gnome
Recommended packages:
  compiz-vanilla-kde
The following NEW packages will be installed:
  compiz-vanilla compiz-vanilla-gnome
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/417kB of archives.
After unpacking 2343kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 99049 files and directories currently installed.)
Unpacking compiz-vanilla (from .../compiz-vanilla_0.0.13+cvs20060822_i386.deb) . ..
dpkg: error processing /var/cache/apt/archives/compiz-vanilla_0.0.13+cvs20060822 _i386.deb (--unpack):
 trying to overwrite `/usr/bin/compiz', which is also in package compiz-core
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking compiz-vanilla-gnome (from .../compiz-vanilla-gnome_0.0.13+cvs20060822 _i386.deb) ...
dpkg: error processing /var/cache/apt/archives/compiz-vanilla-gnome_0.0.13+cvs20 060822_i386.deb (--unpack):
 trying to overwrite `/usr/share/gconf/schemas/compiz.schemas', which is also in  package compiz-plugins
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/compiz-vanilla_0.0.13+cvs20060822_i386.deb
 /var/cache/apt/archives/compiz-vanilla-gnome_0.0.13+cvs20060822_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
----------------------------

At the moment I just wanna get rid of these errors so I can install other packages. Anyone has any idea howto?

---

### Post by ayoli on 2006-08-25
i had a similar problem with a compiz/cgwd update last days, i had to run apt-get install -f twice or three times.
regards.

---

### Post by WhizCas on 2006-08-25
I have run it now about five times, but I still get the 'E: Sub-process /usr/bin/dpkg returned an error code (1)'-error. Maybe there is a stronger command to just remove the packages? I already treid apt-get remove...

---

### Post by Ramses de Norre on 2006-08-25
Aptitude is better in resolving dependencies, you might want to try that.

---

### Post by ayoli on 2006-08-25
i don't really like aptitude, for a complete frontend as aptitude i prefer a gui app like synaptics.
btw the error WhizCas have could be overridden by installing packages concerned with :
```
dpkg -i package_name --force-overwrite
```
regards.

---

### Post by Ramses de Norre on 2006-08-25
You can use aptitude as a command line program just like apt-get with almost the same syntax, I don't like the gui of it neither but on command line it's definitely better as apt-get.

---

### Post by WhizCas on 2006-08-25
Both thanks for your response. In aptitude I get a error almost a like and I dont see how dpgk will help.. Which package must I use to overwrite, the vanilla .deb?

---

### Post by blackmh on 2006-08-25
Try with "sudo dpkg --force-all -i /var/cache/apt/archives/name_of_package.deb"
then apt-get install -f

---

### Post by ayoli on 2006-08-25
> **WhizCas said:**
> Both thanks for your response. In aptitude I get a error almost a like and I dont see how dpgk will help.. Which package must I use to overwrite, the vanilla .deb?

the one which return an error:
/var/cache/apt/archives/compiz-vanilla_0.0.13+cvs20060822_i386.deb
/var/cache/apt/archives/compiz-vanilla-gnome_0.0.13+cvs20060822_i386.deb

after run apt-get install -f (or aptitude equivalent)
regards.

---

### Post by ayoli on 2006-08-25
> **Ramses de Norre said:**
> You can use aptitude as a command line program just like apt-get with almost the same syntax, I don't like the gui of it neither but on command line it's definitely better as apt-get.

ok, i'll read doc a bit, then give a try ;)

---

### Post by WhizCas on 2006-08-25
Well the installer wants me to install the vanilla packages. At the moment I just want to install the packages and move on without errors. Isnt there a way to just install them with either synaptics either aptitude?

---

### Post by WhizCas on 2006-08-26
Does anybody know how to just force delete this packages?

---

### Post by Ramaddan on 2006-08-26
Hi,

I had a similar problem getting rid of a package before,
and I had to do it manually, and the solution was posted [here]("http://www.ubuntuforums.org/showpost.php?p=1070911&postcount=7"):
> 
Hi,
I don't know if anyone replied to this problem, or if anyone needs help with it, but I figured how to fix such a problem without having to re-install Ubuntu again.

I ran into the same problem, and saw some other people run into it,
but I did not find a solution, so I kept following through the original files, and I figured how to fix the problem.

First the problem occured for me when I tried to use "alien" to change
files from rpm to deb files.

So after fooling around with all the apt-get commands, and dpkg commands,
to no avail, I finally decided to try my luck manually.

1. I opened up the deb files with Archive Manager, to have an idea of where
the files install, and followed through and saw where all the files are,
and uninstalled them.

2. Also make sure you read the files in the control zip file within the deb package with gedit (or other editor), and find out where the files where
installed.

3. Make sure all installed files and folders are deleted.
Some files will require root pass, so be careful you don't delete other files and folders.

4. After making sure that all files and folders are deleted.

- Check "/var/packages" to see if there are any related folders
and delete them.

5. The most important:
- In order to remove package info from system, go into "/var/lib/dpkg/info", and delete all files associated with package and delete them.

6. Now go into a terminal and type:
- sudo dpkg -r --force-remove-reinstreq <package name> (without brackets)

- Then, sudo dpkg --purge <package name> (without brackets)

7. Update repositories with: sudo apt-get update

And hope that you're done, and it works.

This thread is a bit old, but I did not find a reply anywhere, so I thought to myself that this might help some people.

Hope this helps.

---

