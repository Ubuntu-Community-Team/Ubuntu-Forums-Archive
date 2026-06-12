---
title: "Windows running in Ubuntu"
date: 2007-03-21
forum: General Help
---

### Post by spiggo89 on 2007-03-21
Hey, I read a post on digg about running windows within Ubuntu via some sort of virtual emulation, I was wondering if this is possible, and to have windows itself on a side of a xgl cube?
if you understand what im asking, thanks for your help :popcorn:

---

### Post by ZoiaGuyver on 2007-03-21
Hmmm thats something ive not tried tbh, but i have ran linux ontop of other linux installs with VMWare.

I should think a Virtual Machine (like VMWare or others) would be possible of making it happen. 

As for running it on the side of a Cube in Beryl i dont know about that i spose you should be able to as Beryl would just manage the VM window like any other.

---

### Post by hikaricore on 2007-03-21
[http://ubuntuforums.org/tags/index.php/vmx/](http://ubuntuforums.org/tags/index.php/vmx/)

It would be possible to run vmware on a side of the 
beryl or compiz cube, but you would need a decent computer
with a good amount of memory and a suitable video
card in order to avoid lagging yourself all to hell.  :)

*** note you'd have to disable vmware's ability to hold focus
on the mouse/keyboard in order to avoid weird issues. ***

---

### Post by Yoooder on 2007-03-21
It is perfectly possible, and not terribly hard to do.

If you have Ubuntu running with Beryl or Compiz, then all you need to do is pick a VirtualMachine product.  VMWare workstation is the commercial option, VirtualBox is a good free option, and qemu is a good grassroots option.

You just create the virtual machine, start it up fullscreen, and then just need to find a portion of your VirtualMachine software that overlays the Windows screen to click on and rotate your cube.  for example, VMware workstation has a small bar at the top of the screen (if you're familiar with Windows Remote Desktop, it's similar to the yellow bar at the top center).  I run my VM OS fullscreen, and to rotate over to another screen I just moust over that bar, middle click, and rotate away.

You should be able to find lots of tutorials on installing Beryl or Compiz, and VirtualBox has a .deb package. On a difficulty scale of 1 to 10 this should be about a 2...  pretty easy overall

I was doing this exact setup using a demo/beta of VMWare Workstation 6 (only because I already had a VMware 5.5 Virtual Machine) on Feisty, and it worked beautifully.  I actually used it for work (as a windows application developer) and the other guys only knew I was running Linux when I'd start twirling the cube (guaranteed to make them drool, even our Vista testers).

---

