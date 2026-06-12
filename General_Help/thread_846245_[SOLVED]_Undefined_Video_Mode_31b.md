---
title: "[SOLVED] Undefined Video Mode 31b"
date: 2008-07-01
forum: General Help
---

### Post by Skillachi on 2008-07-01
So I have a HP DV6700t laptop, specs are

Intel T9300 2.5Ghz
3GB RAM
250GB HDD
Geforce 8400m GS

and all the other bells and whistles. When i start up the computer however, right after i select ubuntu in grub I get a message that says
"Undefined Video Mode 31b, please press enter to see available video modes or press space to continue". When i press space it loads into ubuntu with no problem though. Is it possible to get rid of this message?

---

### Post by Skillachi on 2008-07-01
anyone... anyone? Dont all shout at once now :D

---

### Post by Balinus on 2008-07-05
I have the same problem :(

It began after I did this : [http://ubuntuforums.org/showpost.php?p=5319721&postcount=13](http://ubuntuforums.org/showpost.php?p=5319721&postcount=13)

It's quite annoying...!

---

### Post by Balinus on 2008-07-05
I have found this solution and it works : [http://ubuntuforums.org/showthread.php?t=466181](http://ubuntuforums.org/showthread.php?t=466181)

---

### Post by Skillachi on 2008-07-07
doesnt work for me. apparently hwinfo isnt a recognized command

---

### Post by avtolle on 2008-07-07
As set out in the link which you were given, hwinfo needs to be installed; use Synaptic (search for it) and install from there, or from the terminal```
sudo aptitude update && sudo aptitude install hwinfo
```then to run it, use the command given in the link.

---

### Post by Skillachi on 2008-07-12
I installed the hwinfo and ran the tests and found the video mode that i think would work best but i dont know how to implement it (the thread doesnt describe that part)

---

### Post by plucky on 2008-07-13
> **Skillachi said:**
> I installed the hwinfo and ran the tests and found the video mode that i think would work best but i dont know how to implement it (the thread doesnt describe that part)

You need to add **vga=xxxxxx** value you want to the kernel line in the file menu.lst

To do so ```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.old
gksudo gedit /boot/grub/menu.lst
```
The first line makes a copy of the menu.lst file and the second line lets you edit the file.

Search for the entry that looks like this 
> title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=03aa7483-5b8f-4c1e-bd09-5db055ead5eb ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

and add vga=<some value> after **quiet splash**

Also search for > ## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

and add it here as well (after quiet splash) so that when you get updates to menu.lst,it will keep the same kernel parameters.

Good Luck

---

### Post by Skillachi on 2008-07-13
Much thanks plucky, problem solved

---

### Post by chk9 on 2009-12-29
never mind...

---

### Post by GTASouthPark on 2010-01-15
Wow, ok Plucky, you are a genius.  I'm running on Ubuntu 9.10, same undefined video mode.  Did everything you said.  My lists already said "VGA=795" but I switched the "795" with a 0x03something number that i found using the hwinfo.  It removed the problem.. soo happy :) :) :) Sorry if this is like bringing a 2 year old thread up.. but yeah. fixed a problem on Ubuntu 9.10 :)

---

### Post by invisible_ on 2011-04-23
Thank you very much plucky. The solutions really work but it is slowing down the boot a little so if there are any other ways to remove the unnecessary files, please post the solutions here.

If anyone want to know how people got to this error of "Undefined video mode" here is what happened to me. Also my error was Undefined video mode 31c.
 
I am running Ubuntu 10.04 LTS x32, Intel CPU, nVidia GT430. 

I used nVidia drivers from the websites and everything was smoothly running until I updated the Ubuntu. The I forgot how I installed the drivers from the official website (silly me) and I looked for better easier solutions (basic user..nothing advanced).

I found somewhere: do this to get GT430 drivers:
System>Administration>Software Sources
Software Sources tick 'Proprietary drivers for devices (restricted)'

Very bad advise... because nothing changed at all some files where installed but graphic card didn't allow Extra Visual effects.

Then I found how I installed drivers from [www.nvidia.com]("http://www.nvidia.com") and installed them then:
sudo /etc/init.d/gdm start
All working well all happy just until I restarted...

After the restart the error Undefined video... start coming up and I try searching it but no success and decided to uninstalled most of the installed Xorg files and servers (very bad idea..) 
Then I found a way to fix the deleted Xorg files but the error was still there. (OoOps I guess just I deleted all Xorg, Xserver files..silly me again )

Thanks to Plucky now the error is gone. 

Thank you very very much.
I hope this can help other too. :)

---

