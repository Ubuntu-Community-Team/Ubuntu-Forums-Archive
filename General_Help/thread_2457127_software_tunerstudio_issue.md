---
title: "software tunerstudio issue"
date: 2021-01-26
forum: General Help
---

### Post by mkeating on 2021-01-26
I'm having  issues running tunerstudio software on Ubuntu.    The readme.txt tells you to unpacked in a directory and then run TunerStudio.sh file to open the program.  But it has issues.  I tried installing the program a second time using snap on a different VM, same problem.    The program does open  when i enter "./tunerstudio" and creates a graphical icon.  But the the icon doesn't work and when i  type "tunerstudio" into the terminal i get i get the below error:

matt@GnomeBasic:~/snap/tunerstudio/common/TunerStudioMS$ tunerstudio 
ln: failed to create symbolic link '/home/matt/snap/tunerstudio/138/TunerStudioMS': File exists


I also got these errors when i first installed:

matt@GnomeBasic:/bin$ tunerstudio
Gtk-Message: 09:07:25.705: Failed to load module "canberra-gtk-module"
/snap/tunerstudio/138/launch: line 35: cd: /home/matt/snap/tunerstudio/138/TunerStudioMS: Too many levels of symbolic links
matt@GnomeBasic:/bin$ tunerstudio
ln: failed to create symbolic link '/home/matt/snap/tunerstudio/138/TunerStudioMS': File exists


matt@GnomeBasic:~/snap/tunerstudio/common/TunerStudioMS$ bash TunerStudio.sh
This script must be located in the TunerStudio directory. To be able
to launch without path create a symlink of this script to a directory in PATH.

Example: ln -s /home/john_doe/TunerStudioMS/TunerStudio.sh /usr/local/bin

---

