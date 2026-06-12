---
title: "Permission denied error while installing a software"
date: 2014-11-09
forum: General Help
---

### Post by tom_sawyer on 2014-11-09
[SIZE=2][FONT=verdana][COLOR=#333333]I'm trying to install a software called OOF2 on ubuntu 14.04. The prerequisites were installed perfectly according to the instructions given [here]("http://www.ctcms.nist.gov/oof/oof2/prerequisites.html"). Following which I had to execute two commands[/COLOR]
```
python setup.py build
python setup.py install
```
[COLOR=#333333]while running the build command I got repeated instance of the following warning.[/COLOR]
```
cc1plus warning command line option ‘-wstrict-prototypes’ is valid for c/objc but not for c++
```
[COLOR=#333333]Later while running the install command, the following error was reported.[/COLOR]
```
error: [Errno 13] Permission denied: '/usr/lib/liboof2engine.so'
```
[COLOR=#333333]
Question 1 : What does that error mean and how do I solve it?
[/COLOR]
[COLOR=#333333]Question 2 : The install command ran for few seconds before the error was reported. How do I remove the partially installed files(if any)? If I run the install command again without removing the partially installed files, will it create problems?
[/COLOR]
[COLOR=#333333]Question 3 : Where is the software getting installed? I have not mentioned any file path anywhere.
[/COLOR]
[COLOR=#333333]Question 4 : The instructions in the software website includes a '%' infront of the command. How important is this percentage symbol? I get an error if I use it[/COLOR]
```
bash: fg: %tar: no such job
```

[COLOR=#333333]Question 5 : should I try using 'sudo' before the build and install command? What are the implications?[/COLOR]
[COLOR=#333333]
Note: I don't use Ubuntu frequently. Please try to provide very straightforward answers.[/COLOR]
[/FONT][COLOR=#333333][FONT=UbuntuRegular][FONT=verdana]Thanks for your patience :)[/FONT]
[/FONT][/COLOR][/SIZE]

---

### Post by claracc on 2014-11-09
I suppose you are trying to install software from source through compiling and installing.

Here, [http://www.wikihow.com/Compile-a-Program-in-Linux](http://www.wikihow.com/Compile-a-Program-in-Linux) you have a step by step guide to do so, with steps explained.

You have to use sudo when you run command ```
sudo make install
```

---

### Post by tom_sawyer on 2014-11-09
no need to use python then?? and what about the partially installed files?

---

### Post by claracc on 2014-11-09
In the instructions page, I can only see, you have to install the following software:

```
sudo apt-get remove graphicsmagick-libmagick-dev-compat
   sudo apt-get install python-gtk2-dev
   sudo apt-get install libgnomecanvas2-dev
   sudo apt-get install libmagick++-dev
   sudo apt-get install liblapack-dev
   sudo apt-get install bison
```

As you say the installation of this software went well, what are the other instructions you followed to install the oof2 software, and what is the source tar package you are trying to compile?

---

### Post by tom_sawyer on 2014-11-09
After running those commands, I downloaded the OOF2 program from here [http://www.ctcms.nist.gov/oof/oof2/index.html#download](http://www.ctcms.nist.gov/oof/oof2/index.html#download)

The [readme ]("http://www.ctcms.nist.gov/oof/oof2/source/README")file had these instructions 

```
tar -xzf oof-<version>.tar.gz
cd oof-<version>
python setup.py build
python setup.py install
```

The source tar package was " [COLOR=#000000][FONT=monospace]oof2-2.1.11.tar.gz "[/FONT][/COLOR]

---

### Post by tom_sawyer on 2014-11-11
anyone??

---

### Post by pc240284 on 2014-12-03
Hey I don't know if you have found the answer yet but I had the same problems as you did. I am also quite new to linux and python librairies, so sorry if there is any mistakes in what I say.

 The error means that you are not logged as an administrator, so that you cannot change all the thing you want to. In this case you don't have the right to create the files oof wants to in your root folder. I guess that you are the administrator of your system since you did install the prerequisites. You have to know that logging in Linux (via the logging screen, as you do in Windows for ex) doesn't mean that your session is in admin mode. So basically, you have to use "sudo" before any command line if you want to run something as an administrator. It will ask you your password again. This is a second level of security I guess.

You don't need to uninstall anything, even after the failure. I found that using linux command lines to install libraries or softwares is very powerful in that way (again I am new to linux). For example, you can try to re-install the prerequisites (re-type the command lines) and you will see that it will tell you that it is already installed and up-to-date. You should have a look at all the commands "apt-get" here : [https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto) For example if you type "sudo apt-get upgrade" it will upgrade everything that need to be.

I don't understand the warning with the C++ and C/objc... It's only a warning though :)
But now that you have the prerequisites, type "python setup.py build" (note that you don't need "sudo" here, it will only create files in your oof folder) and then "sudo python setup.py install". Then you only need to type "oof2" to start the software.

Sorry if something is not clear...

---

### Post by ceramdz on 2015-01-19
Hi tom,

I have installed oof2 on my machine under unbunto 14.10 and during the compilation the terminal shows the same error message. In my case oof2 is working well. You may be need to run build and install together without swig like this ---> " sudo python setup.py build --skip-swig install ". Check if you have installed pygtk properly  with the appropriate modules (libglade, python-cairo-dev, etc.)

---

### Post by ceramdz on 2015-01-19
Hi tom,

I have installed oof2 on my machine under unbunto 14.10  and during the compilation the terminal shows the same error message. In  my case oof2 is working well. You may be need to run build and install  together without swig like this ---> " sudo python setup.py build  --skip-swig install ". Check if you have installed pygtk properly  with  the appropriate modules (libglade, python-cairo-dev, etc.)

---

