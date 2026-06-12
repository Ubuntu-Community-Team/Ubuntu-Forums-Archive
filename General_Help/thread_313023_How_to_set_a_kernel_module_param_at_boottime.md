---
title: "How to set a kernel module param at boottime?"
date: 2006-12-05
forum: General Help
---

### Post by alanfranz on 2006-12-05
Hello... I've just a small question...

how can I force to load a certain module with a certain param?

I have a kernel module for the MS Natural 4000 keyboard which only acts the way I want it to if i use a certain param, e.g. I usually do:

insmod usbnek4k ascii_keycode=1

Since the code is under development, it'll probably take some time to find out a 'final' solution which will not need that kind of 'hack'... besides hardcoding the value to 1 in the usbnek4k.c file, is there another way around it? If I add it to /etc/modules I don't seem to be able to pass a param as well.

---

### Post by mgmiller on 2006-12-05
I think you need to edit /boot/grub/menu.lst

Make a backup of it first, in case something goes awry, so you can easily get back to where you were.

There is an "automagic" part near the top where you can add in kernel modules.  Don't uncomment anything here.  Double hashmarks (##) are not processed, but single hashmarks (#) are.  
You would just add your module to the appropriate line, save the file and then run ```
sudo update-grub
``` to make it add the lines to all the kernels listed below.  This will also automatically append the change to any new kernel you update to.  I'm just not sure if you would add your entry to the last line of the 
"## default kernel options" area 
or to the last line of the 
"## additional options to use with the default boot option, but not with the
## alternatives" area.  
Again, you are not creating a new line here, just appending your info onto the end of the last line.

---

### Post by dmartinsca on 2006-12-05
Hang on, no need to mess with grub, that's for passing parameters to the kernel! Kernel modules can be passed options when they are loaded. Create a file in /etc/modprobe.d/ called usbnek4k and in it put **options usbnek4k ascii_keycode=1**

That should do it, every time the usbnek4k module is loaded it should be passed that option. You can add usbnek4k to /etc/modules to have it load on boot if it isn't already doing so.

BTW, run **man modprobe.d** for more info.

---

### Post by alanfranz on 2006-12-08
Thanks to both of you! I'll test both solutions soon.

---

