---
title: "local cluster???"
date: 2005-06-17
forum: General Help
---

### Post by kerinin on 2005-06-17
here's my problem: i have two computers, both fairly old - a laptop and a desktop.  i have ubuntu installed on both of them, and i use both as workstations.  i am constantly having to install things twice, fix things twice, tweak things twice, update things twice, etc etc etc.  i also have been running out of disk space for storage-slurping applications like dvd ripping.

my question is two part - first, is there a way that i can install ubuntu on ONE of my two machines (preferably the desktop) and then share that install with the laptop, perhaps via remote host, perhaps via remote desktop.  what are the options here?

secondly - is it practical to set up a shared filesystem (i know enough about this to throw out acronyms like NFS and RAID but not much else).  what about cluster filesystems like intermezzo or lustre?  the objective here would be to have a some directories split across the laptop and desktop hard drive allowing for large temporary storage operations and shared user files.

what would be really cool (and probably a pain in the arse to set up) would be to set up a cluster between the two computers which would allow desktop access from either computer, would create a shared virtual filesystem, and would allow task migration between the processors to speed them up if only one is being used.  is this possible?  i've done a little reading on openMOSIX but from what i can tell the drone nodes are practically unusable and task migration cannot happen from a drone to another drone or from drone to master.

thanks for any advice.

---

### Post by Alexander Kirillov on 2005-06-17
[QUOTE=kerinin]here's my problem: i have two computers, both fairly old - a laptop and a desktop.  i have ubuntu installed on both of them, and i use both as workstations.  i am constantly having to install things twice, fix things twice, tweak things twice, update things twice, etc etc etc.  i also have been running out of disk space for storage-slurping applications like dvd ripping.

my question is two part - first, is there a way that i can install ubuntu on ONE of my two machines (preferably the desktop) and then share that install with the laptop, perhaps via remote host, perhaps via remote desktop.  what are the options here?

secondly - is it practical to set up a shared filesystem (i know enough about this to throw out acronyms like NFS and RAID but not much else).  what about cluster filesystems like intermezzo or lustre?  the objective here would be to have a some directories split across the laptop and desktop hard drive allowing for large temporary storage operations and shared user files.

what would be really cool (and probably a pain in the arse to set up) would be to set up a cluster between the two computers which would allow desktop access from either computer, would create a shared virtual filesystem, and would allow task migration between the processors to speed them up if only one is being used.  is this possible?  i've done a little reading on openMOSIX but from what i can tell the drone nodes are practically unusable and task migration cannot happen from a drone to another drone or from drone to master.

thanks for any advice.[/QUOTE]
 Shared user files and documents/video/etc are definitely possible via NFS - this is probalby the easiest solution. But it is non-symmetric: one computer acts as NFS server, so it actually stores all the files; the other acesses these files. So if the server is down - you have no files. And it does not exactly allow to have a directory split across two machines.  

If you have a really fast network, you definitely can install all your apps only on one machine (say, the desktop) and run them from laptop remotely, using ssh with X forwarding (ssh -X). This does require that you have Ubuntu installed on the laptop - but it only needs to be a very basic installation, with ssh and X11. What will happen is that apps will run on  desktop processor, but will  show on laptop screen. Of course, this puts a signficant load on desktop CPU. 



Do not know enough about RAID and cluster soltuion - sorry.

---

### Post by kerinin on 2005-06-17
i've been playing with X forewarding, mostly for using my desktop speakers to play audio from my laptop.  i was having problems with netload when running a browser locally and other programs remotely, but maybe if i ran the entire window manager remotely it woudln't be such a problem (the desktop is connected directly to the router).

---

### Post by rick_1010 on 2006-10-14
Sshfs is another great solution for firesharing, I haven't used the alternatives but for sshfs you can actually mount a folder (or the entire hard disk) of another Linux machine so you can directly access and edit the files using a browser such as Nautilus.

---

