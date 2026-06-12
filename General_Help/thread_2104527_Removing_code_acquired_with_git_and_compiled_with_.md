---
title: "Removing code acquired with git and compiled with make"
date: 2013-01-13
forum: General Help
---

### Post by cscj01 on 2013-01-13
System: Ubuntu 12.04 x64 with Gimp 2.8.2 installed.

I recently installed source for babl, gegl, and gimp with git into a folder in my home directory.  I then compiled using ./config, make and make install to another folder in my home directory.

Now that I have checked it out, I am trying to decide whether I want to remove all code and packages installed as a result of the preceding operations or keep everything and update it as new functionality becomes available.

I have several questions about how to accomplish either of these.

If I decide to remove:

[LIST=1]
[*]Is there a command or commands to automatically get rid of all the files created by the ./config, make, and make install commands?
[*]Is there a command to remove all the git acquired source?
[*]Should I remove all the dev libs I installed as prereqs to compiling babl, gegl, and gimp?
[/LIST]
If I decide to keep:
[LIST=1]
[*]Is there an easy way to do this?
[*]If so, what are the steps required?
[/LIST]
As usual, any help will be appreciated.

---

### Post by cscj01 on 2013-01-15
bump

---

### Post by mc4man on 2013-01-15
> **cscj01 said:**
> System: Ubuntu 12.04 x64 with Gimp 2.8.2 installed.

I recently installed source for babl, gegl, and gimp with git into a folder in my home directory.  I then compiled using ./config, make and make install to another folder in my home directory.

Now that I have checked it out, I am trying to decide whether I want to remove all code and packages installed as a result of the preceding operations or keep everything and update it as new functionality becomes available.

I have several questions about how to accomplish either of these.

If I decide to remove:

[LIST=1]
[*]Is there a command or commands to automatically get rid of all the files created by the ./config, make, and make install commands?
[/LIST]

If you didn't alter the source folders for those 3 you could, - 
cd to each folder in a terminal & run
sudo make uninstall 
or 
Considering they all were installed to the same prefix (folder), likely /opt/gimp-2.9, then just delete that folder (gimp-2.9) as root.

---

### Post by cscj01 on 2013-01-15
> **mc4man said:**
> If you didn't alter the source folders for those 3 you could, - 
cd to each folder in a terminal & run
sudo make uninstall 
or 
Considering they all were installed to the same prefix (folder), likely /opt/gimp-2.9, then just delete that folder (gimp-2.9) as root.

Thank you.  That helps with the option of removing the installs.

---

