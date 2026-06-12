---
title: "what is the safest way to install the virtual instance of Ubuntu on my laptop?"
date: 2015-09-09
forum: General Help
---

### Post by shahin on 2015-09-09
Greetings-
I have a Ubuntu Virtual Machine, which I have installed software and configured, but I am tired of the memory overhead associated with running the VM on my Windows machine. If there was a way for me to safely transfer the VM on to my laptop, and just run Ubuntu natively (I guess that the right term), I would do it. What is the best way to do this? 
Thanks in advance 
Sean

---

### Post by grahammechanical on 2015-09-09
I do not think that there is a way to transfer.

You need to install Ubuntu on that laptop and may be dual boot with any other OS on it. And then set up Ubuntu the way you like it. It should be possible to transfer data files to a USB memory stick and then transfer them on to the laptop. 

Keep in mind that in the VM it is Windows that is communicating with the hardware. In a hard disk install it would be Ubuntu that does the communicating with the hardware and the OS will need to install hardware driver modules appropriate for the hardware of the laptop. This will happen during installation.

---

### Post by shahin on 2015-09-09
> **grahammechanical said:**
> I do not think that there is a way to transfer.
Thanks. I wonder if anyone has put together a sticky on how to transfer a VM image as thoroughly as possible? I mean something like:
1- run the command ... to get a list of all the installed packages
2- run the command ... to copy all user configured settings, scripts, etc. 
3- ...

---

### Post by MartyBuntu on 2015-09-09
I think **RoboLinux** has the ability to do what you're doing. Go grab the live disk and test it out.
I have **RoboLinux **installed in a VirtualBox instance, but I've never explored that specific duty which you're referring to.

---

### Post by tgalati4 on 2015-09-10
First, back up your /home/shahin directory to a USB stick.  You want to make sure you get your personal data backed up.

Then follow:  [http://askubuntu.com/questions/17823/how-to-list-all-installed-packages](http://askubuntu.com/questions/17823/how-to-list-all-installed-packages)

This makes a list of installed packages.  Save the text file to your USB stick.  Then use the file to install these packages into your new, clean Ubuntu installation.  Be sure to install all updates immediately after your initial installation.  This will take some time.

Then selectively copy personal data files to your new home directory.  Don't copy the entire directory because it may over write fresh configuration files for your newly installed apps--and that can cause breakage.

Simply trying to turn a VM image into hard disk ISO image sounds good on paper, but in practice you will have problems.  I'm not aware of a simple method to do this, so you are left with a clean install and reinstallation of your packages.

---

