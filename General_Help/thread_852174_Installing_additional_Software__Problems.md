---
title: "Installing additional Software | Problems"
date: 2008-07-07
forum: General Help
---

### Post by sweetaussie on 2008-07-07
Hi all I'm very new to this and I'm having trouble installing software.I start of in the terminal and get up to moving the the file from desktop.I then change cd and try the sudo apt-get install and this is what it says.

```
janny@janny:~$ cd Desktop
janny@janny:~/Desktop$ dir
crossword-0.1.0.tar.gz  gtz-0.9.1-20020521-win32.zip
gtz                     interLOGIC-linux-i386.tar.gz
janny@janny:~/Desktop$ mv -f ~/Desktop/gtz ~/Gtz
janny@janny:~/Desktop$ cd ~/Gtz
janny@janny:~/Gtz$ dir
AUTHORS  gtz.exe    libgdk-0.dll       libgmodule-2.0-0.dll  libintl-1.dll
COPYING  iconv.dll  libglib-2.0-0.dll  libgtk-0.dll          README
janny@janny:~/Gtz$ su
Password:
root@janny:/home/janny/Gtz# sudo apt-get install gtz
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package gtz
root@janny:/home/janny/Gtz#

```


I'm not sure what I'm doing wrong can someone please point me in the right direction.Thanks in advance.

---

### Post by avtolle on 2008-07-07
It appears that the gtz file is a Windows .exe file, which will not install on a Linux system. Are you using Wine?

---

### Post by brian_p on 2008-07-07
> **sweetaussie said:**
> I'm not sure what I'm doing wrong can someone please point me in the right direction.Thanks in advance.

I snipped your report to save space but it was a very clear and concise one.

The only files you can install end in .deb. Yours didn't - so you can't!

Use the package manager, synaptic. Familiarise yourself with it. It is your best friend.

---

### Post by mcduck on 2008-07-07
Yeah, that's definitely a Windows executable. Try with Wine, or perhaps Mono if the program is coded in C#.

Also, apt-get is _only_ for installing programs from repositories. It has nothing to do with stuff you download to your machine and then install manually.

Manually insyalling depends on what kind of package you downloaded. .deb packages can be installed either by simply clicking on them, or with the "sudo dpkg -i packagename"-command. .rpm's can be converted do .dpkg with "alien" and then installed. These ways will register the package with ubuntu's package management so they can be removed using dpkg, apt-get, aptitude or Synaptic or any other package management tool.

Other than those, all packages are simply compressed archives that can contain pretty much anything from source code to ready-to-use binary executables. (just like a .zip or a .rar). When the software is distributed this way your only choise is to extract it and take a look what's inside, you usually find a README or INSTALL file that tells you how it should be installed.

---

### Post by sweetaussie on 2008-07-07
> **avtolle said:**
> It appears that the gtz file is a Windows .exe file, which will not install on a Linux system. Are you using Wine?

Thanks for your quick response.  I do apologize for not being better at this.  I love tinkering, but sometimes get stuck, like this time.

This is where I got this file from, I was under the impression that it would work on Linux.  How can I tell if it will, or will not?
[http://www.linux.org/apps/AppId_5734.html]("http://www.linux.org/apps/AppId_5734.html")


[HTML]Gyahtzee is a gnomified version of yahtzee. It is based on a curses version released by Orest Zborowski in 1992.
 
Homepage 	http://www.geocities.com/CapeCanaveral/Lab/7731/gyahtzee.html
Download 	http://www.geocities.com/CapeCanaveral/Lab/7731/gyahtzee-980624.tgz
Author 	Not Shown <sdh_AT_po_DOT_cwru.E.D.U>
Version 	snapshot
Licence 	GPL
Source 	Yes
Environment 	Gnome
Status 	Development
[/HTML]

Also, what is wine?

Sorry. :(

Thanks again.  Hope to hear from you again on this.

---

### Post by avtolle on 2008-07-07
From visiting the link, and looking at what you posted, the program that I think you want is 
gyahtzee-980624.tgz which is definitely not what you show in your initial post. Thus, I am confused a bit.

EDIT: Wine is an application that allows *some* Windows programs to be run in Linux.

---

### Post by soccerboy on 2008-07-07
wine is an api stack built for unix systems so that windows executables can run in linux.  It is not perfect with windows api yet so not all windows applications run but most can run.

---

### Post by sweetaussie on 2008-07-07
> **avtolle said:**
> From visiting the link, and looking at what you posted, the program that I think you want is 
gyahtzee-980624.tgz which is definitely not what you show in your initial post. Thus, I am confused a bit.

EDIT: Wine is an application that allows *some* Windows programs to be run in Linux.

YES you was right so i went and downloaded the right one and the same thing happens.So are all these programs on this site windows or linux?

---

### Post by mcduck on 2008-07-07
> **sweetaussie said:**
> YES you was right so i went and downloaded the right one and the same thing happens.So are all these programs on this site windows or linux?

Well, it looks like it is for Linux. That would mean that it's a C# app and you can run it natively in Linux with Mono (C#/Mono apps often come as .exe files even for Linux systems).

Check the readme file for better instructions, but generally running "mono filename" should work.

edit: I downloaded the software and the correct package doesn't have .exe file but source code instead.. You'll need to follow the instruction in the INSTALL file to compile it. But are you sure that this program isn't in Ubuntu's repositories? In that case you shouldn't be installing it by hand anyway.. ;)

---

### Post by brian_p on 2008-07-07
> **sweetaussie said:**
> YES you was right so i went and downloaded the right one and the same thing happens.So are all these programs on this site windows or linux?

Did the file you downloaded end in .tgz? If it did it is source code. It is used to build (that is, make) a program which will work on Linux. Building programs can be easy, hard or very hard. How much effort you want to put into it may depend on how desperately you need the program.

---

