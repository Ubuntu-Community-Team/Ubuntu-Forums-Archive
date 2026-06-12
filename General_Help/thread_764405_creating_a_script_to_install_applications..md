---
title: "creating a script to install applications."
date: 2008-04-23
forum: General Help
---

### Post by JAGGEDSPHERE on 2008-04-23
I would like to create a script that I would add a number of apt-get install someprogram commands
HH comes out soon and I would like to compile a list of applications I need to install to get my OS 'just so'
Does anyone have a link to a tutorial for making a script that could do such a thing?

---

### Post by alixthedark on 2008-04-23
why dont you just go to the konsole and type:    
*sudo apt-get install* [package_name]

---

### Post by Vadi on 2008-04-23
Yeah, no script needed - just copy down the name of the packages you'd like, and then do "sudo apt-get install *package1* *package2 package3* ...".

Keep in mind though that unless you'll be reinstalling ubuntu completely, you won't need to reinstall your programs after an upgrade.

---

### Post by girishv on 2008-04-23
I use another method. I made separate partition for /usr/local and most of my additional software is installed in it. For the software from ubuntu, I can use the list of installed programs on the present OS with dpkg --list and use it when I upgrade the OS.

NOTE: For some strange reason, my /usr/local also got wiped out when I tried HH beta. Lucky, I had a backup. Now, I wont mount /usr/local during installation, but, edit later


Girish

---

### Post by JAGGEDSPHERE on 2008-04-24
So what about if I have a mix. lets say I have a collection of tarballs, debs and stuff in the repos and I just want to have all of these programs install in one action?

Edit: I know I can just copy/paste commands into the terminal but I want to learn a little about Linux and thought that making a script that would run a list of commands would be a good exercise.

---

### Post by LausArndon on 2008-04-24
A simple way to do it is just to type the commands straight in to the script.

```
apt-get install package-1
apt-get install package-2
apt-get install package-2
```

When the first one is finished installing it will go straight to the next command. What I don't know how to do is to make it answer yes when it asks you if you want to continue. You won't be able to go leave the house and let it do its' thing, but you won't have to remember all the packages you want and type it all in.

It doesn't even look like it should be that hard to do. If anyone know how, let us know. I'm kind of interested in this too.

---

### Post by nsche on 2008-04-24
> **LausArndon said:**
> A simple way to do it is just to type the commands straight in to the script.

```
apt-get install package-1
apt-get install package-2
apt-get install package-2
```
...
try ```
apt-get --yes install package ...
```
whatever commands you would enter to do the task from the command (shell) prompt can be put in a file and that file then executed by a command like ```
sh file
```
Answering questions is a bit harder and there are programs like expect for that but that is a whole 'nother world.

---

### Post by LausArndon on 2008-04-24
I just figured it out. A whole lot more simple than I thought

```
sudo apt-get install package-1 -y
```

As simple as a -y. You'll never even see the prompt. It already knows you say yes and should automatically start the download and install.

---

