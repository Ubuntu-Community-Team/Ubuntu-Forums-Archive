---
title: "Linux file system questions"
date: 2006-11-01
forum: General Help
---

### Post by brad1138 on 2006-11-01
Just have some basic questions on the Linux file structure. Linux installation usually creates 3 partitions. A swap partition, a partition for OS files and the main partition for everything else. Is everything in "/" the "main" partition? Is there a way to look at the 3 partitions to see how big they are (it wasn't shown during installation)? In windows I would always create folders like "Download" and "Programs"(for stored programs). Where would be a good place to put similar folders in the Linux file structure.

Thanks,
Brad

---

### Post by 23meg on 2006-11-01
> Linux installation usually creates 3 partitions. A swap partition, a partition for OS files and the main partition for everything else."Everything else" resides in your home folder, which you can also make into a partition of its own. To understand this, you should familiarize yourself with the concept of mount points. Take a look at [this document]("http://http://www.builderau.com.au/news/soa/10_things_you_should_know_about_every_Linux_installation/0,339028227,339219801,00.htm") for a start. > Is there a way to look at the 3 partitions to see how big they are (it wasn't shown during installation)?Applications / Accessories / Disk Usage Analyzer, or ```
df -h
```> In windows I would always create folders like "Download" and "Programs"(for stored programs). Where would be a good place to put similar folders in the Linux file structure.Your home folder.

---

### Post by evilc on 2006-11-01
If you open Nautlis (file manager) you can make a folder (dir) under what you called the setup should be the first folder (dir) under places, this is usually where all your bits go.
When you make a folder (dir) you can make sub folders within it if you like.
In linux all folders can be the same as dir as in windows. Hope this helps

---

### Post by brad1138 on 2006-11-01
Thanks, that helps a lot. 2 things I am still not clear on. 1st Home isn't all of "everything else" I believe USR is where most 3rd party programs are stored (a bit like 'Program files' in Windows) that must be in "Everything else" also. I guess I don't really need to worry about that, just curious. 2nd /(root) is where "Linux" OS files are (right?). I would have figured it would create a partition big enough to fit all necessary OS files with some extra room for updates etc... but in file browser it is showing 100% usage of "/". Does that mean it is full? I think I am reading it wrong but I don't quite understand. It may just be a setting of DUA but I was hoping to see "hda1 size 5Gb used 3.2 Gb" and hda2 size 35 Gb used 4.3" or something like that. I guess that was 3 Q's :) 

Thanks,
Brad

---

### Post by markus79 on 2006-11-01
Think of your "Home" folder as the "My Documents" in windoze. Its where you keep all your personal files and documents, but not important program and system files. That way you can't do too much damage to the system by staying in your home directory. So when you partition it think of the size you want for your files, music and movies etc.

The /root directory is basically the home directory for the user "root". Its not for os files.

---

### Post by LenzM on 2006-11-01
Here's a decent intro on what all of the different directories are:
[http://doc.vic.computerbank.org.au/tutorials/linuxdirectorystructure/](http://doc.vic.computerbank.org.au/tutorials/linuxdirectorystructure/)

Programs you install with apt-get will be put in the correct location automatically, and they generally put files in many places.  If you are interseted, open up Synaptic, right click on a package you have installed and choose Properties, then look at the 'Installed Files' tab.  If you are installing them by hand (compiling) then the most common place is /usr/local/ or sometimes /opt

Your personal files should all go in /home/username/

---

### Post by podunk on 2006-11-01
Well, actually you could have 50 hard drives with 4 partitions each and they would all be considered as subfolders of
/ (root)
with their own mount points. There is no everything else. :)

The default install in *Dapper* is 2 partitions? One as / and the other as swap. You can customize this during the install of course,  but if you let the installer do it's thing you end up with 2 Ubuntu partitions.

If you show 100% full on / there is very likely a problem. Did you type the command
```
df -h
```
as suggested by 23meg? If that returns 100% on your / I would imagine there is a big problem with your set up.

You write your files in /home/your_name because it's the only directory you can save files to without jumping through hoops.

---

### Post by brad1138 on 2006-11-01
[I]Well, actually you could have 50 hard drives with 4 partitions each and they would all be considered as subfolders of
/ (root)[/I]  

Boy that would be confusing :D 

O.K. that makes more sense. I hadn't tried df -h, now I have, I got 
"**/dev/hda1    size 37G  used 3.4G  avail 32G**". Thats what I was looking for.

Ok I think I know everything now :mrgreen:. Maybe not quite but that answers my questions.

Thanks again,
Brad

---

### Post by matthewstory on 2006-11-01
the "OS" files are mostly in the /boot folder, which is usually a seperate partition, don't know if your setup is this way or not, but the /boot folder is where the kernel image and initrd files are stored.

Generic Comparison of Windows File Structure to Linux:

/bin and /sbin

these folders are like Control Panel -> Utilities, they are your system programs.

/usr/local/ and /usr/bin and /usr/sbin

These three are like program files, that's where the non-system programs go.

/lib and /usr/lib

These are shared libraries for programs, like DLL in windows, /lib are system wide generic libraries, and /usr/lib is for more specific program shared libraries (like the libraries for X-Server).

/home/<username>

Like the \Documents and Settings\Users\<User Name> folder in windows, this has folders like: downloads, Desktop, Documents etc.

/etc

This is a place for configuration files used by linux programs, there isn't really anything like this in windows, as in windows the config files are usually stored with the executable in the program files directory

/media

This is a place for mounting non-permanent media, USB drives, CD-ROM drives etc, don't know exactly where this is in windows, but it's kind of like D:, E:, F: etc.

/dev

This folder holds all your devices files . . . there's really nothing like this in windows i don't think, aside from it's kind of like C: D: etc again, in that your drive devices are in here e.g. /dev/hda, /dev/hda1 etc etc.

/boot

This holds the kernel image, and the grub info, as well as initrd files for grub to initialize a kernel.  This is like a the system partition in windows.

As has been suggested earlier, the way disks are used in linux is much different, and consequently much more powerful than the way it is used in windows.  In linux you have devices that you mount to a point in the file system.  So every folder could be a different hard disk were you to want that.  To say that every device is a subfolder of the root partition is a bit misleading, as the root of the filesystem is just where the root partition is mounted, and then inside the filesystem you can mount other disks to different folders, this doesn't make them equivalent to that folder, it's just that that's where you access them.  This is very different from the LETTER: system in windows, and arguably much more powerful.

Well this has been sufficiently long winded.

---

