---
title: "Problems with synaptic"
date: 2007-09-16
forum: General Help
---

### Post by Pusur on 2007-09-16
Hi. The problem is basically this:

I tried to install VirtualBox, but it startet hanging, and I cancelled the installation. And now, if i even try to start Synaptic, or anything using apt-get/aptitude, I get the error "E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.". If i try to start the .deb-file, I get the error "Failed to open the software package
The package might be corrupted or you are not allowed to open the file. Check the permissions of the file.". What is wrong, and what can I do to fix this?

---

### Post by nowshining on 2007-09-16
what did you start to install from .deb file or synaptic ??

---

### Post by Pusur on 2007-09-16
I started installing the .deb-file, with GDebi.

---

### Post by nowshining on 2007-09-16
so a double-clic then

did you follow the instructions on screen, because it should of asked you some instructions and asked u if you would of like to unload something - don't remember but I remember I had to when i installed it. :) that's probably what happened if you didn't actually read the output of the terminal - which is always best to do because many packages may ask one to agree to a EULA, inform one of some incompatibilites..

do this for me

applicaitons - accessories - terminal

type

uname -r

hit enter and post the output..

---

### Post by Pusur on 2007-09-16
2.6.20-16-generic...

---

### Post by nowshining on 2007-09-16
I asked that because on ur profile u didn't put what ubuntu or linux version u were running - okay its  feisty fawn :) 7.04 with all updates...I hope...

---

### Post by nowshining on 2007-09-16
in the terminal type

```

sudo apt-get install -f

```

hit enter and enter your password

Note the password when typing will not show up neither in plain text or astricks so just type it out as you usually would and then hit enter..

post the output :)

---

### Post by koer on 2007-09-16
> **nowshining said:**
> in the terminal type

```

sudo apt-get install -f

```

hit enter and enter your password

Note the password when typing will not show up neither in plain text or astricks so just type it out as you usually would and then hit enter..

post the output :)

i got the same problem as him and i followed what you said , the output is :"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 


HELP?

---

### Post by Pusur on 2007-09-16
```
sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.

```

Same as before...

Koer: Run the command?

---

### Post by nowshining on 2007-09-16
koer thanks for your input do that in the termina but with sudo


in other words it could benefit them too

so in the terminal

type

```

sudo dpkg --configure -a

```

i've never done it so i have no clue what it asks.. but if you want you can ask on this thread or open up a new one..

---

### Post by nowshining on 2007-09-16
so far for me it just went back to the command prompt which means what it did was successful - whatever that is..

---

### Post by nowshining on 2007-09-16
also i found this

in the terminal

type

```

cd /var/lib/dpkg/updates

```

then  type
```

sudo rm *

```

Pusur you can try that too..

---

### Post by Pusur on 2007-09-16
Thank's for the help, it's now working again! ^^

Koer, try to run "sudo dpkg --install <nameofpackage>.deb" in a terminal.

---

### Post by nowshining on 2007-09-16
ur welcome :)

thanks to koer for his/her post as it was their post that did put us on the right track for a fix..

---

### Post by koer on 2007-09-16
i typed  sudo dpkg --configure -a
and then it shows the koer@UBUNTU: again ,
i run synaptic and it shows:
"E: The package virtualbox needs to be reinstalled, but I can't find an archive for it."
"E: Internal error opening cache (1). Please report."

i try to open the .deb file for virtualbox and it shows:
"could not open virtualbox_1.5.0-24069-1_ubuntu_feisty_i386.deb"
"The package might be corrupted or you are not allowed to open the file. check the permissions of the file"

