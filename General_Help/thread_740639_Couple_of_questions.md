---
title: "Couple of questions"
date: 2008-03-31
forum: General Help
---

### Post by waterskill on 2008-03-31
Hey guys. I gots a couple of questions for you.
1) What is the command for running a program?
2) When I install a program using the Terminal where does it go?
3) What is "Grub"?

Just some questions thathave been bugging me. :)
:popcorn:

---

### Post by Doorslammer on 2008-03-31
1) What is the command for running a program? it depends 
what program  most the time it's the name of the program .
if you type  firefox  then your browser firefox will open , 

2) When I install a program using the Terminal where does it go? don't have areal answer as I'm a newbbie also  most go to usr/bin I think if the program is installed system wide other wise it go's in your home directory  most the time hidden  .foldername

3) What is "Grub"? it's the boot loader  or boot menu if you will

hope that helps some

---

### Post by waterskill on 2008-03-31
> **Doorslammer said:**
> 1) What is the command for running a program? it depends 
what program  most the time it's the name of the program .
if you type  firefox  then your browser firefox will open , 

2) When I install a program using the Terminal where does it go? don't have areal answer as I'm a newbbie also  most go to usr/bin I think if the program is installed system wide other wise it go's in your home directory  most the time hidden  .foldername

3) What is "Grub"? it's the boot loader  or boot menu if you will

hope that helps some

Oh ok :) I'm trying to run dvr by the way

---

### Post by rainwalker on 2008-03-31
1) Answered in the post above

2) It depends; It can be in the directory you run the installer in, or it could be /usr/bin, or a couple others. I think you can use the command ```
whereis <what you're looking for goes here>
``` to find the location of files

3) Grub is the bootloader that allows you to choose what OS you want to boot into

---

### Post by warp99 on 2008-03-31
> 1) What is the command for running a program?

At the command line it's the name of the program. If it's not in the system path you would use a ./<name_of_program> to run the program in the current directory.

> 2) When I install a program using the Terminal where does it go?

If you install a .deb package it's installed according to Debian guidelines, which is normally within the '/usr' directory. When installing a program not a deb file, source or third party installer, most programs will install in the '/usr/local' or '/opt' directory.

> 3) What is "Grub"?

Grub stands for "Grand Unified Boot-loader"

If you want more questions answered just check out my signature.

---

### Post by Doorslammer on 2008-03-31
[http://monkeyblog.org/ubuntu/installing/#where_did_it_go](http://monkeyblog.org/ubuntu/installing/#where_did_it_go)

this should help you

---

### Post by waterskill on 2008-03-31
Thanks guys :))

---

### Post by em3raldxiii on 2008-03-31
Doorslammer has the gist of it.  I'll just add a bit of detail:

1.  When an application is installed in most linux distributions, your command-line-interface will be "updated" with the appropriate command to run the application you are trying to run.  In more than 95% of situations that *I* am aware of, it's conveniently the name of the application.  So, some commonly used applications are:  gedit, nano, aptitude, apt-get, etc.  Often you can run the command line program and feed it some info (like apt-get install blablaprogram).  This is especially true for command-line apps, but can even work for graphical apps.  And many of the single-line commands can be run from the ALT-F2 command interface as well.

If the program is not installed, but is simply a package you have downloaded and stuck in your home directory, then (assuming the file is executable), you can simply type ./programname into your command-line-interface to fire it up.

2.  As doorslammer pointed out, /usr/bin gets some stuff, but there are plenty of other places that various things go.  If you are fairly new to the whole thing, I would advise you to just "not worry about it" ... if it's installed happily with synaptic or with aptitude, then you shouldn't need to know where stuff went.  The only thing you might wanna mess with at this point would be configuration files which would be "hidden" directories or files in your /home/yourusername/ directory.

3.  GRUB is a boot loader that handles how you want your computer to start up.  If you have more than one OS installed, then it would give you the option to start your computer with one of the other OSs.  Windows has a boot loader as well, but it's much less robust so you almost never experience it.  There are other boot loaders that you can use .... strangely the name escapes me right now ... but the distribution "Mandriva" uses it.

You can also edit a configuration file for GRUB to include other things, or to change it's colors, etc.

---

