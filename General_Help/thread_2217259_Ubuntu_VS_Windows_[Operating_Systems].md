---
title: "Ubuntu VS Windows [Operating Systems]"
date: 2014-04-16
forum: General Help
---

### Post by Muhammad_Ahmad_Mujtaba on 2014-04-16
Hello everyone, i am muhammad ahmad mujtaba. Although it has been a week , since i have switched from Windows to Linux [Ubuntu & Debian] but i actually has no concept of their root directories.
I am very good at Windows operating system eg regisrty editing, NTFS partition related problems and softwares stuff etc. 
But
I found Linux much different from Windows to learn and i am very excited to learn as much thing as i can learn about but for now i want to know **what does the directory in which Linux [eg Ubuntu] has been installed, contains what folders and what does they mean.**

During **installation mount point was '/' :**

Fresh Windows Operating system would atleast have following folders in root directory , usually C: drive. [x64 architecture].

**Program Files** [folders where x64 softwares are installed.]
**Program FIles (x86)** [folders where x86 softwares are installed.]
**Users** [ Users accounts ]
**Windows** [operating system files].

and Linux would have [Debian] , where drive name is** 'File System' parallel to C: in Windows**.

[B]bin
boot
dev
etc
home
lib
lib64
lost + found
media
mnt
opt
proc
root
run
sbin
selinux
srv
sys
temp
usr
var
initrd.img
vmlinuz.exe

[/B]I want to know where softwares are installed and short description of all these folder; it will help me understand and operate Linux well.
Thanks to everyone!

---

### Post by stalkingwolf on 2014-04-16
you might want to down load the absolute beginners guide.  here is one location [http://ubuntu-manual.org/downloads]("http://ubuntu-manual.org/downloads").
and getting started with ubuntu from the same location.

There is also a wealth of information and tutorials here[www.psychocats.net/ubuntu/&#8206;]("www.psychocats.net/ubuntu/&#8206;") 
Psychocats also has several tutorials posted on this site but for the life of me i cant recall which forum (only one cup of coffee so far :D)

---

### Post by su:bhatta on 2014-04-16
Well, I cant give you the details of all. Cause never have to deal with all of them !

But 'Home' is where by default the 'Documents, Downloads.Pictures, Videos & Music ' are.
You will find the executable of most of your programs under /usr/bin

And yes, read up that manual posted by stalkingwolf :)

---

### Post by startas on 2014-04-16
Well, i know for sure that there is no standard or good location for all the installed programs, every developer randomly chooses where to install his program. Common locations are /home/user , /opt . Its actually hard to describe what is in all these folders, just see for yourself. As for me, most of these folders are useless or junk, as i dont have really much to do with them, i just sometimes use some specific locations, like video drivers location, cache, temp folders. Linux is even more messy in its folders and files structure than windows. You know, installing programs, uninstalling programs -> tons of junk is left to delete it manually and so on...

---

### Post by Muhammad_Ahmad_Mujtaba on 2014-04-16
It seems i have manually crave out the folders to check the installation of softwares; but what about builtin softwares? like mozilla firefox?

---

### Post by war28 on 2014-04-16
Hi Muhammad!

If you don't know where an application is you could always open your terminal and type "whereis programname" or "locate program". 
These two commands will give you an output giving you the location of your programs.

---

### Post by Muhammad_Ahmad_Mujtaba on 2014-04-16
> **war28 said:**
> Hi Muhammad!

If you don't know where an application is you could always open your terminal and type "whereis programname" or "locate program". 
These two commands will give you an output giving you the location of your programs.

thanks man! that is a nice command! xD

---

### Post by dragonfly41 on 2014-04-16
If you have previous understanding of Windows then you will know of the useful tool Total Commander in Windows.

One near equivalent which I use is Krusader.

To install go to Applications > Ubuntu Software Centre.

There are others of course .. Thunar is another .. but just try Krusader for now.

Now launch Krusader

Click on "/" in toolbar to take you to your filesystem.

bin
boot
build
etc.
...

Click on "home" and select your user account

This is similar to entering C:/Users/Yourusername/ in Windows

Now in Krusader go to View > Show Hidden Folders

You can now see installed apps such as .mozilla (Firefox)

You can draw other parallels with Windows.  But a file manager such as Krusader, Thunar or other helps in navigating the file system.

---

### Post by coldraven on 2014-04-16
Install Synaptic Package Manager, you can right click on installed programs and get information on them.
```
sudo apt-get install synaptic
```

or use dpkg like in this example for the program Unetbootin:

```
user@laptop:~$ dpkg -L unetbootin
/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/unetbootin
/usr/share/doc/unetbootin/copyright
/usr/share/doc/unetbootin/changelog.Debian.gz
/usr/share/pixmaps
/usr/share/pixmaps/unetbootin.xpm
/usr/share/menu
/usr/share/menu/unetbootin
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/unetbootin.1.gz
/usr/share/applications
/usr/share/applications/unetbootin.desktop
/usr/bin
/usr/bin/unetbootin
```

Create some users and then look in /home. Then try logging in as one of them and save a document or image and see where the files go.

---

### Post by oldos2er on 2014-04-16
> **Muhammad_Ahmad_Mujtaba said:**
> and Linux would have [Debian] , where drive name is** 'File System' parallel to C: in Windows**.

[B]bin
boot
dev
etc
home
lib
lib64
lost + found
media
mnt
opt
proc
root
run
sbin
selinux
srv
sys
temp
usr
var
initrd.img
vmlinuz.exe

[/B]I want to know where softwares are installed and short description of all these folder; it will help me understand and operate Linux well.
Thanks to everyone!

[https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

[https://help.ubuntu.com/community/LinuxFilesystemTreeOverview](https://help.ubuntu.com/community/LinuxFilesystemTreeOverview)

---

### Post by sdowney717 on 2014-04-16
> **dragonfly41 said:**
> If you have previous understanding of Windows then you will know of the useful tool Total Commander in Windows.

One near equivalent which I use is Krusader.

To install go to Applications > Ubuntu Software Centre.

There are others of course .. Thunar is another .. but just try Krusader for now.

Now launch Krusader

Click on "/" in toolbar to take you to your filesystem.

bin
boot
build
etc.
...

Click on "home" and select your user account

This is similar to entering C:/Users/Yourusername/ in Windows

Now in Krusader go to View > Show Hidden Folders

You can now see installed apps such as .mozilla (Firefox)

You can draw other parallels with Windows.  But a file manager such as Krusader, Thunar or other helps in navigating the file system.

I do not see a way to mount extra drives in krusader or network drives?

---

### Post by dragonfly41 on 2014-04-17
> I do not see a way to mount extra drives in krusader or network drives?

Krusader > Tools > Mountman

or in Ubuntu top bar > Places

there are other ways .. by terminal or by apps.

---

