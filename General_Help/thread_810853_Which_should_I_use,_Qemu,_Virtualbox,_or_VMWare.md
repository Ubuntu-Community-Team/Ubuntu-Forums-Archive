---
title: "Which should I use, Qemu, Virtualbox, or VMWare?"
date: 2008-05-28
forum: General Help
---

### Post by jlacroix on 2008-05-28
Hello everyone. I'm looking to install a small virtual Windows installation (probably Windows 2000) for a single purpose. I'm trying to figure out which virtualization technology I should use to accomplish this.

This is going to be done on my laptop. I use Game Maker for Windows, and that program is proably the only thing keeping Windows on one of my machines. (Ubuntu is used exclusively on all the others). I want to do some programming in Game Maker on a virtual Windows install in Ubuntu.

What I want is just a desktop icon I can click that will launch the virtual machine. I'd rather not have to start a GUI to launch my virtual machine first. (I think Virtualbox and VMWare make you use a GUI). From what I've read, Qemu seems the best for that. However, isn't Qemu rediculously slow?

So anyway in summary I need advice whereas which virtualization technology runs virtual machines the snappiest of the three and which ones can give me a simple command line access so I can make my own icon on my desktop.

---

### Post by bwhite82 on 2008-05-28
IMO, Virtualbox can't be beat. I believe it can be ran from the CLI as well.

---

### Post by jimbob on 2008-05-28
+1
Virtualbox is the best.  I particularly like the seamless transition between the V-Box window and the desktop.

---

### Post by sizzam on 2008-05-28
I'm very satisfied with VirtualBox.  The default shortcut for VirtualBox launches your main 'console' that lets you choose from all available virtual machines.   You can create a shortcut that launches directly into a specific virtual machine or launch a vm from the command line like this:

```
VBoxManage startvm "Name of VM"
```

---

### Post by bwhite82 on 2008-05-28
This shows you how to create a desktop shortcut to your vm as well as the command to start it from a terminal:

[http://blarts.wordpress.com/2007/12/03/how-to-launch-a-virtualbox-virtual-machine-from-a-shortcut/](http://blarts.wordpress.com/2007/12/03/how-to-launch-a-virtualbox-virtual-machine-from-a-shortcut/)

---

### Post by fwre01 on 2008-05-28
I would suggest virtualbox also from experience, i am very happy with VB at the moment, i have USB 2.0 and Gigabit NIC's working in my guests which is something i cudnt get working in VMware

---

### Post by jlacroix on 2008-05-28
Thank you guys, I'm going to give Virtualbox a shot.

Does Virtualbox offer any hardware acceleration? I know most VM softwares don't, but it's been a while so something may have changed since I last tried it.

---

### Post by fwre01 on 2008-05-28
Do you mean for using composite desktop effects? this is something i wud like to see, at present VB doesnt, but i think its on the roadmap and / or being tested at the moment

EDIT: One thing to note about VB, there is the Open Source Edition or the Non-Open Source Edition (but is free for personal use) i dont think the OSE has USB2.0 support (someone may correct me on that)

---

### Post by jlacroix on 2008-05-28
> **fwre01 said:**
> Do you mean for using composite desktop effects? this is something i wud like to see, at present VB doesnt, but i think its on the roadmap and / or being tested at the moment

EDIT: One thing to note about VB, there is the Open Source Edition or the Non-Open Source Edition (but is free for personal use) i dont think the OSE has USB2.0 support (someone may correct me on that)

I downloaded the main edition, but I'm confused, since when is it made by Sun? I downloaded version 1.6 from Sun so is that the right thing? (When you go to the Virtualbox website it takes you to Sun's site to download).

As far as hardware acceleration, I'm not looking for composite effects. I'm going to be using Vbox to develop 2D games in Windows, since there aren't many (if any) good game development products like Game Maker for Ubuntu. I just need a tad bit of hardware acceleration for old school 2D games. (Which is the kind I make).

---

### Post by fwre01 on 2008-05-28
yeah, Sun purchased VB off innotek and made it their own, it seems pretty good (except they broke host networking in their first release!) but its fixed now in 1.6.2

Im not sure about other hardware acceleration...?

---

### Post by jlacroix on 2008-05-28
I got Vbox installed, haven't had a chance to use it yet but whenever I go into the settings, I get the following error:

> Could not load the host usb proxy service (VERR_FILE_NOT_FOUND). The service might not be installed on the host computer.

I'm guessing that means USB support is off, but I haven't verified that yet.

---

### Post by fwre01 on 2008-05-28
> **jlacroix said:**
> I got Vbox installed, haven't had a chance to use it yet but whenever I go into the settings, I get the following error:



I'm guessing that means USB support is off, but I haven't verified that yet.

Yeah, you need to uncomment some lines in your /etc/init.d/mountdevsubfs.sh 

so it looks like this...

```
        #
        # Magic to make /proc/bus/usb work
        #
         mkdir -p /dev/bus/usb/.usbfs
         domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
         ln -s .usbfs/devices /dev/bus/usb/devices
         mount --rbind /dev/bus/usb /proc/bus/usb
}
```

Then just enable it from the settings of your guest OS

---

### Post by jlacroix on 2008-05-28
> **fwre01 said:**
> Yeah, you need to uncomment some lines in your /etc/init.d/mountdevsubfs.sh 

so it looks like this...

```
        #
        # Magic to make /proc/bus/usb work
        #
         mkdir -p /dev/bus/usb/.usbfs
         domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
         ln -s .usbfs/devices /dev/bus/usb/devices
         mount --rbind /dev/bus/usb /proc/bus/usb
}
```

Then just enable it from the settings of your guest OS

That fixed it, thank you.

Thanks to everyone for the swift and informative replies. I'm installing an OS on the virtual machine right now. With Virtualbox, it makes me wonder why VMWare even exists, this thing is full of features and seems to work great without a price tag.

---

### Post by jlacroix on 2008-05-28
It looks like Virtualbox and I won't be getting along afterall. I finished installing Windows 2000, and after installing the guest additions, the highest resolution I can get is 800x600. This is a 1280x800 laptop.

So other than Virtualbox, what else might I try?

---

### Post by bingoUV on 2008-05-28
> **jlacroix said:**
>  From what I've read, Qemu seems the best for that. However, isn't Qemu rediculously slow?



Qemu is not slow at all. In response to your other question, Qemu also supports hardware acceleration. Not of 3D graphics, but kernel mode acceleration.

It is difficult to get full resolution in Qemu, i.e. no UI for it , but it is possible.

---

### Post by jlacroix on 2008-05-28
Nevermind, I figured out the resolution problem, when I go full screen I get the normal resolution for my laptop.

My last problem with Virtualbox so far is I can't figure out how to access my Linux home directory from within the guest OS.

---

### Post by jrusso2 on 2008-05-28
You need to install the virtual box guest additions for the guest operating system.  I hope you got the non open source one.

---

### Post by jlacroix on 2008-05-29
> **jrusso2 said:**
> You need to install the virtual box guest additions for the guest operating system.  I hope you got the non open source one.

Yeah, I got the guest additions installed. Another problem I have is with Game Maker itself (the very purpose I did this) and it won't work, which I believe is a problem with Game Maker not Virtualbox or Ubuntu. I'm able to play a ton of games on my laptop so it makes no sense, Game Maker is only 2D unless you force it to be 3D.

---

