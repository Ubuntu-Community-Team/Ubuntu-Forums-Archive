---
title: "Bootsplash Howto"
date: 2005-04-08
forum: General Help
---

### Post by chronusdark on 2005-04-08
ok i dont want to start a flame war about linux eyecandy vs usability all i want to know is if someone got bootsplash to work with ubuntu hoary using 2.6.10 686 kernel.....i know i have to recompile the kernel and i am comfortable with that im just unfamiliar with the process to install bootsplash and set it up
Please help me.

thanks in advance :D

---

### Post by erkki70 on 2005-04-09
Hi,
Have a look to this thread:
[http://ubuntuforums.org/showthread.php?t=24858](http://ubuntuforums.org/showthread.php?t=24858)
Useful infos can also be found searching the forums for example like this:
[http://ubuntuforums.org/search.php?searchid=488223](http://ubuntuforums.org/search.php?searchid=488223)

Hope this helps.

Cheers,
Erkki

---

### Post by chronusdark on 2005-04-09
your first link shows a thread i have already read and it just talks about how usplash works and such
i already have usplash working but i dont like it as much as bootsplash
your second link says no matches found.
i have already looked all over this forum and i cant find out just how to get bootsplash working 
im very familiar with how to use the search

i downloaded the bootsplash patch i think im supposed to use
 and when i applied it, it listed all the stuff its supposed to when patching the kernel

sudo make menuconfig in /usr/src/linux i see bootsplash under device drivers -->graphics
but when i make the kernel it gives me errors relating to the bootsplash i could tell you what they were but i did it late last night and i cant remember

my kernel version is 2.6.10-5-686
and i got the bootsplash for 2.6.10

---

### Post by erkki70 on 2005-04-10
Ok, sorry you couldn't find anything interesting.
I had bootsplash working in my previous Debian Sid distro also on a 2.6.10 Kernel, but I have to say it wasn't very stable and sometimes would appear only when quitting or restarting. It needs quite much tweaking to get it properly working IMHO.

Would be good if you can post the error when you build your kernel. ;)

Have you enabled the following options when you do the make menuconfig?
 ```

 [size=2]Code maturity level options  --->       
     
[*] Prompt for development and/or incomplete code/drivers       
 Processor type and features  --->       
     
[*] MTRR (Memory Type Range Register) support       
 Device Drivers  --->       
     Block devices  --->       
         <*> Loopback device support       
         <*> RAM disk support       
         (4096) Default RAM disk size       
         
[*]   Initial RAM disk (initrd) support       
 Graphics support  --->       
     
[*] Support for frame buffer devices       
     
[*]   VESA VGA graphics support       
     Console display driver support  --->       
         
[*]   Video mode selection support       
         <*> Framebuffer Console support       
     Bootsplash configuration  --->       
         
[*] Bootup splash screen
[/size]
``` 
         Original is here and even though it's a different distro, you'll find very well documented how-to: [http://forums.gentoo.org/viewtopic.php?t=49036]("http://forums.gentoo.org/viewtopic.php?t=49036")
Another good resources: [http://bulma.net/body.phtml?nIdNoticia=1812](http://bulma.net/body.phtml?nIdNoticia=1812) instructions for 2.4 kernel but useful anyway.
I used this as well as the infos from bootsplash.org and bootslpash.de plus googling to get Debian specific infos.

Good luck and hope this helps.

Cheers,
Erkki

---

