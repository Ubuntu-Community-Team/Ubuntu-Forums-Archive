---
title: "how to install mediubuntu"
date: 2007-07-06
forum: General Help
---

### Post by zig1234 on 2007-07-06
im a linux noob and need to know how to install mediubuntu for dvds and stuff

---

### Post by tgm4883 on 2007-07-06
> **zig1234 said:**
> im a linux noob and need to know how to install mediubuntu for dvds and stuff

[http://ubuntuforums.org/showthread.php?t=413626](http://ubuntuforums.org/showthread.php?t=413626)

Searching is wonderful.  Stickies are better.

---

### Post by zig1234 on 2007-07-06
man that just more confusing :-(

i get stuck here:

Add the following lines to add the Medibuntu repository to the file:


Quote:
## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free

---

### Post by tgm4883 on 2007-07-06
> **zig1234 said:**
> man that just more confusing :-(

i get stuck here:

Add the following lines to add the Medibuntu repository to the file:



## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free

How?  It gives you step by step instructions.

> Edit the file /etc/apt/sources.list using either of the following commands in a terminal:
```


$gksudo gedit /etc/apt/sources.list
```

to open it in the GUI text editor

or

```
$sudo vim /etc/apt/sources.list
```

to open it in the Vim command line text editor


Add the following lines to add the Medibuntu repository to the file:

```
## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
```

Add the last 4 lines to the file it has you open.  Then continue the guide.

---

### Post by zig1234 on 2007-07-06
except for the first code the rest do nonthing when i copy and paste them in the terminal

---

### Post by tgm4883 on 2007-07-06
> **zig1234 said:**
> except for the first code the rest do nonthing when i copy and paste them in the terminal

What are you pasting in the terminal?

---

### Post by zig1234 on 2007-07-06
ya

---

### Post by tgm4883 on 2007-07-06
> **zig1234 said:**
> ya

?

---

### Post by zig1234 on 2007-07-06
the guide says paste them in the terminal and thats what im doing

---

### Post by zig1234 on 2007-07-06
the code thats what im pasting in the terminal

---

### Post by tgm4883 on 2007-07-06
> **zig1234 said:**
> the code thats what im pasting in the terminal

Do this in terminal
```

gksudo gedit /etc/apt/sources.list
```

then add this to the bottom of the file that opens
```

## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on https://launchpad.net/products/medibuntu/+bugs
deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free
```

Then save the file and continue the guide.  Let me know if there are more problems.

---

### Post by airtonix on 2007-11-06
for future reference.....

whenever you see 

$

it means that its the start of a terminal command.

---

### Post by reachme_anywhere on 2008-02-08
[FONT="Tahoma"]Hi All,

Just installed Ubuntu 7.10 
Can some one share the installation document for how to install mediubuntu !
[/FONT]
[FONT="Arial"]The software I'm looking for is to be able to make calls from Computer to Computer over net.[/FONT]

Is there a complete packaged software suite that does the following:
Work with Yahoo, Rediff Messengers and as well talk to them using PC-PC 

Thanks

---

### Post by confused57 on 2008-02-08
> **reachme_anywhere said:**
> [FONT="Tahoma"]Hi All,

Just installed Ubuntu 7.10 
Can some one share the installation document for how to install mediubuntu !
[/FONT]
[FONT="Arial"]The software I'm looking for is to be able to make calls from Computer to Computer over net.[/FONT]

Is there a complete packaged software suite that does the following:
Work with Yahoo, Rediff Messengers and as well talk to them using PC-PC 

Thanks

I believe this is what you're looking for:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by reachme_anywhere on 2008-02-09
[FONT="Tahoma"]Hi [/FONT]

Thanks a lot this has worked like charm.

Can you please help with the following two as well:

* If I want to make phone calls from my PC-PC through internet which software in this library of mediubuntu will useful !

* All these updates and packages are getting installed into / partition in Ubuntu! Are they not supposed to be using /usr partition ?

I have used Redhat & Fedora there when I create a /usr partition automatically it is recognized and all the installations will go into /usr

Updates going into / in Ubuntu does not seem to be a healthy idea.
Is there anyway the updates can be forced to go into /usr instead of /[root] 

regards,

---

### Post by tgm4883 on 2008-02-09
> **reachme_anywhere said:**
> [FONT="Tahoma"]Hi [/FONT]

Thanks a lot this has worked like charm.

Can you please help with the following two as well:

* If I want to make phone calls from my PC-PC through internet which software in this library of mediubuntu will useful !

* All these updates and packages are getting installed into / partition in Ubuntu! Are they not supposed to be using /usr partition ?

I have used Redhat & Fedora there when I create a /usr partition automatically it is recognized and all the installations will go into /usr

Updates going into / in Ubuntu does not seem to be a healthy idea.
Is there anyway the updates can be forced to go into /usr instead of /[root] 

regards,

How is this related to medibuntu?  Are you looking for some VOIP support?

---

### Post by zvacet on 2008-02-10
@ zig1234


Programs>accessories>terminal run this command


```
gsudo gedit /etc/apt/sources.list
```

You will see your source list file and to that file add at the bottom this line

deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free

Save and close the file.Again from terminal

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -
```

```
sudo apt-get update
```

Now you have medibuntu repository in your source list and you can go to the synaptic and install packages you need from medibuntu.In synaptic search box type paackage name and synaptic will find it.Just mark for install and apply.

---

