---
title: "[SOLVED] How to get into a terminal session on boot up in Hardy Heron"
date: 2008-05-31
forum: General Help
---

### Post by paquette on 2008-05-31
First, I am new to Ubuntu and Linux.  I have Hardy Heron on a multi-boot machine.  I tried to get version 8.4 of the ATI Radeon to work (on my x1900) following the second method described on [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide) but with no luck.  Last week ATI released version 8.5 so I thought I would try again, especially after discovering the information at [http://www.phoronix.com/forums/showthread.php?t=10050](http://www.phoronix.com/forums/showthread.php?t=10050) .

When I first looked at the information on the latter site the latest post (the one about using sudo modprobe) was not there.  Although I had to modify very slightly the

sudo dpkg -i --force-overwrite xorg-driver-fglrx_8.493*.deb fglrx-kernel-source_8.493-0*.deb fglrx-amdcccle_8.493-0*.deb

command on the Wiki page to take account of two deb filenames that have an additional number in their name, the method seemed to work well—everything extracted and compiled, the module installed and so forth with no errors.  When I rebooted, however, I wound up with the same problem described on the phoronix discussion, namely that boot up stopped on a white, or sometimes black, screen.  I rebooted again and unwisely chose the option to rebuild the X server from the recovery menu.

By this point in time the final post on the phoronix discussion had arrived and I thought it offered the final link in a very difficult installation chain.  I reasoned that if I could get into a terminal session I could probably find the xorg.conf?? configuration file that resulted from my installation activities and rename it to xorg.conf, then reboot and do the steps suggested in the last post to the phoronix discussion.

Somehow, and for the life of me I cannot remember now how I did it, I managed to get a terminal session from the console line available from the recovery menu.  Everything looked pretty much as I had suspected it would. I used gedit to examine each of the xorg.conf versions in <username>@machinename~ /etc/X11.  I then try to rename xorg.conf to something else and was going to rename the xorg.conf version timestamped at the end of my installation activities to xorg.conf.

Something went wrong with my use of the rename command, however, and the terminal session hung.  I rebooted intending to pick up where I left off but, even after several hours, I could not remember how I had managed to get into the terminal session.  I'm sure it's absurdly simple in comparison with the relative complexity of the problem of getting the ATI board to work.  I really don't want to reinstall Ubuntu from scratch and start all over, so please, how do I get back into a terminal session on boot up?

---

### Post by quelx on 2008-05-31
**CTRL-ALT-F1** perhaps?

---

### Post by pointone on 2008-05-31
The "Recovery Mode" option from the GRUB menu, perhaps?

---

### Post by paquette on 2008-05-31
Thanks to both of you for replying.

I tried CTRL-ALT-F1 although I'm sure that's not what I did when I managed to get into the terminal session.  I recall seeing some wording about the terminal session being a very basic terminal that should only be used when bootup failed or something like that.

That's the nub of my question--**how do I get into a terminal session from the recovery menu--or somewhere else during bootup**?  My recollection is that I entered some kind of a command on the console line available from the recovery menu but I was very busy yesterday and and could be wrong about that.

---

### Post by paquette on 2008-05-31
Mystery solved!

After I chose to rebuild X server from the recovery menu I did get through the login screen.  I then clicked on “Options” in the lower left-hand corner and selected the last option failsafe terminal.

I just did that again and used sudo mv to make the necessary name changes and now I'm back to where I was before—a black frozen screen.  In any case, this particular problem is resolved.

---

