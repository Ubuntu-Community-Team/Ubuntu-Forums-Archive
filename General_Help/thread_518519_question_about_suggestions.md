---
title: "question about suggestions"
date: 2007-08-06
forum: General Help
---

### Post by rubperezt on 2007-08-06
i would like to know if there is (and if so where?) a suggestion session for futher linux/ubuntu versions, i would like to suggest some kind of easier way to install programs, like windows .exe package or Mac copy-to-install system instead of rpm/tar.gz/synaptic package/deb/etc it scares out new users like me :P!

---

### Post by Rab22 on 2007-08-06
I have trouble understanding what makes debs so much harder than exes?  In reality, you can perform the same tasks -- download, double click, and select "install".

---

### Post by misfitpierce on 2007-08-06
Yea installing them is not harder what so ever... Getting a package uninstalled could be simplified some I believe for new users. Installing deb is pretty straight forward... Find ubuntu package in deb double click install done.

---

### Post by rubperezt on 2007-08-06
well yes. deb is relatively easy (still is a bit less flexible as windows/mac system) but what about the other type of installation? and what about having different types of installation? one and only one would be perfect.

---

### Post by Rab22 on 2007-08-06
Well there is the 'Add/Remove Software" on Ubuntu.  I've never use it because it's too basic...

What I think Ubuntu needs to do is do a rework on "Add/Remove".   It should probably be under Systems > Administration and when selected should query a listing of all the currently installed applications and **only** show those by default.  There should be some type of option to "Install New Software" which will show other software packages that can be installed.  What also needs to be worked into it is the ability to perform "dpkg-reconfigure"...since that would help resolve some of those instances where people need to use the command line (like if you want to change your GDM to KDM or visa versa).

---

### Post by rubperezt on 2007-08-06
what about just copy the directory and the application is already installed? why bother making rpm files or tar.gz or .deb or which ever why not instead copy the entire directory to the system (like copy /TextEditor3.0 [assuming that all TextEditor3.0 needed files are into /TextEditor3.0 directory) to /usr/programs) manually add a shortcut to your menu and thats it.?
I have been using windows for 10years and just now i decided to switch, what was holding me back was the "lack" of applications for linux, now i just discovery that there are tons of apps for linux for almost anything i could think off but sadly it is a bit hard to install them.

---

### Post by nitro_n2o on 2007-08-06
> **rubperezt said:**
> what about just copy the directory and the application is already installed? why bother making rpm files or tar.gz or .deb or which ever why not instead copy the entire directory to the system (like copy /TextEditor3.0 [assuming that all TextEditor3.0 needed files are into /TextEditor3.0 directory) to /usr/programs) manually add a shortcut to your menu and thats it.?
That will not work... dependencies issues are more than this... what makes *nix great is that "Do one thing and do it good" an application might be using several libraries and tools that are not the system and needed to be installed.. 
however if you put all your needs in one folder for some particular program then you'll need some HUGE disk to have multiple redundant packages and libraries... 
and ohhhhhh adding shortcuts manually might is harder than compiling from source

---

### Post by mcduck on 2007-08-06
> **rubperezt said:**
> what about just copy the directory and the application is already installed? why bother making rpm files or tar.gz or .deb or which ever why not instead copy the entire directory to the system (like copy /TextEditor3.0 [assuming that all TextEditor3.0 needed files are into /TextEditor3.0 directory) to /usr/programs) manually add a shortcut to your menu and thats it.?
I have been using windows for 10years and just now i decided to switch, what was holding me back was the "lack" of applications for linux, now i just discovery that there are tons of apps for linux for almost anything i could think off but sadly it is a bit hard to install them.

The problem with that s that it makes all applications take much more disk space and resources than what is really needed. Pretty much all applications today use at least some libraries, and in the Windows way every application must bring it's own copy of all libraries with it.

For example instead of having one mp3 library that all your music and media tools use in the Windows way each program needs it's own copy of that library. And then if you run several of those programs at the same time they each need to load their own versions of that library into RAM. In the package-based way Linux uses all programs can share the same library, and it only needs to be loaded to RAM once and then all prorams can use it.

In theory Windows could do the same , but the way programs are installed means that there's no way actually do it. There's no version control or any other smart way of managing these libraries in Windows and therefore each program must use their own copies of libraries.

Anyway, as long as what you want is available in Ubuntu's repositories installing and removing software is way easier than ever in Windows/Mac platforms.

And the other file formats are needed, if not for you, then for those who actually develop the software and need to get it in source code format instead of binary packages. And as there are so many different Linux distributions, running on many different computer architectures, that source code is the only way to distribute your program to everybody.

edit: Actually there already is a way to install software in the Windows style, Autopackage. It's just that the package management in Linux is so much better that in the end people don't use Autopackage. ;)

---

### Post by strabes on 2007-08-06
[http://linux.oneandoneis2.org/LNW.htm]Linux is NOT windows](http://linux.oneandoneis2.org/LNW.htm]Linux is NOT windows)

**sudo apt-get install packagename** or **sudo dpkg -i package.deb**

Just because it's different than what you're used to doesn't mean it's inferior. Linux's method of sharing libraries is objectively better than windows'. Being able to fetch & install almost any program I want with one command is also objectively better than windows' method: 1) Open browser 2) Search for program's website 3) Browse program's website until I find the download. 3) Download the .exe 4) Browse to the exe folder. 5) Double click on the exe. 6) Click "next" 9 times in a wizard. 7) Restart computer. 8 ) Finally run program.

There is also no way of updating your programs/applications unless the program has that feature built in. Generally, if you want to update an application in windows, you have to manually repeat all of the steps listed above. In (debian-based distros of) linux, all it takes is one (or two) command(s): **sudo apt-get update && sudo apt-get upgrade**

---

### Post by rubperezt on 2007-08-06
ok the copy n' install might not be the best idea but still several type of installer it is not very confortable specially for new users. After 1 week im starting to feel more comfortable with the deb package, the synaptic package system but still it can be improved. After all the rpm package and deb package where created to simplify the installation process of tar.gz etc but now tar.gz is still in use. 
Other issue that i believe is a bit extreme at least for Home PC users is the need to put passwords everywhere. I think that in the desktop version u should have the option to deactivate password in the installation.

---

