---
title: "can't install java runtime"
date: 2007-12-20
forum: General Help
---

### Post by meharts on 2007-12-20
Hi again, I have Ubuntu server7.10 and have just upgraded the distro. I have tried to install java runtime which seems to be missing after the upgrade. 
I try using apt, but when it asks for the cd it wont take the info from the cd. It keeps on trying to load from the cd and that rolls on the screen.

I have no desktop environment to work with - unnecessary clutter. I have tried using webmin to install it but I had  the error  explained above.

Does anyone know how I can install java back on the computer? I have tried working from the command line but get the same problem?

Unfortunately there isn't a console to work from either!!

I would appreciate any help I can get on this one.

meharts

---

### Post by tshrinivasan on 2007-12-20
do you have net connection with that server?

if you have,
just uncomment the line for CD in the file
/etc/apt/sources.list

the  run apt-get update.

now run apt-get install sun-java6-jre

this will install jre form the internet.

---

### Post by meharts on 2007-12-21
Thanks for stopping by tshrinivasan! I appreciate what you are saying - but how do I amend the sources.list? I have no console?

meharts

---

### Post by meharts on 2007-12-21
Ok tried to use nano to edit sources.list, but get a terminal error?!!

meharts

---

### Post by Partyboi2 on 2007-12-21
to open your source.list
```
gksudo gedit /etc/apt/sources.list
``` or
```
 sudo nano /etc/apt/sources.list
```
If you need help with it, post your sources.list

---

### Post by meharts on 2007-12-21
Hi Partyboi2, I haven't a problem with editing the sources.list - just can't get access to it!!

I haven't gksudo and if you look at the previous post I get an error when trying to run nano from a command shell I get the following:

> 

> sudo nano  /etc/apt/sources.list
Error opening terminal: unknown.



If you know what that problem can be, then I am all ears:)


meharts

---

### Post by Partyboi2 on 2007-12-21
Is it just nano you are not able to use? What happens if you use vim instead of nano?

---

### Post by meharts on 2007-12-21
Nothing seems to work!!

I ran apt-get install apt-get install sun-java6-jre from the command shell and the screen goes blank but seems to be working. There is indication that the processor is working with something...... it then says finished but there is now java?!! I use java runtime for my package handler on webmin. I rebooted but nothing had changed. I get the list of packages to be installed and how much space they will take - do you want to continue - which I of course write the command yes and then a blank screen!!!

I am fast loosing interest in Ubuntu!! I don't mind working with different issues but this is ridiculous. Not a happy bunny at the mo:(

meharts

---

### Post by eapache on 2007-12-21
I am going to summarize the situation, please correct me if I am wrong:

You boot up the server version of Ubuntu, and it leaves you at a login prompt. You login and end up with the bash prompt. When you try apt-get it doesn't work. When you try nano, it doesn't work.

If the above is approximately correct, please try the following:
- insert the cd in the drive```
sudo apt-get update
sudo apt-get install nano
```This installs nano from the cd. Then open up sources.list and connect to the server following the previous instructions. Then try the apt-get update and apt-get install for java again.

---

### Post by meharts on 2007-12-21
Nano is installed I just get errors saying "Error opening terminal: unknown"


I will have to do a reinstall!!

Beginning to wonder why Ubuntu is so popular?!!

I am not connected to the computer through my monitor the server is part of my home network.

That is why I have webmin, so I don't need a desktop environment and I don't need to be connected to it through my monitor.

meharts

---

### Post by meharts on 2007-12-21
Sorry guys!! I having a bad back day and my patience isn't in best form:)

I do appreciate your help! Going to Ireland on Sunday and didn't need any computer issues before I go!

meharts

---

### Post by meharts on 2008-01-02
Well, I suppose that no one has the answer to my problem. so I think I will ditch Ubuntu and go with Clark Connect instead.

I appreciate that it was my fault that  I upgraded the distro by mistake - just thought someone would have some sort of solution.

Might do a re install as well. Sorry, rambling on again.

Thanks for your help.

Meharts

---

