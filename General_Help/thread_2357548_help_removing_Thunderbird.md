---
title: "help removing Thunderbird"
date: 2017-04-03
forum: General Help
---

### Post by jakenewomer on 2017-04-03
I have Thunderbird messed up trying to add a second account. I looked up help which told me I had to setup a profile and I told it to go to the deskop. Now I have three thunderbird files on the desktop I cannot get rid of and every time I click on the Tbird icon the desk loads up with files again. I would just like to get rid of it all and start over. It appears as though there is no way to uninstall something with ubuntu.

---

### Post by TheFu on 2017-04-03
User files are not removed when a program is uninstalled.  The user should delete them if that is his/her intention.
There are 2 methods to remove a program from the system that was installed through a package manager.
* remove 
* purge.
```

sudo apt purge thunderbird
```
or```

sudo apt remove thunderbird
```

Any of the package management systems (apt/apt-get/aptitude/synaptic/whatever can do this, just the options are a little different.

According to the manpage for apt -
```
APT(8)                                APT                               APT(8)

NAME
       apt - command-line interface

SYNOPSIS
       apt [-h] [-o=config_string] [-c=config_file] [-t=target_release]
           [-a=architecture] {list | search | show | update |
           install pkg [{=pkg_version_number | /target_release}]...  |
           remove pkg...  | upgrade | full-upgrade | edit-sources |
           {-v | --version} | {-h | --help}}

DESCRIPTION
       apt provides a high-level commandline interface for the package
       management system. 
...
       install, remove, purge (apt-get(8))
...
           Removing a package removes all packaged data, but leaves usually
           small (modified) user configuration files behind, in case the
           remove was an accident. Just issuing an installation request for
           the accidentally removed package will restore its function as
           before in that case. On the other hand you can get rid of these
           leftovers by calling purge even on already removed packages. [B]Note
           that this does not affect any data or configuration stored in your
           home directory.[/B]

```
Clear as mud?  Manpages are an acquired taste, but almost always contain the best description for how things actually work.

So - "purge" removes any system-level configuration files and the programs and libraries installed. These are almost always tiny whereas "remove" leaves those in place and only removes the programs and libraries installed. This is consistent across all the APT-based package management tools.

Over the years, where thunderbird places end-user files has changed a few times. Plus there are other cache files that might be left behind too. Find those with 
```
$ find ~/ -type d -iname \*thunder\*

```

---

### Post by SeijiSensei on 2017-04-03
All your profiles for Thunderbird are stored in /home/username/.thunderbird (notice the leading dot).  If you delete that directory, you'll start afresh, and you won't need to purge Thunderbird itself.
```

cd ~
rm -rf .thunderbird

```
If you use a GUI file manager, you may need to change a setting to see "hidden" files beginning with a dot.

---

### Post by jakenewomer on 2017-04-03
Thank you that got rid of the installation. Do you know how I can get rid of orphaned files on my desktop. I cannot drag them to recycle bin

---

### Post by deadflowr on 2017-04-03
Files on the desktop are in the folder Desktop in the file manager (Files)
just highlight > right click select Trash/rubbish/whatever garbage is for your locale.
Then go to Trash to empty it.

---

### Post by bonestabone on 2017-04-03
I just started a new thread about this, in Debian you can use the package deborphan to find orphaned packages. I don't know the best way to do this in Ubuntu though.

---

### Post by deadflowr on 2017-04-03
orphan files and orphan packages are different things.

---

### Post by jakenewomer on 2017-04-03
Thank you after a reboot they are gone. I don't think I',m cut  out for Linux. I wish any of you who pop up telling people to use Linux when there are complaints about windows would stop. I don't know anyone who would go through what I have to begin using it and I thank you for your help. Maybe what I have is all some people need after all many users just use webmail. I have it setup and have my shared drive and printers working and that is the most progress I've had so far after many attempts over the years. But to simply act like someone can begin using it like windows is cruel. I'm 74 years old and will just stop using a computer when the final choice is windows 10 or apple.

---

