---
title: "[SOLVED] install IE6"
date: 2007-08-02
forum: General Help
---

### Post by DougieFresh4U on 2007-08-02
I'm having a problem installing ie6.  Seems I interupted something and noe terminal gives messege 'internet explorer needs to be reinstalled but I can not find archive for it'. Can some one please help me clean up this mess. I don't know what to do:confused
Please let me know what more info you need, thanks

---

### Post by DougieFresh4U on 2007-08-02
I get this in terminal
[B]dougie@DougiesLeanMachine:~$ sudo apt-get remove iceape
[sudo] password for dougie:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package internet-explorer-6-ubuntu needs to be reinstalled, but I can't find an archive for it.
dougie@DougiesLeanMachine:~$[/B]

Please help, I can not open synaptic and can not run any thing in terminal

---

### Post by FleetAdmiral74 on 2007-08-02
When you fix synaptic, might try [http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)

Worked fine for me.

---

### Post by DougieFresh4U on 2007-08-03
Some one please rescue me:lolflag:

---

### Post by DougieFresh4U on 2007-08-03
Desperate for help please!!!!!

---

### Post by DougieFresh4U on 2007-08-03
[COLOR="Red"][SIZE="5"]**BUMP**[/SIZE][/COLOR]

---

### Post by Seisen on 2007-08-03
How did you install in it anyway?

---

### Post by DougieFresh4U on 2007-08-03
> **Seisen said:**
> How did you install in it anyway?

Thank you for your interest. 
I do not believe its installed or it was stopped during install as it's not any where to be found :confused: I think it was the .deb file provided n a thread on forum here. 
As you can see from screenshot, I cannot access synaptic and terminal gives message. 
Is there a way to purge in terminal or some way to locate any file having to do with IE?

---

### Post by DougieFresh4U on 2007-08-03
Please help! I can't update or or use terminal, please help me:(

---

### Post by DougieFresh4U on 2007-08-03
Sorry for all the BUMPS, but I'm a getting desperate, as I need my terminal and terminal won't let me use it as I keep getting internet explorer messege (shown in screenshot post)

---

### Post by splintercellguy on 2007-08-03
Try removing the package with sudo apt-get remove <wutever the package name is>. And have you tried ies4linux?

---

### Post by DougieFresh4U on 2007-08-03
> **splintercellguy said:**
> Try removing the package with sudo apt-get remove <wutever the package name is>. And have you tried ies4linux?

Thanks for reply!
I have tried to remove but keep getting terminal messege about needing to install internet explorer 6. 
Is there some code for purge and remove package?

---

### Post by splintercellguy on 2007-08-03
Try sudo dpkg --force-remove-reinstreq --remove <name of the package> (obtained from [https://answers.launchpad.net/ubuntu/+source/gnome-utils/+question/7350](https://answers.launchpad.net/ubuntu/+source/gnome-utils/+question/7350)).

---

### Post by DougieFresh4U on 2007-08-03
> **splintercellguy said:**
> Try sudo dpkg --force-remove-reinstreq --remove <name of the package> (obtained from [https://answers.launchpad.net/ubuntu/+source/gnome-utils/+question/7350](https://answers.launchpad.net/ubuntu/+source/gnome-utils/+question/7350)).

[B]dougie@DougiesLeanMachine:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package internet-explorer-6-ubuntu needs to be reinstalled, but I can't find an archive for it.
dougie@DougiesLeanMachine:~$  sudo dpkg --force-remove-reinstreq --remove internet-explorer-6
dpkg - warning: ignoring request to remove internet-explorer-6 which isn't installed.
dougie@DougiesLeanMachine:~$[/B] 
I don't know how to proceed as I just installed IE6 from tankas and have icon on desktop

---

### Post by splintercellguy on 2007-08-03
That's not the name of the package :). sudo dpkg --force-remove-reinstreq --remove internet-explorer-6-ubuntu

---

### Post by DougieFresh4U on 2007-08-03
> **splintercellguy said:**
> That's not the name of the package :). sudo dpkg --force-remove-reinstreq --remove internet-explorer-6-ubuntu

Thank you so much you are the guru. All fixed and terminal is working great!!
Thank you again, you are the greatest:)

---

