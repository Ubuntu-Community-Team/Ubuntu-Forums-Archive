---
title: "Problem installing Nuke?  (compositing program)"
date: 2007-10-14
forum: General Help
---

### Post by dnsfailure on 2007-10-14
Hello, I'm wanting to try the demo version of Nuke on the fresh copy of Ubuntu Linux that I have installed (this is my first time using Linux)

I'm running the 64 bit version of Linux (on a 64 bit compatable machine), and I believe the Ubuntu version is 7.04.

The Nuke Installer can be found here:  [http://www.thefoundry.co.uk/promo/Nuke4.7v3-linux-x86-release-32.tgz](http://www.thefoundry.co.uk/promo/Nuke4.7v3-linux-x86-release-32.tgz)

When I download the installer, I unpack it to my desktop and I try to run the installer (it's icon is blue with two meshed gears, looks like an installer to me!)  When I double click on the unpacked installer file, nothing happens.  Nadda, nothing.  No error message or anything.

My only guess is that possibly this is not a 64 bit application, due to the number 32 in the file name?  I'm going to try and find out from the Foundry if this is a 32 bit program only.  If it is 32 bit only, I guess my only option is to go to a 32 bit version of Linux?  Or is there a way to run a 32 bit program under a 64 bit Linux?  (pardon my lack of hardware/software knowledge, but I guess that would defeat my whole purpose for running 64 bit then?)

My reason for going to Linux is so that I can build and utilize a machine with large amounts of ram (16gigs or so) to help out with my editing of very large image files (20,000 and 30,000 pixel wide film scans).  Nuke is a program I know and love in Windows when I'm at work, and I'm hoping to run it on Linux to make use of more ram (and I've been told that Nuke runs faster on Linux anyway, even with out extra ram)

Thanks for any help or info!

Daniel

---

### Post by jocko on 2007-10-14
You probably need to run the installer from a terminal:
```
cd /path/to/file
./filename
```Or, if the installer needs to be run with administrative privileges (this is usually the case):
```
sudo ./filename
```(of course, instead of "filename", you should use the name of the actual file)


If the program is 32bit only, it may not work on a 64bit platform, but there may be ways to do it.
Post any errors you get when you run the installer. If you're lucky someone will have an idea on how to solve them.

---

### Post by daveisadork on 2007-10-14
> **dnsfailure said:**
> My only guess is that possibly this is not a 64 bit application

It is indeed 32 bit only. That's what the x86 in the file name is referring to.

---

### Post by dnsfailure on 2007-10-14
hm... the light at the end of the tunnel is getting dimmer... haha!  Well, if indeed this is only a 32 bit application and the 64 bit linux won't run it, I guess my only other option is to run the 32 bit Linux, or just stick with Windows.  

Can the 32 bit Linux handle more ram than Windows 2k?  Or is there not really going to be any advantage to running Nuke in 32 bit Linux versus 32 bit windows?  I hear that Nuke runs a bit faster on Linux regardless of the ammount of Ram, but if it's only going to be a small increase (since I won't be able to use more than a few gigs of ram anyway) I might as well just stick with Windows unless I find I like Linux better?

THanks for the replies!  

Where do I type in the "sudo ./filename"?  Sorry, I'm new at Linux.

---

### Post by jocko on 2007-10-14
> **dnsfailure said:**
> Where do I type in the "sudo ./filename"?  Sorry, I'm new at Linux.

Open up a terminal: Program --> Accessories --> terminal

---

### Post by jocko on 2007-10-14
I tried to download and install nuke myself, just to see what's needed.
The installer is graphical, so you should be able to start it by double clicking it (If you run it as a normal user it will install into your home folder).
It seems to install fine on my 64bit laptop, but when I try to run it, it asks for a valid license.
So it may work on 64 bit, can't tell for sure, as I don't feel like getting a license for a program I don't think I have any use for.
It could be that you need to install some extra packages before you can run the installer. If you try to start it from a terminal, it should give an error and tell you what's missing.

---

### Post by dnsfailure on 2007-10-14
Joco, when I type in 
```
sudo ./Nuke4.7v3-linux-x86-release-32-installer
```

I get  "command not found"


and when I type in 
```
cd /home/dnsfailure/desktop/Nuke4.7v3-linux-x86-release-32-installer
```

I get "No such file or directory"  is that the correct way to point the terminal to the file?

---

### Post by jocko on 2007-10-14
> **dnsfailure said:**
> Joco, when I type in 
```
sudo ./Nuke4.7v3-linux-x86-release-32-installer
```I get  "command not found"


and when I type in 
```
cd /home/dnsfailure/[COLOR=Red]desktop[/COLOR]/Nuke4.7v3-linux-x86-release-32-installer
```I get "No such file or directory"  is that the correct way to point the terminal to the file?

The "command not found" error is because you are in the wrong directory, so the terminal can't see the file you tell it to run.
You have to tell the terminal which directory to work in. That's what the cd command does.

Make sure you type the correct path. If the file "Nuke4.7v3-linux-x86-release-32-installer" is on your desktop, the correct path is "/home/dnsfailure/[COLOR=Red]Desktop[/COLOR]/" (or simply ~/Desktop/"). Notice the capital "D" in "Desktop". The file system is case sensitive.
Also, don't include the filename in the path you cd (=change directory) to.

---

### Post by circusmonkey on 2007-10-21
Its pretty pointless as I am finding trying to use linux at this time the only application that will currently run with ease is Houdini 

Nuke fails 


./Nuke4.7v3-linux-x86-release-32-installer: error while loading shared libraries: libz.so.1: cannot open shared object file: No such file or directory
xxx@circusmonkey:/media/vfx_project/LiniuxApplications$


shake fails 

xxxx@circusmonkey:~$ cd /opt/shake-v4.10.0606/bin
xxxxt@circusmonkey:/opt/shake-v4.10.0606/bin$ ./shake
/opt/shake-v4.10.0606/bin/shkx.exe: error while loading shared libraries: libXext.so.6: wrong ELF class: ELFCLASS64


It fails from what I can see because Unbuntu does not  and cannot run wtih 32 bit libs and 64 bit libs . Apart from all the permission rubbish and sudo / root nonsense and having to use a sodding terminal to do anything .It would be a good OS if it was more user friendly and not designed for people with degrees in computer science  who are interested in the nuts and bolts. 
I just want to run my applications like shake / nuke / maya and Houdini. 3 of which it fails on so its back to xp !

---

### Post by wawarren on 2007-10-22
I just tried this myself and I had libz.so.1 missing so I downloaded the 32bit library from this site and copied it into my usr/lib32 directory.  

Now I'm getting this...  libXinerama.so.1: wrong ELF class: ELFCLASS64

anyone know how to fix this?

edit: nevermind, it appears as though Ubuntu is trying to tell me that it can only find the 64bit version of libXinerama.so.1.  I'll check [http://packages.ubuntu.com](http://packages.ubuntu.com) for the 32 bit version of this library after work and post if I get it working.

---

### Post by jocko on 2007-10-22
> **circusmonkey said:**
> Its pretty pointless as I am finding trying to use linux at this time the only application that will currently run with ease is Houdini 

Nuke fails 


./Nuke4.7v3-linux-x86-release-32-installer: error while loading shared libraries: libz.so.1: cannot open shared object file: No such file or directory
xxx@circusmonkey:/media/vfx_project/LiniuxApplications$


shake fails 

xxxx@circusmonkey:~$ cd /opt/shake-v4.10.0606/bin
xxxxt@circusmonkey:/opt/shake-v4.10.0606/bin$ ./shake
/opt/shake-v4.10.0606/bin/shkx.exe: error while loading shared libraries: libXext.so.6: wrong ELF class: ELFCLASS64


It fails from what I can see because Unbuntu does not  and cannot run wtih 32 bit libs and 64 bit libs . Apart from all the permission rubbish and sudo / root nonsense and having to use a sodding terminal to do anything .It would be a good OS if it was more user friendly and not designed for people with degrees in computer science  who are interested in the nuts and bolts. 
I just want to run my applications like shake / nuke / maya and Houdini. 3 of which it fails on so its back to xp !

As I said, I managed to install Nuke on my 64bit gusty, with no complaints about missing libraries or wrong ELF class.
(but as I don't have a license I don't know if the installed program works, I just know the installer works).
You'll need to install some 32 bit libraries, which you get by installing the package ia32-libs from the repos.

---

