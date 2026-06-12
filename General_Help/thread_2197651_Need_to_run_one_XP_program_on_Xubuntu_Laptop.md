---
title: "Need to run one XP program on Xubuntu Laptop"
date: 2014-01-04
forum: General Help
---

### Post by glennc on 2014-01-04
Hello,
  I don't know if it is possible, but have an old HP laptop that was XP installed. I put Xubuntu on it and runs good. I have need of an astronomical program that only runs on MS that connects to a camera attached to a telescope. I was wondering if I could run my old XP copy in a virtual box in Xubuntu. I tried running it with wine and absolutely no luck. 
  I have never used any virtual machines so unfortunately I have no knowledge of it or how to. 
I appreciate any assistance if it is possible and how I might do it.

glennc

---

### Post by egeezer on 2014-01-04
Did you ever try searching Softpedia for the equivalent program htat will run under Ubuntu?

---

### Post by tomearp on 2014-01-04
You can use the free [VMware Player]("https://my.vmware.com/web/vmware/free#desktop_end_user_computing/vmware_player/6_0") software to run your old copy of XP, assuming you still have the install disc. 

I have not used it in Xubuntu but it should, at least in theory, be possible.

---

### Post by ian-weisser on 2014-01-04
Installing a VM is terribly easy. 
I use Xubuntu, and have an XP running in Virtualbox.
1) Check that your hardware is recognized by the Linux kernel before you go any farther. XP drivers won't work in a VM. 
2) Get Virtualbox or VMWare Player from the Software Center. Free.
3) Install your XP into Virtualbox. You need an XP install disk. There's an install wizard to help you.

---

### Post by glennc on 2014-01-04
Hello egeezer,
   From what I've researched there is no equivalent for my camera. I'll double check but the program that works is MS only shareware.
Thanks
glennc

---

### Post by glennc on 2014-01-04
> **ian-weisser said:**
> Installing a VM is terribly easy. 
I use Xubuntu, and have an XP running in Virtualbox.
1) Check that your hardware is recognized by the Linux kernel before you go any farther. XP drivers won't work in a VM. 
2) Get Virtualbox or VMWare Player from the Software Center. Free.
3) Install your XP into Virtualbox. You need an XP install disk. There's an install wizard to help you.

Hello ian-weisser,
   Thanks for your response. How do I check if the Kernel recognizes the hardware? Also which is easier, more forgiving.... VirtualBox or VMWare?
Appreciate the help! Doesn't sound exceptionally hard for my lack of expertise.
glennc

---

### Post by Bucky Ball on 2014-01-04
Software Centre>install Virtualbox>Launch Virtualbox>Create a virtual machine>Install XP into that virtual machine>Install whatever program you need to use. 

About that straightforward. There are a million Virtualbox how-tos on the interwebs.

---

### Post by glennc on 2014-01-04
Hello Bucky Ball,
   Thank you for your reply, you've been a great help in the past! Will give it a try tonight!
Finger's crossed!
glennc

---

### Post by Bucky Ball on 2014-01-04
Try these:

