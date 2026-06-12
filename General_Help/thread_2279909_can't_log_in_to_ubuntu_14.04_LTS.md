---
title: "can't log in to ubuntu 14.04 LTS"
date: 2015-05-26
forum: General Help
---

### Post by john_patterson on 2015-05-26
I can not log in to my computer.  I have two user accounts and a guest account.  I can not log in to any of them.

This computer is about 3 weeks old.  I installed several pieces of software, and had to monkey around with some .so files in that process.  I created one alias in the .bashrc of one of my accounts.  I had left the computer up and running for at least 2 weeks.  The clock disappeared from the top tool bar.  I tried a bunch of stuf to get it back and figured I'd power down and power back up to see if the clock comes back.  Now I can not log in to any of my accounts - not even guest login.  The screen looks like it's the wrong resolution.  The text that lists the usernames is bigger than it used to be.  

I poked around on the web, and tried moving the .Xauthority for one of my accounts, but no luck.  (I can ctrl-alt-F1 to get to a shell...)

Anyone have more ideas to try?

---

### Post by ajgreeny on 2015-05-26
Tell us a lot more about your hardware and what exactly you have done to it.

What software did you install and how did you do that?
What were the various .so files that you had problems with and what did you do to try and get back the clock in the top panel?

---

### Post by john_patterson on 2015-05-26
I will try:

My machine was made by a company called Colfax International.  It has an 800GB SSD as the main drive.  There is also a 1TB HDD.  It has a Xeon CPU with 8 cores (16 threads).  The graphics card is a GTX 970, I think.  I'm using an ethernet connection for internet.  

I installed the educational version of Autodesk's Maya.  The educational version of Maya is not officially supported under linux by Autodesk.  So, I was using advice from forums to get it going.  I had to create a symbolic link from libssl3.so to libssl.0.9.8, since Maya wants libssl.0.9.8.  There were also some issues with libcrypto, but I don't remember what exactly I did.

In terms of the system tray clock, I was again working off advice from the internets.  I think I ran a command like this a few times:

[COLOR=#111111][FONT=Ubuntu]sudo apt-get install indicator-datetime

[/FONT][/COLOR]...and this:[COLOR=#111111][FONT=Ubuntu]

[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]sudo killall unity-panel-service

[/FONT][/COLOR]I've also installed SideEffects Software's Houdini, and Gimp.  Those both went very smoothly.

---

### Post by john_patterson on 2015-05-27
SOLVED:

I looked at this thread:

[https://bbs.archlinux.org/viewtopic.php?id=189898](https://bbs.archlinux.org/viewtopic.php?id=189898)

and had a look at my 

/var/log/Xorg.0.olg

I noticed that I was apparently trying to load nvidia drivers and nouveau drivers, which is apparently a problem.

so I tried to figure out how to remove the nouveau drivers and found this page:

[https://askubuntu.com/questions/481414/install-nvidia-driver-instead-nouveau](https://askubuntu.com/questions/481414/install-nvidia-driver-instead-nouveau)

...and this page:

[http://linuxers.org/howto/how-remove-nouveau-drivers-ubuntu](http://linuxers.org/howto/how-remove-nouveau-drivers-ubuntu)

I edited the 

/etc/modprobe.d/blacklist.conf


I rebooted, and still could not log in.  Then I got super lucky and found the nvidia driver that the people who made my machine had used.  I tried to run it, but I had to disable the display manager.  I do not have gdm, or kdm.  I have lightdm.  I got lucky figuring that out.

Then I was able to run the nvidia dreiver installer.  Then I was able to log in.

Am I going to have this problem everytime I get an update from ubuntu?  I don't think I can live like that.  I have no idea how/why the nouveau driver got installed.

---

### Post by efflandt on 2015-05-27
Which nvidia drivers are you running and was it an Ubuntu package (from normal repositories or a ppa) or was it a script you downloaded from nvidia.com? Not sure which driver is required for GTX 970, but my GTX 750 Ti was one of the earlier cards with that Maxwell chip and when I first installed 64-bit 14.04.1 it would not work with default nouveau driver or nvidia-current package (could not log in). But it worked with nvidia-331-updates. I am currently using a newer nvidia-349 package from xorg-edgers ppa (they now also have a nvidia-352 beta package). Ubuntu packages from the repositories (or a ppa) usually update properly using Software Updater. Driver scripts from nvidia.com used to have to be rerun after any kernel update, but not sure if that is more automatic now.

---

### Post by john_patterson on 2015-05-27
I installed this file:

NVIDIA-Linux-x86-64-346.59.run

It was sitting on my machine when it was shipped to me, so I have no idea where it came from.  Thanks for all that info - it's really beyond me, but I hope it can helps anyone who stumbles on this thread.

---

### Post by Bashing-om on 2015-05-27
john_patterson; Well, ......

Like this;
The Nvidia proprietary driver ( NVIDIA-Linux-x86-64-346.59.run) gets built against the currently installed kernel; when the kernel gets updated this proprietary driver gets broke. In this situation there is nothing to do but re-install the driver as it then gets built against the new kernel.
Bear in mind this is a PROPRIETARY code, and we in linux do not have access to it. What results is beyond our control.
If it is to be a problem for you, what you can do is install the latest release 15.04 ( not a LTS release) as that release does have support for the 346 version driver as that driver is in ubuntu's software repository.


[INDENT][INDENT]that be what little I know
[/INDENT][/INDENT]

---

### Post by john_patterson on 2015-05-27
Here are a couple of total beginner questions:

1)  How often will the kernel be updated, generally speaking?  Weekly?  Once a year?  If I have to re-install this driver every week I might want to deal with this situation.

2)  If I install ubuntu 15.04, will I have to re-install the programs I've installed on the machine like emacs, gimp, Maya and Houdini?

3)  What about the Nouveau driver?  Could I avoid this headache by using the nouveau driver?  It's open-source, right?  Maybe it's a little less needy?

---

### Post by Bashing-om on 2015-05-28
john_patterson; Welp;

Again, like this:
In responses:
1) There is no set schedule. the kernel is updated as the need and patches are made. In a point release the kernel will have the latest/greatest ( if Hardware Enablement (HWE) is employed will have the future release kernel installed) .

2) IF you do a clean fresh install of 15.04 then YES all your favorite aps will have to be (RE-)installed and configured ; IF you choose to upgrade from 14.04 to 15.04 ( must also do the in-between upgrade of 14.10) then these 3rd party PPA's (software) must be disabled, and maybe these aps will still be available in 15.04 IF the PPA maintainers have got their code up to speed. Before enabling these PPAs one would have to verify that the ap has support in 15.04.

