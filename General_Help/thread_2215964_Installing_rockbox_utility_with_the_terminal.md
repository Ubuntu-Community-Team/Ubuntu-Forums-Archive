---
title: "Installing rockbox utility with the terminal"
date: 2014-04-09
forum: General Help
---

### Post by aneblanc on 2014-04-09
I am trying to install Rockbox on an Ipod classic. I have installed the Rockbox Utility program with Ubuntu Software Centre and started it. When I click on "install" it says: "Could not open Ipod, permission denied". 

What is the command to use in the terminal to install it?

Thanks

---

### Post by grier-devon on 2014-04-09
Which generation of ipod classic are you trying to install on?

---

### Post by aneblanc on 2014-04-09
5th Generation 30Gb

---

### Post by slickymaster on 2014-04-09
> **aneblanc said:**
> I am trying to install Rockbox on an Ipod classic. I have installed the Rockbox Utility program with Ubuntu Software Centre and started it. When I click on "install" it says: "Could not open Ipod, permission denied". 

What is the command to use in the terminal to install it?

Thanks

See this: [Rockbox on IPOD and permission denied]("http://ubuntuforums.org/showthread.php?t=1115319&p=7342321&viewfull=1#post7342321")

---

### Post by aneblanc on 2014-04-09
I did the following but I don't see the option: "use a custom command"

[I]download the Rockbox automatic installer from [http://www.rockbox.org/twiki/bin/vie...ility#Download](http://www.rockbox.org/twiki/bin/vie...ility#Download) and extract it. Then right click on the executable and click on "open with other application..." Instead of selecting a program, go down to the arrow where it says "use a custom command" and simply type in 
Code:
gksu
[/I]

---

### Post by slickymaster on 2014-04-09
> **aneblanc said:**
> I did the following but I don't see the option: "use a custom command"

[I]download the Rockbox automatic installer from [http://www.rockbox.org/twiki/bin/vie...ility#Download](http://www.rockbox.org/twiki/bin/vie...ility#Download) and extract it. Then right click on the executable and click on "open with other application..." Instead of selecting a program, go down to the arrow where it says "use a custom command" and simply type in 
Code:
gksu
[/I]

When you right-click it, you have the option "Open With Other Application..." <- click it and it will open a dialog box where you'll find the "Use a custom command:" option in the bottom.

---

### Post by aneblanc on 2014-04-09
I did right click on the executable file Rockbox Utility then clicked on "Open with other application", it opens a box called "Select an application to open Rockbox Utility" with "Recommended applications" and "Show other applications". I clicked on the latter option but there is nowhere "Use a custom command:" option.

Couldn't I use the terminal instead as I originally asked? I just don't know the command and where to find the program.

---

### Post by slickymaster on 2014-04-09
See the pictures bellow.

1. "Use custom command:" in the 'Open With' dialog
[ATTACH=CONFIG]251869[/ATTACH]

2. Click the arrow at the left of the "Use custom command:" phrase opens a text box where you type the **gksu** command and hit the 'Open' button:
[ATTACH=CONFIG]251870[/ATTACH]

---

### Post by aneblanc on 2014-04-09
Believe or not but I don't have that option! Sorry about that. Any other idea?

---

### Post by slickymaster on 2014-04-09
After spending some time searching, since I don't ever used it before, I went ahead and manage to install in a Virtual Machine just using the terminal.

[The official website]("http://www.rockbox.org/wiki/RockboxUtility#Download") only provides source code for Ubuntu users, but [GetDeb repository has added Rockbox Utility packages for Ubuntu 12.04 and higher]("http://www.getdeb.net/software/rbutil"), so what I did was to add GetDeb repository by running the follwoing in a terminal window:```
wget http://archive.getdeb.net/install_deb/getdeb-repository_0.1-1~getdeb1_all.deb
sudo dpkg -i getdeb-repository_0.1-1~getdeb1_all.deb
```After that I just installed Rockbox Utility, running:```
sudo apt-get update
sudo apt-get install rbutil
```

---

### Post by aneblanc on 2014-04-09
I tried to install rbutil with this

~$ sudo apt-get install rbutil
Reading package lists... Done
Building dependency tree       
Reading state information... Done
rbutil is already the newest version.

Then I tried to run it with

~$ rbutil
No command 'rbutil' found, did you mean:
 Command 'dbutil' from package 'mailavenger' (universe)
rbutil: command not found

Then I tried this too

~$ sudo rbutil
sudo: rbutil: command not found

Don't know what to do next, probably try another forum.

Thanks a lot anyway for spending your time with my little problem.

---

### Post by Yellow Pasque on 2014-04-09
Well, then the binary is not named rbutil. To figure out the name of the binary, look at
```
dpkg -L rbutil
```
The binary will probably be installed in /usr/bin
```
gksu binaryname
```

---

### Post by aneblanc on 2014-04-10
Thanks. Your help was precious. I installed rockbox on the ipod though it doesn't load. I have to try again...

---

