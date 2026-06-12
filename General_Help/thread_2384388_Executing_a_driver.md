---
title: "Executing a driver"
date: 2018-02-06
forum: General Help
---

### Post by warmango on 2018-02-06
Alright, im expirimenting to find out these things MYSELF! please dont put me down,

Alright, im attempting to execute a .c file as a script...stupid i know, but i want to try it anyways, only a few issues, 
this is the code inside the script [http://paste.ubuntu.com/26532366/](http://paste.ubuntu.com/26532366/)
but when i run it, i get this error
```
(trusty)zach-15803@localhost:~/Downloads/huion-driver-master$ ./hid-huion.c
./hid-huion.c: line 1: /bin: Is a directory
./hid-huion.c: line 2: hid-huion.c: command not found
./hid-huion.c: line 3: hid-huion.c: command not found
./hid-huion.c: line 4: syntax error near unexpected token `('
./hid-huion.c: line 4: ` *  Copyright (c) 2013 Martin Rusko'
```


im trying to run it as a script to (in my mind atleast) emulate the computer running it, 

also i have troubles with the makefile that came with it

the code inside the file 
[http://paste.ubuntu.com/26532398/](http://paste.ubuntu.com/26532398/)


```
(trusty)zach-15803@localhost:~/Downloads/huion-driver-master$ ./Makefile
./Makefile: line 1: syntax error near unexpected token `$(KERNELRELEASE),'
./Makefile: line 1: `ifneq ($(KERNELRELEASE),)'
```

---

### Post by TheFu on 2018-02-06
We all started out in the same place.

C language isn't a script.  It must be compiled and linked before it can be "run."
You cannot run a .c file.  It won't work - ever.

The steps are.
* edit the C file.
* compile the C file, fix any errors or warnings from the compiler output.
* link the C file with any/all libraries to make it link.  Fix any errors or warnings from the linker output.
* After both the compile and link steps are finished, you should end up with file.c, file.o and file (the executable).  You can run it by using **./file**. The ./ forces the current directory to be used.

gcc is a normal compiler and linker on Linux. There are others.

Make is just a way to handle builds (compile and linking) in a more automatic way when there are multiple files, multiple libraries and perhaps multiple programs being created. A simple shell script could be used too, but "make" can understand when a file is modified (timestamp changed), so anything dependent on that modification would be rebuilt.  For a non-trivial compile + link + program "build", this can save lots and lots of time.

BTW, adding an *echo "* at the top of the file isn't likely to work. It breaks because C has double-quotes which break the echo syntax from bash/sh/ksh.  

A very important aspect to Makefiles is they use tab characters for indentation.  If the editor replaces tabs, the makefile won't work. I haven't dealt with Make in years. Looking over the makefile posted, it seems to be a different type of make than I recall.  Sorry, can't help.

---

### Post by warmango on 2018-02-06
OH! the "echo" command was me trying to quickly send the internals of the file into a pastebinit.. then i realized i could just "cat" the files

And honestly, im newbish, and the only machine i have the doesnt natively support the device is running Lubuntu 14 through Crouton on a arm chromebook

like, im only in highschool

and i noticed that most of the errors i get in the .c file when i try to run it that way, are in the /*comments/* in the file,

---

### Post by TheFu on 2018-02-06
My comments were for generic C programs.  Device drivers are a little different.  There should be a README file or INSTALL file included with the code that explains how to make things work.

But .... if chromeOS doesn't support the device, then you are screwed.  That is why I don't run ChromeOS - kernel modules that google hasn't approved are nearly impossible to add to ChromeOS.  Since the same kernel is used under crouton and ChromeOS, you can't add the driver to the crouton instance either.  BTW, I'm typing on a chromebook that I had to wipe ChromeOS from to run Ubuntu so I could use kernel modules.

I decided it was easier to wipe ChromeOS than it was to try to get the kernel module I needed working under ChromeOS.  It is a security issue from the google point of view while it was a missing capability to me.

---

### Post by warmango on 2018-02-06
i dont want to sound like a childish kid you'd find on TF2 or any mmo, but....HOW?!
i want to wipe chrome-OS off my Samsung Series 5 ALEX Chromebook, but i have no clue how, im only using crouton because it was the only thing i could get to work

---

### Post by TheFu on 2018-02-07
> **warmango said:**
> i dont want to sound like a childish kid you'd find on TF2 or any mmo, but....HOW?!
i want to wipe chrome-OS off my Samsung Series 5 ALEX Chromebook, but i have no clue how, im only using crouton because it was the only thing i could get to work

Google found this: [https://www.reddit.com/r/chromeos/comments/7tvt5g/help_installing_linux_on_samsung_series_5/](https://www.reddit.com/r/chromeos/comments/7tvt5g/help_installing_linux_on_samsung_series_5/)

Doesn't look good.  

How to load a real Linux on any Chromebook is a specialize effort for each different vendor and model.  If loading Linux on a chromebook is desired, it is best to do all the research BEFORE purchasing.  I've seen a few models come to our LUG looking to get Linux and there wasn't anything we could do.

---

