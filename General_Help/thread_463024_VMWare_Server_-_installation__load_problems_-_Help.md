---
title: "VMWare Server - installation / load problems - Help!!"
date: 2007-06-03
forum: General Help
---

### Post by AD-RS1600i on 2007-06-03
Where to begin, I have been fighting with this problem all afternoon and now I am thoroughly frustrated with it!!

I think it is installed correctly using the 

sudo apt-get install vmware-server vmware-tools-kernel-modules

However this took me all afternoon to achieve with various other threads, because originally it would not install saying there was already a version installed that I first needed to purge from the system.  I think I managed to achieve this as in the end it did install correctly.... 

I also tried a 

sudo apt-get install --reinstall vmware-server vmware-tools-kernel-modules

Essentially, the icon for VMWare Server now appear in the menu but on clicking it the package appears on the bottom status bar briefly then disappears.....

My question is, how can I discover what is going on, is there a log file? or is there a way of getting it to check the contents that has been installed..

I did think my system might not be upto it, but it has 384mb of RAM so it should be ok?

I would really appreciate some help as it's annoying not being about to understand what's wrong with it.... 

Thanks in advanced.

Adrian

---

### Post by raja on 2007-06-03
384 MB RAM is on the lower end for running a virtual machine, I guess it wont be enough. Still that should only be a problem when you run a virtual machine, should not affect vmware-server itself. Start the server from the terminal, you will get a clearer idea of what is wrong since you will get an error message.
This might be a bit off the track, but VirtualBox, in my opinion, is easier to install and runs as well as vmware.

---

### Post by veloce on 2007-06-04
> **raja said:**
> 384 MB RAM is on the lower end for running a virtual machine, I guess it wont be enough. Still that should only be a problem when you run a virtual machine, should not affect vmware-server itself. Start the server from the terminal, you will get a clearer idea of what is wrong since you will get an error message.
This might be a bit off the track, but VirtualBox, in my opinion, is easier to install and runs as well as vmware.

Someone else is having these symptoms, but when the run vmware from a terminal it starts fine. Try that:  in a terminal enter "vmware" and see if you get anywhere.

---

### Post by AD-RS1600i on 2007-06-04
Thanks for your help, I really appreciate it!! :)

Right, the plot thickens :)

After attempting to load VMware at the terminal 

          adrian@adrian-desktop:/usr/bin$ vmware

I get the following error message,

         exec: 180: /lib/wrapper-gtk24.sh: not found

Which is great as it may explain my problem, but at the same time, i'm not sure how to go about fixing this? Surely this file would normally come from the installation package that 'apt-get' downloads and installs?

Any more ideas guys & gals ?:KS

Thank you 

Adrian

---

### Post by veloce on 2007-06-04
> **AD-RS1600i said:**
> Thanks for your help, I really appreciate it!! :)

Right, the plot thickens :)

After attempting to load VMware at the terminal 

          adrian@adrian-desktop:/usr/bin$ vmware

I get the following error message,

         exec: 180: /lib/wrapper-gtk24.sh: not found

Which is great as it may explain my problem, but at the same time, i'm not sure how to go about fixing this? Surely this file would normally come from the installation package that 'apt-get' downloads and installs?

Any more ideas guys & gals ?:KS

Thank you 

Adrian

Never come across that before!  Only thing I can suggest is that you google that error, see if someone else has had it and solved it.

---