3) Opensource driver has complete full support for most graphics sets. New hardware may lag in this support > The open source drivers may or may not have the performance that one might get from a proprietary driver. In some applications the opensource driver may even perform better. In between installing a driver from OEM, and open source are two additional alternatives; PPAs maintained by the ubuntu community, and installing the proprietary driver from the Software Center's "Additional Drivers" utility. ---- But, but but with the GTX 970 graphics card there may be no other alternative than the proprietary driver. ----
Installing from "Additional Drivers" vastly lessens the impact of an upgrade breaking the driver. That is what Dynamic Kernel Mode Setting (DKMS) is all about:
Some OEMs utilize this capability better than others
depending on the driver and source the driver available from the software Center should have complete support
open source driver does have complete full support. IF open source does well there will be no fret about breaking this driver in any update process.
-----------------------------------

Me, I run the LTS release (14.04) as my work horse and have other releases installed( when I break my work horse, I have another to goto ). I do run open sources driver on all of them and this driver performs very well in each.
Your mileage may well vary. It all depends on your hardware, how old AND how new. The GTX 970 card might fit into the "too new" category.
----------------------------

All that said,When we do our homework and find that the card is supported; will not take long to purge a present driver, install another and see what your results are.

[INDENT][INDENT]drivers:
[INDENT][INDENT][INDENT]that interface between the kernel and the hardware
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by john_patterson on 2015-05-29
OK, thanks for all the info.  At least I know how to solve this problem if it comes up again.  It was a bummer to be unable to log in and have no idea why.  

I still don't have a clock on my system tray.  Haha!  I'm going to pick my battles, though....

---

### Post by Bashing-om on 2015-05-29
john_patterson; Good deal;

When the graphics driver does not interface between the Xserver layer (kernel) and the hardware, nothing GUI works properly.
RE-install the driver.

as to:
> 
I still don't have a clock on my system tray. Haha! I'm going to pick my battles, though....

that is the subject of another thread. - threads are like dead men, one to the box -

Now if the present matter is concluded:
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

and it is ->
[INDENT][INDENT][INDENT]up up and away
[/INDENT][/INDENT][/INDENT]

---

