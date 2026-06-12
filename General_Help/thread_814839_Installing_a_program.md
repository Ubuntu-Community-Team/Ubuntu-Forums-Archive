---
title: "Installing a program"
date: 2008-06-01
forum: General Help
---

### Post by PhDP on 2008-06-01
I tried to install a program (MatLab), but it doesn't seem to work like WIN. First, I had no idea where to put it, so I choose to put it inside my personal folders.

But now, it's suppose to be installed, and there's no .exe in the folder, no "MatLab" in the "Applications" menu, no MatLab in the "Add/Remove" section...

---

### Post by LaRoza on 2008-06-01
> **PhDP said:**
> I tried to install a program (MatLab), but it doesn't seem to work like WIN. First, I had no idea where to put it, so I choose to put it inside my personal folders.

But now, it's suppose to be installed, and there's no .exe in the folder, no "MatLab" in the "Applications" menu, no MatLab in the "Add/Remove" section...

I don't understand. This is a Linux version of MatLab. You have the directory in your home folder. 

It is not installed. It is in your home folder. There will be no ".exe" or ".msi" in it, because they are Windows file extensions. 

You will have to install it. There are probably instructions for that in the directory.

If you did install it, you can run it using the command line.

---

### Post by PhDP on 2008-06-01
> **LaRoza said:**
> I don't understand. This is a Linux version of MatLab. You have the directory in your home folder.

Well, I don't know about that, they asked me where to install it, and I installed it in "[username]/program/MatLab" (I had no idea where to put it).

> **LaRoza said:**
> If you did install it, you can run it using the command line.

How ?

And how can I uninstall a program ?

How can I add Matlab in my "Applications" menu ?

---

### Post by vvvladut on 2008-06-01
Try opening a terminal and just type **matlab** in it - and see what happens.

How did you install it?

---

### Post by ibuclaw on 2008-06-01
> **PhDP said:**
> 
How ?

Open a terminal and **cd** to the directory where the MatLAB is.
Then type in **ls** to view the contents.
All executable files should be highlighted in green.

Then to run the file, type in
```
./filename
```
The constant is the "**./**" part. filename is the name of the file.

> **PhDP said:**
> 
And how can I uninstall a program ?

If it's installed in an isolated folder, just remove the folder to uninstall it.


> **PhDP said:**
> 
How can I add Matlab in my "Applications" menu ?
Right-Click on the applications tab and select "Edit Menus".

Regards
Iain

---

### Post by PhDP on 2008-06-01
I used the "install" file on the DVD, and it seemed to work fine, they asked where to put the file, what packages to install, and then they "installed it".

---

### Post by PhDP on 2008-06-01
> **tinivole said:**
> Open a terminal and **cd** to the directory where the MatLAB is.
Then type in **ls** to view the contents.
All executable files should be highlighted in green.

Then to run the file, type in
```
./filename
```
The constant is the "**./**" part. filename is the name of the file.

Great, it's just like DOS :)

There are no executable files, but there's a "liscences" file, perhaps I need to do something with it (it's highlighted in blue).

---

### Post by vvvladut on 2008-06-01
This DVD that you installed from...you're sure it is Matlab for Linux, right?

Just asking...

---

### Post by PhDP on 2008-06-01
> **vvvladut said:**
> This DVD that you installed from...you're sure it is Matlab for Linux, right?

Just asking...

Yes.

But it doesn't make any sense, the MatLah folder is less than 1 mo big...

---

### Post by vvvladut on 2008-06-01
I don't know anything about how Matlab for Linux installs, but did you try typing matlab in a terminal? What does it do?

---

### Post by PhDP on 2008-06-01
I tried "Matlab", "matlab", "MatLab", and it does nothing.

I would like to try to reinstall it, but I'm sure 100% sure it's safe to delete the MatLab folder I created.

---

### Post by vvvladut on 2008-06-01
If it's in your home folder, I think it is.

Sorry, I'm a newbie myself and have never installed Matlab so don't know how to help, except tell you to pay attention to the installation instruction and whatever the installer says when installing. And yes, try to reinstall, I'm sure you won't break anything.

---

### Post by LaRoza on 2008-06-01
Please explain the process. I am very confused. Who is "they" who said it was installed?

---

### Post by PhDP on 2008-06-01
Ok, I was successful to a point this time... but it's still a mess, I can't believe how complicate it is to install Matlab on Ubuntu.

So, I used the 'install' file on the DVD to install Matlab, I chose the directory (I still have no idea where programs are normally installed) and select the 'Linux' option, and it was installed. At the end of the installation, I was asked if I wanted to open Matlab, I said yes, and yea, Matlab work...

But for some reason, I can't open Matlab with the console, I can't open it from the directly where it's installed (there's no exe file), and MatLab is not in 'Applications'.

---

### Post by magnus0 on 2008-06-01
> 
But for some reason, I can't open Matlab with the console, I can't open it from the directly where it's installed (there's no exe file), and MatLab is not in 'Applications'.

What do you mean .exe? There's no such thing as .exe in Linux, that's only in Windows.

---

### Post by Joeb454 on 2008-06-01
From a console (terminal) type ```
which matlab
``` what does that return?

---

### Post by PhDP on 2008-06-01
> **Joeb454 said:**
> From a console (terminal) type ```
which matlab
``` what does that return?

Nothing, absolutely nothing. Not even a "there is no such thing as ..."

---

### Post by Joeb454 on 2008-06-01
Strange - yet you say Matlab is installed?

---

### Post by PhDP on 2008-06-01
I solved the problem, apparently, you need to install Matlab from the dvd, but then you need to run 'sudo .../matlab_install', I'm not sure to know what it does exactly, but it seems to integrate matlab into ubuntu.

---

### Post by Joeb454 on 2008-06-01
I'm guessing it copies the files from the DVD to your Ubuntu install, and then requires you to run some sort of install file to set it all up correctly.

---

