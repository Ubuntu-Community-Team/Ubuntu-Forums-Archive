---
title: "How to run autorun.inf cds and files?"
date: 2008-07-03
forum: General Help
---

### Post by myromance123 on 2008-07-03
I know this is a noob question but I cant find any packages or ways to run this, and I really NEED to run it, so any help is appreciated.

This is the error I get when trying to run the file from cd:

Couldn't display "/media/cdrom0/autorun.inf".
There is no application installed for this file type

---

### Post by jocko on 2008-07-03
I'm pretty sure you can't run a cd autorun program in linux.
The autorun programs on cd's are usually designed to run on windows, and usually just to start an installer program (which is also designed for windows).

Exactly what is on the cd?

---

### Post by lisati on 2008-07-03
Maybe there are exceptions to the "Designed for Windows" generalizations. Some CDs I have with autorun built in (mostly from magazines) are set to open up an HTML page which should be viewable with Firefox under Linux....

---

### Post by myromance123 on 2008-07-03
.pdf files are on the cd, and because it was made by cie it wont give me permission to view them individually, it has to be done through their program which is initiated from the autorun. It also has .htm versions of the files but i cant view those either. They open up in firefox blank.

  There was this tutorial in ubuntu wiki for autorun capability but it does not work for me so I was wondering if there was another way around~

  I really need to access this cd for my upcoming exams and I dont want to have to reinstall Xp (if there is no solution though, i will have to resort to it).

  Anyhelp whatsoever is appreciated~

---

### Post by jocko on 2008-07-03
> **lisati said:**
> Maybe there are exceptions to the "Designed for Windows" generalizations. Some CDs I have with autorun built in (mostly from magazines) are set to open up an HTML page which should be viewable with Firefox under Linux....
Yes, but the autostart program which loads that html page is still most likely a windows program.

---

### Post by jocko on 2008-07-03
> **myromance123 said:**
> .pdf files are on the cd, and because it was made by cie it wont give me permission to view them individually, it has to be done through their program which is initiated from the autorun. It also has .htm versions of the files but i cant view those either. They open up in firefox blank.

  There was this tutorial in ubuntu wiki for autorun capability but it does not work for me so I was wondering if there was another way around~

  I really need to access this cd for my upcoming exams and I dont want to have to reinstall Xp (if there is no solution though, i will have to resort to it).

  Anyhelp whatsoever is appreciated~

Do you know which file is the actual program (probably a .exe file)?
If you're lucky you can run it with wine.
If you're not sure which file is the executable program file, open up the inf file in a text editor (gedit). It should say which file it would start in windows.

---

### Post by mcduck on 2008-07-03
Just open the autorun.inf with a text editor (yes, it's a text file), check what program or file it's configured to open, and if it's some file that can actually be viewed in Linux then open it manually.

---

### Post by myromance123 on 2008-07-03
Yes there is an .exe file but I have already tried opening it with wine and nothing happens (the file is shellexe.exe if that means anything)

  Like I said this is a cd with cie permission blocks all over, I cant run the autorun even in the texteditor because I dont have permission. 
   Its very frustrating indeed :)

  Is there a way to running the cd normally without using the autorun.inf or .exe files? or is there any software packages that can help me run .htm files on ubuntu?

  Thanks for the replies so far ~

---

### Post by jocko on 2008-07-03
> **myromance123 said:**
> Yes there is an .exe file but I have already tried opening it with wine and nothing happens (the file is shellexe.exe if that means anything)

  Like I said this is a cd with cie permission blocks all over, I cant run the autorun even in the texteditor because I dont have permission. 
   Its very frustrating indeed :)

  Is there a way to running the cd normally without using the autorun.inf or .exe files? or is there any software packages that can help me run .htm files on ubuntu?

  Thanks for the replies so far ~

Firefox reads htm files fine.
I'm not sure what you mean by "cie permission blocks"?
But it seems it prevents you from reading any file from the cd?
In that case, the problem is the "cie permission blocks", without it you would be able to read the pdf's and htm's normally, and would probably even be able to configure your system to run the autorun feature with wine (with that [wiki tutorial]("https://wiki.ubuntu.com/autorun?highlight=%28autorun%29")).

---

### Post by cszikszoy on 2008-07-03
I thought that in 8.04 wine was configured to run the autorun.inf files that are on CD's and such?

[https://wiki.ubuntu.com/autorun](https://wiki.ubuntu.com/autorun)

I'm pretty sure this works, just install wine and everything should be fine.

---

### Post by myromance123 on 2008-07-03
Hmm, so it most probably means that this cd was made to work ONLY on windows, which means they do not rock. CIE is an examination board and this cd was produced by them. 

  Would there be a way to toggle off the permissions ? I have tried with checking the properties of the files and checking permissions but I cant change that .

  There is another file which is menu.js . Maybe if I could get that running I could access the files at the very least. What do I need to make .js files work then? Because my ubuntu says it has no application  capable of opening the file.

 The reason the wiki tutorial doesnt work for me is that in the terminal when I am trying to:

```
sudo apt-get build-dep gnome-volume-manager
mkdir gnome-volume-manager
cd gnome-volume-manager
apt-get source gnome-volume-manager
wget http://launchpadlibrarian.net/8292130/gnome-volume-manager-autorun-inf-02.patch
patch -p1 < gnome-volume-manager-autorun-inf-02.patch
cd gnome-volume-manager-2.17.0
./configure --prefix=/usr
make
sudo make install

```

 It will ask me whether or not i accept installing it and taking up space for it, the usual [Y/n] question but whether I enter "Y" or "n" it just aborts .

---

### Post by jocko on 2008-07-03
To install a package from source, if you got the source code from the repos, you don't need to run ./configure, make or make install.
Instead run this command:
```
fakeroot debian/rules binary
```
It will build a real debian package, which you can install with dpkg or gdebi.
(but first you'll need to install two packages: fakeroot and dpkg-dev)

But still, the problem you have is that you can't read the files on the cd. Solve that first.
Can you copy the files off the cd and change the permissions?

---

### Post by myromance123 on 2008-07-03
Yes I have tried copying the files off the cd and putting them on to my pc but it wont even allow me to do that. I have no problems with game cds except this cd and 2 other cds i had borrowed from my friends(contained halo and cod4). 

  All I know is that their similarities is the autorun feature preventing me access to the cd contents.

  I have kept up to date with my ubuntu, its 8.04.

---

### Post by v_mil on 2013-01-09
autorun.inf is a well-known great vulnerability  of Windows :cry:. The first thing may be performed after Windows (XP and older) installation (NOT IN LINUX!!!) is to disable autorun on all disks. No antivirus software can identify absolutely all viruses. I know some infections of antivirus-protected systems by very new autorun trojans. Another Windows vulnerability is desktop.ini, used any time the folder is opened by Windows Explorer. And we must use any third-party commander to secure Windows (NOT LINUX!!!). Linux does not use autorun. This makes Linux more secure. It is possible to write a packet that activate autorun possibilities, but please do not try to do it. Don't open a door for trojans!

---

### Post by oldos2er on 2013-01-09
Old thread closed, please don't bump old threads.

---