of gees, and now firefox is crashing for no reason, im really screwed on this one :(

and more i try running sudo dpkg --install virtualbox_1.5.0-24069-1_Ubuntu_feisty_i386.deb and it says:

"dpkg: error processing virtualbox_1.5.0-24069-1_Ubuntu_feisty_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 virtualbox_1.5.0-24069-1_Ubuntu_feisty_i386.deb"

---

### Post by Maestro23 on 2007-09-16
> **koer said:**
> i typed  sudo dpkg --configure -a
and then it shows the koer@UBUNTU: again ,
i run synaptic and it shows:
"E: The package virtualbox needs to be reinstalled, but I can't find an archive for it."
"E: Internal error opening cache (1). Please report."

i try to open the .deb file for virtualbox and it shows:
"could not open virtualbox_1.5.0-24069-1_ubuntu_feisty_i386.deb"
"The package might be corrupted or you are not allowed to open the file. check the permissions of the file"

of gees, and now firefox is crashing for no reason, im really screwed on this one :(

and more i try running sudo dpkg --install virtualbox_1.5.0-24069-1_Ubuntu_feisty_i386.deb and it says:

"dpkg: error processing virtualbox_1.5.0-24069-1_Ubuntu_feisty_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 virtualbox_1.5.0-24069-1_Ubuntu_feisty_i386.deb"

Try this in terminal for the virtualbox .deb

> sudo dpkg --force-remove-reinstreq –remove pkgname

---

### Post by koer on 2007-09-16
this is what i get :
jaime@UBUNTU:~$ sudo dpkg --force-remove-reinstreq –remove virtualbox_1.5.0-24069-1_Ubuntu_feisty_i386.deb
dpkg: need an action option

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !

what do i do now ?

---

### Post by Pusur on 2007-09-16
Did you try ```
"sudo dpkg --install <nameofpackage>.deb" 
```?

---

### Post by koer on 2007-09-16
> **Pusur said:**
> Did you try ```
"sudo dpkg --install <nameofpackage>.deb" 
```?

yes i did , it gave me this:

koer@UBUNTU:~$ sudo dpkg --install virtualbox_1.5.0-24069-1_Ubuntu_feisty_i386.deb
Password:
dpkg: error processing virtualbox_1.5.0-24069-1_Ubuntu_feisty_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 virtualbox_1.5.0-24069-1_Ubuntu_feisty_i386.deb
koer@UBUNTU:~$ 

is there a way to reinstall synaptic ? or that wont fix it ?

---

### Post by nowshining on 2007-09-16
try the following commands then

```

sudo apt-get update
sudo apt-get clean

```

---

### Post by koer on 2007-09-17
> **nowshining said:**
> try the following commands then

```

sudo apt-get update
sudo apt-get clean

```

nope still wont work, it shows the same errors as before ....

---

### Post by koer on 2007-09-17
> **nowshining said:**
> also i found this

in the terminal

type

```

cd /var/lib/dpkg/updates

```

then  type
```

sudo rm *

```

Pusur you can try that too..

okay im sure the solution is this, i  change the directory and type "sudo rm" but what does * mean ?

---

### Post by nowshining on 2007-09-17
the astrick means to remove all it's a wildcard :) in other words it will delete every folder and or file in the updates folder. :) no need to delete them one by one.

---

### Post by koer on 2007-09-18
this is what i get:
```
koer@UBUNTU:~$ cd /var/lib/dpkg/updates
koer@UBUNTU:/var/lib/dpkg/updates$ sudo rm *
Password:
rm: cannot remove `*': No such file or directory
```

---

### Post by koer on 2007-09-18
> **koer said:**
> this is what i get:
```
koer@UBUNTU:~$ cd /var/lib/dpkg/updates
koer@UBUNTU:/var/lib/dpkg/updates$ sudo rm *
Password:
rm: cannot remove `*': No such file or directory
```

woops , okay i got synaptic working now , i just had to reinstall virtualbox , it was easy i just had to specify the route of the packge!

anyways, i was glad to help , and thank you all for the help also :D

:popcorn:

---

### Post by nowshining on 2007-09-18
ur welcome and your response will help others if they have the same problem in the future. :)

---