Ubuntu How-to:
[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

Download latest (but the version in the repos is fine):
[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

XP in Ubuntu (from step 2):
[http://www.wikihow.com/Install-Windows-XP-on-Ubuntu-with-VirtualBox](http://www.wikihow.com/Install-Windows-XP-on-Ubuntu-with-VirtualBox)

XP in Ubuntu (from step 3):
[http://ubuntuguide.net/installi-windows-xp-inside-ubuntu-using-virtualbox](http://ubuntuguide.net/installi-windows-xp-inside-ubuntu-using-virtualbox)

Other leads to follow:
[https://duckduckgo.com/?q=install+xp+virtualbox+ubuntu](https://duckduckgo.com/?q=install+xp+virtualbox+ubuntu)

Good luck. Pretty easy once you get the hang of it. Remember, when installing XP in VB it is the same as installing it the normal way; you will need to restart the XP virtual machine two or three times to complete the installation.

With VB installed you can also explore all those other Linux distros you only ever wondered about by running them Live, most don't need to be installed as VMs. You can simply mount the ISO as a virtual machine without even burning a disk! ;)

---

### Post by monkeybrain20122 on 2014-01-04
It depends on how much ram you have. VM is not feasible if you don't have at least 3G of ram.

Also if your VM us connected to a camera I think vbox from repo wouldn't work,--need usb integration,-- you need the version from Oracle and install guest addition
[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by glennc on 2014-01-04
Hello again, just had a lengthy update and got VirtualBox installed. Will give it heck in the morning! That other stuff sounds interesting. Hope this will work tomorrow
Thank you for the links Sir!
glennc

---

### Post by glennc on 2014-01-05
> **monkeybrain20122 said:**
> It depends on how much ram you have. VM is not feasible if you don't have at least 3G of ram.

Also if your VM us connected to a camera I think vbox from repo wouldn't work,--need usb integration,-- you need the version from Oracle and install guest addition
[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

Hello monkeybrain, well....... it doesn't have 3G and it certainly needs the USB port. So thanks for the extra avenue of exploration. Anyone notice laptops are very expensive lately?
Good evening
glennc

---

### Post by Bucky Ball on 2014-01-05
Yes, you'll need Guest Additions. Go here:

[https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)

And look for:

VirtualBox 4.3.6 Oracle VM VirtualBox Extension Pack  All supported platforms 

Click on 'All supported platforms' and save that somewhere. You will install the guest additions into the XP VM once it is running in Virtualbox. 

If you go to the heading 'Debian-based Linux Distributions' here:

[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

... and add the PPA for your release then that will keep Virtualbox updated (installing from a .deb won't).

---

### Post by C.S.Cameron on 2014-01-05
I prefer Vbox downloaded from: [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

The version from Ubuntu Download Center used to have issues with USB, not sure if it still does.

---

### Post by ian-weisser on 2014-01-05
> **C.S.Cameron said:**
> The version from Ubuntu Download Center used to have issues with USB, not sure if it still does.

Full USB support is in the VBox in the Ubuntu repositories (Software Center).
I migrated from the upstream version of VBox to the Ubuntu repository version, and I use USB on it regularly.
I no longer get those annoying "You should upgrade your VBox" popups anymore, too.

---

### Post by glennc on 2014-01-06
Hello Bucky Ball,
    Got tied up, but back at it again. I have VirtualBox 4.1.12_Ubuntu r77245 installed. Tried to follow the set-up but that differs slightly from my prompts. I think I got the basic setup Ok? In reference to the VM VirtualBox Extension Pack I followed the link, chose "All supported platforms" and it saved the file to the laptop.
  I am lost as to any of the following instructions, PPA, debian etc. Sorry!

glennc

> **Bucky Ball said:**
> Yes, you'll need Guest Additions. Go here:

[https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)

And look for:

VirtualBox 4.3.6 Oracle VM VirtualBox Extension Pack  All supported platforms 

Click on 'All supported platforms' and save that somewhere. You will install the guest additions into the XP VM once it is running in Virtualbox. 
If you go to the heading 'Debian-based Linux Distributions' here:

[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

... and add the PPA for your release then that will keep Virtualbox updated (installing from a .deb won't).

---

### Post by glennc on 2014-01-06
> **ian-weisser said:**
> Installing a VM is terribly easy. 
I use Xubuntu, and have an XP running in Virtualbox.
1) Check that your hardware is recognized by the Linux kernel before you go any farther. XP drivers won't work in a VM. 
2) Get Virtualbox or VMWare Player from the Software Center. Free.
3) Install your XP into Virtualbox. You need an XP install disk. There's an install wizard to help you.

Howdy again,
    Seems to have worked!?!!! XP installed In Virtual Box. Now I need to add the USB support. I have downloaded the file Bucky Ball suggested and can't figure how to get it attached, install or added on.
     You mention in a later post of having a running XP with USB support. Could you elaborate on that, please?
Thank you Sir
glennc

---

### Post by ian-weisser on 2014-01-06
There are lots of ways to do it. No additional software is needed (if the device is recognized by the Linux Kernel)

Here is one way:

Plug in your USB device before starting XP.
Start XP.

While the VM Guest (XP) is booting, look for the little icons along the bottom of the XP window.
Click on the little USB icon.
[IMG]https://lh5.googleusercontent.com/_-CRO_ltgYvZsnTx4lhUHF-j4Lv8AMBhpz7UOsUFby4=w143-h48-p-no[/IMG]

The icon will open a list of USB devices. If an item on the list has a checkmark, XP can use it.
If you want a device on the list to have a checkmark, simply select it.

---

### Post by glennc on 2014-01-06
Hello,
   It currently states that there are no usb devices. It did this before with a wireless mouse plug and it is doing it with the camera usb connection cable.
Help?
Thanks
glennc

---

### Post by Bucky Ball on 2014-01-06
Go here:

[http://www.dedoimedo.com/computers/virtualbox-guest-addons.html](http://www.dedoimedo.com/computers/virtualbox-guest-addons.html)

Look under the first heading down the page a bit:

'Install Guest Additions on Windows guest'

If you're asked to browse for a file, you want the Extensions Pack you downloaded previously. 

This should give you access to USB and a whole bunch of other extras.

---

### Post by glennc on 2014-01-06
Not quite sure what is wrong, but still can't get the USB working. I don't think I am understanding how to install the guest addons or something. That has to be installed in the guest account of the Xubuntu Virtualbox? I am confused. It keeps saying there is no USB devices. 
Will try some more tomorrow.
Thanks everyone for your help so far!
glennc

---

### Post by ian-weisser on 2014-01-07
Is the camera linux-compatible? It must be for VBox to use it for XP.
Does it show up properly in /var/log/dmesg when you plug it in? Or is it an "unrecognized device"?

---

### Post by glennc on 2014-01-07
> **ian-weisser said:**
> Is the camera linux-compatible? It must be for VBox to use it for XP.
Does it show up properly in /var/log/dmesg when you plug it in? Or is it an "unrecognized device"?

Hello and thanks,
   Nothing shows up, it states I have no USB devices. This is with the camera or with the wireless mouse usb plugin. I deleted the entries I've tried and will start over. It asks questions that I am guessing some answers to, before I even get to the guest addon part.
Thanks for any thoughts, guesses, advice!
glennc

---

