---
title: "new to ubuntu and started to learn how to create install package but stucked"
date: 2008-06-23
forum: General Help
---

### Post by dinbrca on 2008-06-23
i have started to learn how to create an install packages from:
[http://monkeyblog.org/ubuntu/installing.html#source](http://monkeyblog.org/ubuntu/installing.html#source)
but i got stucked.
when i write:
sudo make install
it tells me:
make: *** No targets specified and no makefile found.  Stop.
is that because there is no configure file?

---

### Post by lennartack on 2008-06-23
Maybe you're in the wrong directory. Find out in which directory the source and the makefile are located and cd to that directory. Did you type the "make" command before make install? And the last possibility is that you don't need to type make install. See if there is a file called INSTALL in the program you've downloaded for installation instructions.

---

### Post by rraj.be on 2008-06-23
You can use this command to install something in a easy manner
```

sudo apt-get install <Application name>
```

Or you can use synaptic package manager to install packages efficiently.
To open synaptic package manager go to 

System --> administration --> synaptic or type


```
sudo synaptic in terminal.

```


Get much more info regarding installing software here

```
[[COLOR="Blue"]https://help.ubuntu.com/community/SoftwareManagement[/COLOR]]("https://help.ubuntu.com/community/SoftwareManagement")
```

---

### Post by dinbrca on 2008-06-23
lennartack:
i cd to where i found makefile.. now when i am in the dir of makefile and enter make it says:
"
cd ../enet; ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.
make: *** [../enet/Makefile] Error 77
"
if you can download the game i want to install and will guide me then thank you very much cause i think it is going to be very hard to explain you where is each file..
this is the link- the game is called assaultcube:
[http://sourceforge.net/project/downloading.php?groupname=actiongame&filename=AssaultCube_v0.93.tar.bz2&use_mirror=switch](http://sourceforge.net/project/downloading.php?groupname=actiongame&filename=AssaultCube_v0.93.tar.bz2&use_mirror=switch)
offical website:
[http://assault.cubers.net/](http://assault.cubers.net/)
i am not so sure if i even need to install it it came with a .tar.gz package..

---

### Post by lennartack on 2008-06-23
> **dinbrca said:**
> 
if you can download the game i want to install and will guide me then thank you very much cause i think it is going to be very hard to explain you where is each file..
this is the link- the game is called assaultcube:
[http://sourceforge.net/project/downloading.php?groupname=actiongame&filename=AssaultCube_v0.93.tar.bz2&use_mirror=switch](http://sourceforge.net/project/downloading.php?groupname=actiongame&filename=AssaultCube_v0.93.tar.bz2&use_mirror=switch)
offical website:
[http://assault.cubers.net/](http://assault.cubers.net/)
i am not so sure if i even need to install it it came with a .tar.gz package..
Hey I played that game too :D. But ok, I downloaded that file and it seems that there are binaries availabe, which means you don't have to compile with make and such. Running assaultcube.sh then gives a message that you need to compile the cube engine, but you can download binaries for the cube engine too: [http://sourceforge.net/project/downloading.php?group_id=91993&use_mirror=switch&filename=cube_2005_08_29_unix.tar.gz&26606469](http://sourceforge.net/project/downloading.php?group_id=91993&use_mirror=switch&filename=cube_2005_08_29_unix.tar.gz&26606469).

---

