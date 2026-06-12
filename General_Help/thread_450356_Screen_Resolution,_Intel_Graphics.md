---
title: "Screen Resolution, Intel Graphics"
date: 2007-05-21
forum: General Help
---

### Post by Maff88 on 2007-05-21
Hello

I am having a problem getting my MAXDATA laptop to use the correct screen resolution.

Here is that laptop [http://www.barrybennett.co.uk/computers/midrangelaptop.php](http://www.barrybennett.co.uk/computers/midrangelaptop.php)
The Graphics card is a "Graphic Chip Intel® 82945GM Graphics Media Accelerator 950"

I have tried to follow the instructions for "Intel Graphics driver (i810) won't use high screen resolutions" on this page but I seem to get an error.

[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)
 
This is what happens...

> 
matt@matt-laptop:~/Desktop/915resolution-0.5.3$ sudo apt-get install 915resolution
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package 915resolution
matt@matt-laptop:~/Desktop/915resolution-0.5.3$


I’m am very new to Linux and I’m not sure what happening or how to fix it so any help would be great, thanks

Matt

---

### Post by vigleik on 2007-05-21
apt-get can't find the package, probably because you didn't enable the right repository. Do you have something like this:
```
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe
```
in your /etc/apt/sources.list file? I'm assuming you're using 7.04. If you still have trouble, post your /etc/apt/sources.list file.

---

### Post by Maff88 on 2007-05-21
sorry, i dont understand?

How to I enable the right repository?

---

### Post by vigleik on 2007-05-21
Type "gksudo gedit /etc/apt/sources.list". Cut and paste what I wrote in the previous post at the end of the file, and save it. Then try again. (Of course, someone is now going to tell me how there's an easier way to do this.) EDIT: This is still assuming you're using 7.04. If you're using an earlier version then these instructions could break your system.

---

### Post by ghell on 2007-05-21
The "easy way" (longer but probably more fool proof imo) would probably be to just enable universe in synaptic:

System -> Administration -> Synaptic Package Manager
Settings -> Repositories -> Check the "universe" checkbox and close the dialogue
Hit reload

Now you should be able find it in synaptic or use apt-get.

---

### Post by Maff88 on 2007-05-21
Do i need an internet connection for this to work?

The "Community maintained Open Source software (universe)" is checked.

I dont have the internet on the laptop i am running Ubuntu on.

---

### Post by vigleik on 2007-05-21
Thanks for proving me right by providing an easier way. This does indeed reduce the chance of breaking anything if you don't know exactly what you're doing. Maff88: do what ghell said, not what I said.

EDIT: Yes, you do need internet access. That's probably why you failed in the first place. If there's no way for you to get internet access on your laptop, it's still possible to download the required files with another computer and transfer them. That however is more complicated, so I'll leave it to someone else to explain exactly how to do that.

---

### Post by Maff88 on 2007-06-03
Hi

Hope fully somone will read this

I have an Internet connection on my laptop running Ubuntu.

The program seems to install ok, but when i do this

> Once the program is installed you can use the program to list all available vBios modes:

sudo 915resolution -l


i dont get the list of resolutions like in the example

anyone know what I am doing wrong?

Thanks

Matt

---

### Post by bsawler on 2007-07-16
try turning off your X-server.  See here:

[https://help.ubuntu.com/community/i915Driver](https://help.ubuntu.com/community/i915Driver)

---

