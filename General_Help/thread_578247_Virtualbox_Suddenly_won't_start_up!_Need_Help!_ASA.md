---
title: "Virtualbox Suddenly won't start up! Need Help! ASAP"
date: 2007-10-17
forum: General Help
---

### Post by ssc351 on 2007-10-17
Hey guys,

I've got an Ubuntu 7.04 box with Vbox 1.5.0.  I have been running everything great with the upgrade until I started using the shared folders functionality.   Once I did that I noticed my network in the VM stopped working...couldn't ping out, no internet etc...but shared folders still worked.  So I tried disabling the connection...that crashed the VM.  Was able to get back in, somehow the connection got disabled so then I tried enabling it...crashed the machine.  Again, was able to get back in, looked at the connection again still disabled, tried uninstalling the card through control panel. And thats where the problem popped up, now it will start up fine in Safe mode with networking turned off but with normal start up it will get to the blue screen where it asks for a windows logon then aborts. 

a couple other things of note...I am running the seamless deal followed through this thread:  [http://ubuntuforums.org/showthread.php?t=433359](http://ubuntuforums.org/showthread.php?t=433359)
Also, in that thread, I followed a port forwarding so I wouldn't lose Network Manager...see page 22.  And that may be where my problem is coming from.

Here was the last log file:
Log created: 2007-10-17T06:52:43.733529000Z
Executable: /usr/lib/virtualbox/VirtualBox
Arg[0]: /usr/lib/virtualbox/VirtualBox
Arg[1]: -comment
Arg[2]: WinXPpro
Arg[3]: -startvm
Arg[4]: de9a681f-146d-4606-a938-4eff770c9aa3

!!Assertion Failed!!
Expression: RT_SUCCESS(rc)
Location  : /home/vbox/vbox-1.5.0/src/VBox/Devices/Network/DrvNAT.cpp(90) int drvNATSend(PDMINETWORKCONNECTOR*, const void*, size_t)
VERR_SEM_DESTROYED (-363) - Semaphore destroyed while waiting.

Here is the error that popped up:


Unknown configuration in port forwarding.
VBox status code: -2805 (VERR_PDM_DRVINS_UNKNOWN_CFG_VALUES).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 Here is the error that pops up when I uncheck NAT:


Configuration error: Failed to get the "MAC" value.
VBox status code: -2103 (VERR_CFGM_VALUE_NOT_FOUND).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}



Please help! I really need this thing up and running tomorrow to do some major work!

---

### Post by Jose Catre-Vandis on 2007-10-17
a. You don't say what is in your VM, XP ?

b. You don't need to do all that seamless shenanigans in Vbox1.5, it is all taken care of from the command menu (CTRL+L)

c. Have a look here for help on networking using host interface
[http://bimma.me.uk/2007/09/30/ubuntu-creating-host-interface-networking-for-virtualbox/](http://bimma.me.uk/2007/09/30/ubuntu-creating-host-interface-networking-for-virtualbox/)

Suggest maybe a reinstall in Virtualbox to clean things up and reconfigure of your VM to take account of new features

---

### Post by ssc351 on 2007-10-17
Yes, I have XP pro...and I like the way the thread does the seamless better than the integrated VB as well I had it set-up with 1.4 then upgrading to 1.5 after.

How do I reinstall/clean up virtualbox without losing all the data on the guest? Isn't there an image file I can import/save from Ubuntu?

---

### Post by Jose Catre-Vandis on 2007-10-17
Your virtual hard disk can survive a reinstallation. if you used the default locations they are in ```
~/.VirtualBox/VDI
``` Am not sure if the settings survive also, so probably best to make a note of these, and suggest a backup of the virtual hard drive before uninstall.

Re: Seamless, in what way does the manual method exceed the Vbox seamless? I guess the main difference is that you are running a headless rdesktop as opposed to a direct virtual machine? This means you don't have access to the program commands though, e.g. shared folder/USB/CD mounting?

---

### Post by ssc351 on 2007-10-17
So I uninstalled and reinstalled and still get the same thing...
The first thing that pops up is still that port forwarding error.  Is there a way to undo the "port forwarding" as described in the manual seamless link? Is that the problem?

FYI, the VM starts up and gets to the blue screen where is says, " Windows is starting up"

This sucks...thanks for the help.

---

### Post by Jose Catre-Vandis on 2007-10-20
Sorry, it's gone beyond my understanding, but it does look like you probably need to reconfigure the portforwarding area of your setup. Double check what is going on inside your VM and the command line settings for it in Vbox. Might be worth looking through the VM's xml file to see what is in there. (look in the /.VirtualBox/Machines/YourVM folder)

---

### Post by ssc351 on 2007-11-03
Anyone else??? Have any ideas....I upgraded to 1.5.2 but still no worky.  This is going beyond my understanding of Ubuntu and Vbox...so I need some help....pretty please :)

---

### Post by bitumen on 2007-12-06
im using vista as guest in virual box 1.5.2 i mistakenly move (copy, pasted) the vdi to another location and upon rebooting could only use all the safe modes 

vista dvd startup repair , restore, ect ... did nothing to assist me in fixing the issue

the blue screen of death message  hinted at failed video driver initialization

so taken a gamble and unistall the guest additions drivers and rebooted 

yahooo its back => reinstalled the guest additions before i need to reactive again

hope this helps

**second reboot after guest addition install fails **

---

### Post by kalmi on 2008-03-23
I experienced the same problem when trying to use a port below 1024 as a HostPort without being root.
(I know that this is an old thread)

---

### Post by BwackNinja on 2008-05-03
I also know this thread is old, but I just wanted to point out that in the config ~/.VirtualBox/Machines/[your machine name]/[your machine name].xml, when you remove the extradata, with a name starting with "VBoxInternal/Devices/pcnet/" it works again.

---

