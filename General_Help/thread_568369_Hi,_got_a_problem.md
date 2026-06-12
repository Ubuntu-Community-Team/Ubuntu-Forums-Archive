---
title: "Hi, got a problem"
date: 2007-10-05
forum: General Help
---

### Post by ElementShacker on 2007-10-05
I just installing Ubuntu a few days ago. Today, since it was my day off I wante to try and get my Logictech mouse to scroll left and right with Ubuntu

I made a backup of the file,but I can't seem to access it.

The Ubuntu is installed  on a 320gig Western Digital Element External Drive:
[IMG]http://img.photobucket.com/albums/v179/Lt.Doomsday/Untitled-1.jpg[/IMG]


When I turn on the computer, it automatically loads Grub 1.5 and I pick the .16 generic Ubuntu.
When that is done loading, I get the Xserver error saying the mouse can't be found and it then says Xconf will be shutdown until GDE is fixed and then I don't even get a command prompt

With the Recovery mode I do get a prompt, but it's like this:
^oot doomsday-desktop#:

I try and type a command say:
sudo nanao/etc/X11/xorg.conf  
or
sudo mv/etc/X11/xorg.conf/etc/X11/xorg.conf

I just get command not found.

Is it possible to find a way to fix this so I can learn more about Ubuntu or I'm I hosed?

---

### Post by rsambuca on 2007-10-05
> **ElementShacker said:**
> 
With the Recovery mode I do get a prompt, but it's like this:
^oot doomsday-desktop#:

I try and type a command say:
sudo nano /etc/X11/xorg.conf  
or
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf


You just had some typos.  I have corrected them above.

---

### Post by ElementShacker on 2007-10-05
Thanks, finally got it working. I'm just having an issue now of not having permissions. :(

---

### Post by ElementShacker on 2007-10-22
I've been trying to get this scrolling issues fixed with the Logictech mouse and still haven't gotten it to work.

The mouse is a Logictech LX3 Optical Mouse.

---

