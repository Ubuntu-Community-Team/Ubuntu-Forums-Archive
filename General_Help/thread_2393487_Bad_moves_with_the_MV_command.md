---
title: "Bad moves with the MV command"
date: 2018-06-04
forum: General Help
---

### Post by kratos123123 on 2018-06-04
Hello, and thank everyone that takes some time to read this thread.

I am new to the terminal and I already made a huge mistake. Somehow I managed to move a random folder to the &#8220;root&#8221; of my computer. So instead of /var/bla/bla I would have /randomdirectory/var/bla/bla

After that everything except the browser stopped working and I understood I ****ed it up. 

The problem is that even though I have a pen drive with Ubuntu ready to install ( it&#8217;s not the first time I manage to break everything ) I cannot manage to start the installation . 

It says : 

Loading bootlogo...
bootlogo: invalid file format
Error setting up gfxboot

If I type help I get into 

Welcome to Ubuntu!
This is an installation system for Ubuntu 18.04. It was built on 20180426

And even though I can move through the pages with F1 F2 etc ...when I try to install it answers :

Loading install... failed : no such file or directory 

Any ideas ? Thanks a lot if you got to this point !!


*****
EDIT
*****

turns out that the USB Stick that I was using to reinstall Ubuntu didn't function correctly.
I made it bootable again and now I can reinstall.

Problem solved

---

### Post by Impavidus on 2018-06-04
Nice you solved it already. Reinstalling is a quick and easy way to solve problems, but actually fixing them may teach you more.

Moving directories from the root directory is indeed a way to break your system, although I think it would have been solvable without reinstalling or even using a live disk. This is because the /var directory that you moved isn't vital to the system. Most things no longer work when the system cannot find /var, but you should still have been able to run a root shell and some basic commands.

What you could have done is this: Use the grub menu to boot into recovery mode. Use the menu you get next to drop to a root shell. Mount the filesystem in read-write mode, then use the mv command to move your /var directory back and finally get out of your root shell.

Could you mark this thread as solved? Thread tools -> mark as solved.

---

