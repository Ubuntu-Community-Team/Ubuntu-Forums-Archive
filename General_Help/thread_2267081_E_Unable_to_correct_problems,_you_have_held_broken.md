---
title: "E: Unable to correct problems, you have held broken packages."
date: 2015-02-27
forum: General Help
---

### Post by phuongthengoc on 2015-02-27
sorry every one... I have a trouble for wine... I reinstall Ubuntu for my computer... when I install wine

```
sudo apt-get install wine
```

then Terminal show.

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine : Depends: wine1.6 but it is not installable or
                 wine1.7 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

i tried running
```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

then i repeated the process again. Still I get the same error.

please help me :'(

thanks for reading...

---

### Post by westie457 on 2015-02-27
Welcome phuongthengoc.

Try these commands first. ```
sudo dpkg --configure -a
sudo apt-get install --fix-missing
```Post the output if any errors.

---

### Post by phuongthengoc on 2015-02-27
> **westie457 said:**
> Welcome phuongthengoc.

Try these commands first. ```
sudo dpkg --configure -a
sudo apt-get install --fix-missing
```Post the output if any errors.

thanks for rep
but nothing change.

```
panda@panda:~$ sudo dpkg --configure -a
[sudo] password for panda: 

panda@panda:~$ sudo apt-get install --fix-missing
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

panda@panda:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine : Depends: wine1.6 but it is not installable or
                 wine1.7 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

---

### Post by ian-weisser on 2015-02-27
wine1.7 is not in the Ubuntu repositories.
You are adding a PPA and/or settings that break your newly-reinstalled system.

---

### Post by phuongthengoc on 2015-02-27
> **ian-weisser said:**
> wine1.7 is not in the Ubuntu repositories.
You are adding a PPA and/or settings that break your newly-reinstalled system.

thanks for rep

but i'm the newbie
can you guide me...
how to do fix it

---

### Post by Bucky Ball on 2015-02-27
If you have added a wine PPA manually, Uninstall wine, disable the PPA you've added and install wine from the official Ubuntu repositories (Software Centre/Synaptics).

---

### Post by phuongthengoc on 2015-02-27
> **Bucky Ball said:**
> If you have added a wine PPA manually, Uninstall wine, disable the PPA you've added and install wine from the official Ubuntu repositories (Software Centre/Synaptics).

sory guy...
but how to unintall wine... I tried guide for "https://www.winehq.org/download/ubuntu"
now I don't know uninstall @.@
I don't think I install some wine for my ubuntu

---

### Post by phuongthengoc on 2015-02-27
> **Bucky Ball said:**
> If you have added a wine PPA manually, Uninstall wine, disable the PPA you've added and install wine from the official Ubuntu repositories (Software Centre/Synaptics).

I tried disable PPA 
now terminal show.

```
E: Invalid operation uninstall
panda@panda:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine : Depends: wine1.4 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

:(

---

### Post by dino99 on 2015-02-27
first open a terminal, and run: sudo apt-get purge wine*
then add the wine ppa: [https://launchpad.net/~ubuntu-wine/+archive/ubuntu/ppa](https://launchpad.net/~ubuntu-wine/+archive/ubuntu/ppa) (the easiest way is to add it via 'synaptic', install it if not yet, by copy/paste its address)
update the archive (reload synaptic icon)
and finally install wine1.7 with synaptic

---

### Post by phuongthengoc on 2015-02-27
> **Bucky Ball said:**
> If you have added a wine PPA manually, Uninstall wine, disable the PPA you've added and install wine from the official Ubuntu repositories (Software Centre/Synaptics).

> **9d9 said:**
> first open a terminal, and run: sudo apt-get purge wine*
then add the wine ppa: [https://launchpad.net/~ubuntu-wine/+archive/ubuntu/ppa](https://launchpad.net/~ubuntu-wine/+archive/ubuntu/ppa) (the easiest way is to add it via 'synaptic', install it if not yet, by copy/paste its address)
update the archive (reload synaptic icon)
and finally install wine1.7 with synaptic

thanks guy...
but I don't know where copy and paste in synaptic...
can you tell me 
:)
thanks

---

### Post by ian-weisser on 2015-02-27
> **phuongthengoc said:**
> 
but how to unintall wine... I tried guide for "https://www.winehq.org/download/ubuntu"
now I don't know uninstall @.@

Step 1) Get rid of that PPA that broke your system.

Open System Settings
Click Software & Updates
Click the 'Other Software' tab.
Find the PPA you added. Uncheck the box.
Click 'close'


Step 2) Refresh the dpkg database of all the available packages

Open a terminal
```
sudo apt-get update
```
Close the terminal


Step 3) Install the supported version of Wine that's already in the Ubuntu repositories.

Open Software Center
Enter 'wine' in the search box.
Select wine. Click 'install'


Next time, start with Software Center instead of following random instructions off the dirty, dirty internet.

---

### Post by phuongthengoc on 2015-02-27
> **ian-weisser said:**
> Step 1) Get rid of that PPA that broke your system.

Open System Settings
Click Software & Updates
Click the 'Other Software' tab.
Find the PPA you added. Uncheck the box.
Click 'close'


Step 2) Refresh the dpkg database of all the available packages

Open a terminal
```
sudo apt-get update
```
Close the terminal


Step 3) Install the supported version of Wine that's already in the Ubuntu repositories.

Open Software Center
Enter 'wine' in the search box.
Select wine. Click 'install'


Next time, start with Software Center instead of following random instructions off the dirty, dirty internet.


sorry guy
but about 30 minute ago i tried
```
sudo apt-get purge wine*
```
and now i can't find Software & Updates in system setting
ubuntu software center being uninstall

I tried

```
sudo apt-get install software-center*
```

terminal show

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'software-center-aptdaemon-plugins' for regex 'software-center*'
Note, selecting 'lubuntu-software-center' for regex 'software-center*'
Note, selecting 'software-center' for regex 'software-center*'
software-center-aptdaemon-plugins is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 software-center : Depends: gvfs-backends
                   Recommends: software-properties-gtk but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

now... I think I have a BIG trouble @.@

---

### Post by ian-weisser on 2015-02-27
Yes, quite the mucked-up system you seem to have created.

Do you want to learn how to fix it? Might take a day or two following our step-by-step instructions.
Or do you want to reinstall?

Your choice.

---

