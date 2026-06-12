---
title: "Commands From Shortcut?"
date: 2007-01-30
forum: General Help
---

### Post by JFenske on 2007-01-30
Hello, I am new to Linux and I wanted to try out Ubuntu. I used linux once at a friends house and I think I got the hang of everything. 

I have a usb drive. It is a Sandisk Cruzer Micro and it never works right away when I put it in. I have to open a terminal and type this:"sudo modprobe -r ehci_hcd" then I have to type the root password. I was just wondering if there was a way to make a shortcut or program that I just open and it does that command and maybe even gives the password too, or just ask for the password like the update program does.

If there is a way to do this could somebody please show me or explain how to do this? Thanks.

---

### Post by kidders on 2007-01-30
Hi there and welcome,

You can't normally sudo a command non-interactively ... it would be a security risk. If you *really* wanted to though, you could modify /etc/sudoers to force your system to let you do it.

In any case, you shouldn't have to **rmmod** anything to make a device work for you. Rather than unloading the inappropriate driver manually all the time, you should be able to stop it being loaded in the first place by adding **blacklist ehci_hcd** to your /etc/modprobe.d/blacklist. With any luck, that'll solve your problem.

---

### Post by JFenske on 2007-01-30
> **kidders said:**
> Hi there and welcome,

You can't normally sudo a command non-interactively ... it would be a security risk. If you *really* wanted to though, you could modify /etc/sudoers to force your system to let you do it.

In any case, you shouldn't have to **rmmod** anything to make a device work for you. Rather than unloading the inappropriate driver manually all the time, you should be able to stop it being loaded in the first place by adding **blacklist ehci_hcd** to your /etc/modprobe.d/blacklist. With any luck, that'll solve your problem.

Thanks a lot that did it :D 

I have one more question. How do I install the newest drivers for my video card? It says to type this command:

"sudo sh /home/jonathan/Desktop/NVIDIA-Linux-x86-1.0-9746-pkg1.run" But when I do it says that X Server is running and I need to turn it off. What is X server and how do I shut it off?

---

### Post by kidders on 2007-01-30
Hey again,

X is the graphics server that sits under your Gnome/KDE/Xfce. It manages input devices, display adapters, etc. in your graphical environment. Just so your driver installer can keep unexpected oddities to a minimum, it naturally prefers if you kill X before it modifies its configuration files, and starts tinkering with drivers.

Something like **sudo /etc/init.d/**(?)**dm stop** should shut it down. It's probably best if you do it from outside your graphical environment.

There are two things worth noting though:

1. Most things that start **sudo sh...** are quite dangerous. Before you do it, be absolutely certain that the file you're executing is authentic, as you'll be giving it completely unrestricted access to your system.

2. Messing with graphics card drivers is not really a good idea unless you are pretty thoughrally familiar with X ... in particular xorg.conf (it's master configuration file). Whenever you do, there's a 50/50 chance your X server will break, so you need to be in a position to tweak (or reverse) anything the driver installer does.

If you feel like you wouldn't be able to handle operating in a text-only environment for a short spell while you sort things out, I strongly suggest getting help from a Linux-savvy friend before switching driver. I don't mean to be discouraging or over-dramatic, but I'd hate to see you get stuck, with no easy way around the problem. On the other hand, you see, your driver update may, in fact, work perfectly flawlessly!

---

### Post by Motoxrdude on 2007-01-30
True. just make a back-up of your xorg.conf file before you do anything.
```
sudo cp -p /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

---

### Post by JFenske on 2007-01-31
OK, thanks a lot for the tips I think that I will try this later today. I will just make a backup copy and just replace it if anything goes wrong. If I mess up to bad all I need to do is renistall and learn from my mistake.

Thanks for all of the help :D

---

