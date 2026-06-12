---
title: "C Program Installation"
date: 2013-08-16
forum: General Help
---

### Post by billy2 on 2013-08-16
Hi all,  I am new here and would appreciate any help.  I am trying to install a C program on Ubuntu 13.04 but ran into a problem with permissions (I think).

When i type "make INSTALL" in the terminal, it begins to work then comes up with this:
make: [/path/bin/formod_aniso] Error 1 (ignored)
chmod: cannot access '/path/bin/formod_aniso': No such file or directory
make: ***[/path/bin/formod_aniso] Error 1

I have permission to read and write the bin directory, so I do not understand why there is an error creating the file.  If I manually create the file then try to do "make INSTALL" there are no errors but the file is empty and the program doesn't work.

Thanks

---

### Post by Petro Dawg on 2013-08-16
Did you try "sudo make install"?

Be sure you trust the source of the program you try to install.

Also, did you run "make" first?

---

### Post by billy2 on 2013-08-16
When I try "sudo make INSTALL" it doesn't run any of the stuff it was doing before and just says:

Makefile:3: /src/Makefile.config: No such file or directory
make: *** No rule to make target '/src/Makefile.config'. Stop.

---

### Post by Petro Dawg on 2013-08-16
Is there a README file in the folder, usually it will outline what commands are expected to install.

sometimes follows a formula something like this...


```
./configure --*options* **or** sh autogen.sh **or** ./whoknowswhat  
make 
sudo make install
```

---

### Post by billy2 on 2013-08-16
There are some installation notes.  They say to modify the Makefile.config file to work on my computer (I am confident I did this correctly because I have already installed one part of this program correctly using said file) then type "make INSTALL" and that's about it.

---

### Post by Petro Dawg on 2013-08-16
> **billy2 said:**
> Hi all,  I am new here and would appreciate any help.  I am trying to install a C program on Ubuntu 13.04 but ran into a problem with permissions (I think).

When i type "make INSTALL" in the terminal, it begins to work then comes up with this:
make: [/**path**/bin/formod_aniso] Error 1 (ignored)
chmod: cannot access '/**path**/bin/formod_aniso': No such file or directory
make: ***[/**path**/bin/formod_aniso] Error 1

I have permission to read and write the bin directory, so I do not understand why there is an error creating the file.  If I manually create the file then try to do "make INSTALL" there are no errors but the file is empty and the program doesn't work.

Thanks

do you really have a folder called **path**?  did that get put in the config file accidently by chance?

---

### Post by billy2 on 2013-08-16
No, path is not an actual folder. I just replaced the long sequence of directories that this is actually under with it for the purposes of posting it here.

---

### Post by Petro Dawg on 2013-08-16
The full output of the file path might be helpful in diagnosing why the make file doesn't believe the target exists.  I would verify the path is typed correctly in the config file by opening a terminal and trying to change to the target directory "cd **/path**" by copying and pasting the file path from the config file into the terminal window.

---

### Post by billy2 on 2013-08-16
I defined CWPROOT as:

[COLOR=#7A0874]**export**[/COLOR] [COLOR=#007800]CWPROOT[/COLOR]=**path**

and the Makefile has:

include $(CWPROOT)/src/Makefile.config
B = $(CWPROOT)bin

where **path**/bin is the directory where the file is supposed to be created in.

---

