---
title: "RPM command not found?!!!"
date: 2006-11-18
forum: General Help
---

### Post by unixevangelist on 2006-11-18
seriously, this looks like a very basic command used to open and run installer files, whenever i try to use it it says "rpm: command not found"
and whenever i double click an RPM file, it says "cannot open. not a supported filetype" (or something to that meaning)
so HTF do i get RPM? it should be in the kernel but if its not how do i get it? i couldnt find a download on google.

---

### Post by loell on 2006-11-18
.deb pacakage is the equivalent .rpm in ubuntu, perhaps try searching deb package for that program

anyways it seems that you came from an rpm distribution or you've just read about it.

 you can install rpm package by converting it to deb
 ei.

    ```
alien filename.rpm
```
and then it will be converted to filename.deb, double click it to open and install


you should install the alien command first by

   ```
sudo aptitude install alien
```


what rpm package are trying to install?

---

### Post by speedman on 2006-11-18
Ubuntu is Debian based and uses deb files.  rpm isn't native to Debian - it's a Red Hat package type.  You can use alien to convert rpms to debs with varying levels of success, but it is always preferable to use debs in Ubuntu.  However, it is even better to grab a package with a meta tool like apt-get that will resolve dependencies.


Regards,

SM

---

### Post by iamhugeinjapan on 2006-11-18
There's a good chance your program is already in the repositories. Search for it with Synaptic Package Manager (It's in System - Administration)

In Synaptic, under Settings - Repositories you can add multiverse and universe repositories for thousands more programs.

---

### Post by unixevangelist on 2006-11-18
thanks

now how do i run a program that only root has permission to access
i am assuming sudo (sorry im a noob)
but i cant run the newly created deb because im not root (permission denied)

also i got this when i made the file:
Warning: Skipping conversion of scripts in package VMwareTools: postinst postrm preinst prerm
Warning: Use the --scripts parameter to include the scripts.
are these warnings important? how do i add the -- parameter? i tryed typing it after the command and it didnt work, o well
the DEB file is made, only root can access it and i dunnno how to access a file in root

---

### Post by MrFSL on 2006-11-18
> thanks
now how do i run a program that only root has permission to access
i am assuming sudo (sorry im a noob)
but i cant run the newly created deb because im not root (permission denied)
Well you can change permissions using chmod or right clicking on the file from the GUI. sudo dpkg -i yourfile.deb ought to fix your permission denied problems.

> also i got this when i made the file:
Warning: Skipping conversion of scripts in package VMwareTools: postinst postrm preinst prerm
Warning: Use the --scripts parameter to include the scripts.
are these warnings important? how do i add the -- parameter? i tryed typing it after the command and it didnt work
sudo alien --scripts nameoffile.rpm (works like a charm)

---

### Post by PilotJLR on 2006-11-18
> **unixevangelist said:**
> seriously, this looks like a very basic command used to open and run installer files, whenever i try to use it it says "rpm: command not found"
and whenever i double click an RPM file, it says "cannot open. not a supported filetype" (or something to that meaning)
so HTF do i get RPM? it should be in the kernel but if its not how do i get it? i couldnt find a download on google.

Umm... wild guesses like "should be in the kernel" aren't going to help you. :p 
You need to read the basics: [https://help.ubuntu.com/6.06/ubuntu/desktopguide/C/index.html](https://help.ubuntu.com/6.06/ubuntu/desktopguide/C/index.html)

This guide is short and to the point. It will help you a lot!

If you haven't already, install alien with:
```
sudo apt-get update
sudo apt-get install alien
```

Then, install the rpm like so:
```
sudo alien -i --scripts nameofthefile.rpm

```

This will convert RPM to DEB and then install.

---

### Post by PilotJLR on 2006-11-18
One more thing... after you install with the alien -i --scripts command I provided, run 
```

sudo apt-get install build-essential xinetd linux-headers-`uname -r`
sudo vmware-config.pl
```

Those 2 packages I listed are required to build the vmmon kernel module. Let us know if there are any errors, or search here... I'm doing this from memory, but I don't *think* I forgot any packages.

---

### Post by unixevangelist on 2006-11-18
thanks yeah i know the second step, but thanks for helping me
you guys own
my computer experience is just a c++ programmer/gamer/scripter, not a linux pro. this is my first day with linux on VMware Workstation.

---

### Post by PilotJLR on 2006-11-18
> **unixevangelist said:**
> thanks yeah i know the second step, but thanks for helping me
you guys own
my computer experience is just a c++ programmer/gamer/scripter, not a linux pro. this is my first day with linux on VMware Workstation.

Not bad for day one! You jumped right in there!  :D 

Your programming experience will probably be very useful in Linux.

---

### Post by unixevangelist on 2006-11-18
that third step you asked me to do doesnt work
says no such command

---

### Post by PilotJLR on 2006-11-18
> **unixevangelist said:**
> that third step you asked me to do doesnt work
says no such command

Which one????? 

Based on your previous post, I think you might be using an Ubuntu guest OS... so you are trying to install vmware tools??? If so, sudo vmware-config-tools.pl

Note that with a bash/dash shell, you can also type vmware, and hit tab twice to list everything in your path that starts with "vmware."


If you are not trying to install vmware tools, then pls provide specifics on what you are doing and what the error was and when exactly it happened...

---

