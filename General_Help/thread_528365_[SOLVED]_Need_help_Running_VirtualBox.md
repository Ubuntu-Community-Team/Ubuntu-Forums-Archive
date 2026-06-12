---
title: "[SOLVED] Need help Running VirtualBox"
date: 2007-08-17
forum: General Help
---

### Post by kingleer on 2007-08-17
Okay, So I installed Virtualbox. However, when I try to install an Os on it, I get the following error - 


Error


The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 [error]

So, How do I go about fixing this error?

---

### Post by kingleer on 2007-08-17
Nevermind, I think I found the solution


In order to be able to use VirtualBox you must add yourself to the vboxusers group.
This can be done as follows:
Open System --> Administration --> Users and Groups
Click Manage Groups
Look up the vboxusers group in the list, select it and click Properties
In the users list find yourself and mark yourself.
Click OK, close any left open windows and reboot.

Nooby here.

---

### Post by UK-Wobbie on 2007-08-17
> **kingleer said:**
> Okay, So I installed Virtualbox. However, when I try to install an Os on it, I get the following error - 


Error


The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 [error]

So, How do I go about fixing this error?


Ok go to (System -> Administrantion-> Users and Groups) In there go to (Manage Groups)
And look for vboxusers.. Click on it and go to (properties) And click on root and your user name and then click on ok :) DONE

---

### Post by kingleer on 2007-08-17
Thanks, UK-Wobbie. I was able to install xp on Virtualbox. 

You wouldn't happen to know how to configure the network interface with Virtualbox?

When my Xp installation starts up, my wireless connection on Ubuntu dies, and Xp can't connect to the internet as well.

Ideally, I would like for both Ubuntu and Xp to be able to connect to the web at the same time.

---

### Post by UK-Wobbie on 2007-08-17
> **kingleer said:**
> Thanks, UK-Wobbie. I was able to install xp on Virtualbox. 

You wouldn't happen to know how to configure the network interface with Virtualbox?

When my Xp installation starts up, my wireless connection on Ubuntu dies, and Xp can't connect to the internet as well.

Ideally, I would like for both Ubuntu and Xp to be able to connect to the web at the same time.

The only thing i can say of is by looking in the Vbox Settings... You may see something to do with Network!

Good luck :)

---

### Post by bodhi.zazen on 2007-08-17
> **kingleer said:**
> Thanks, UK-Wobbie. I was able to install xp on Virtualbox. 

You wouldn't happen to know how to configure the network interface with Virtualbox?

When my Xp installation starts up, my wireless connection on Ubuntu dies, and Xp can't connect to the internet as well.

Ideally, I would like for both Ubuntu and Xp to be able to connect to the web at the same time.

Networking is somewhat involved, my advice is to read the [Virtualbox manual](http://www.virtualbox.org/download/UserManual.pdf) (sorry), but they do cover what you need to know to get your networking up, but it would be a fair amount of typing to enter it here ...

---

### Post by kingleer on 2007-08-17
Nevermind, I figured out the network problem. It was just a matter of picking the right adapter in 
the Settings. 

No problem. Everything works good.

---

### Post by kingleer on 2007-08-17
I have one last question. How does one share folders? I was able to add a folder on Ubuntu to be share with Virtualbox, but not on the Virtualbox Xp install. 

When I try to add C:\doc I get the following error - 


Shared folder path 'C:\doc' is not absolute.


Result Code: 
0x80070057
Component: 
SharedFolder
Interface: 
ISharedFolder {8b0c5f70-9139-4f97-a421-64d5e9c335d5}
Callee: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

---

### Post by kingleer on 2007-08-17
Nevermind, I found an explanation on how to share folders in Virtualbox here 

[http://www.blog.arun-prabha.com/2007/05/21/configuring-virtualbox-for-sharing-and-mouse-control/](http://www.blog.arun-prabha.com/2007/05/21/configuring-virtualbox-for-sharing-and-mouse-control/)

---

### Post by kingleer on 2007-08-17
Err nope still having a problem sharing folders.  I get stuck at 

net use M: \\vboxsvr\sharedfolder

Get the following error in Virtualbox Xp installation

System Error 53 has occurred.

The network path was not found.

---

