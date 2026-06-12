---
title: "Problem Updating"
date: 2007-01-16
forum: General Help
---

### Post by key134 on 2007-01-16
Hi all,
Ubuntu tells me that I have updates available to install.  I click on the orange icon and it says that:
> Not all updates can be installed.  Run a distribution upgrade, to install as many updates as possible.  This can be caused by and uncompleted upgrade, unofficial software packages or by running a development version.

I don't have an uncompleted upgrade and I am not running a development version.  Maybe it is unofficial software packages?  But what?  So I click the Distribution Upgrade button and it says Upgrading Ubuntu to version 6.10.  I thought I already had 6.10?  Then it fails on "Preparing the upgrade" with the error:

> A unresolvable problem occurred while calculating the upgrade.  Pleas report this bug against the update-manager package and include the files in /var/log/dist-upgrade/ in the bugreport.

I am not one to file bug reports before I know it is a bug.  The files in that directory are attached.  Can anyone help?

Keith

---

### Post by key134 on 2007-01-16
I did an aptitude upgrade which upgrade the few packages that I needed to.  But why are these two packages being held back?  This is the output from "sudo aptitude upgrade" now:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages have been automatically kept back:
  linux-restricted-modules-2.6.17-10-386 
The following packages have been kept back:
  nautilus-sendto 
0 packages upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

```

---

### Post by bkeithly on 2007-01-16
I HAVE BEEN HAVING THE SAME ISSUE!!!!

For me it looks like some nvidia packages I have installed are causing the problem.

I really do not want to remove the nvidia packages in order to get the updates (my screen looks like @ss with out the nvidia drivers)...

Anyway if you figure this out or if ANYONE else has a solution for this, PLEASE let us know.

oh ya,

Key what type of hardware, kernel and other packages are you using (i.e:  nvidia drivers, ndiswrapper etc..)

---

### Post by key134 on 2007-01-16
I have a GeForce 6200 using the nvidia drivers 1.0-9629 (not nv).  I am using the following kernel: 2.6.17-10-386.  I am not using ndiswrapper so I think the only reason I need the restricted kernel modules is because of my video card.  Without the nvidia drivers, TwinView doesn't work.  So... I may be stuck where I am right now.

I do think that I got most of the updates by doing an aptitude update & upgrade.  It seems to work better than the GUI update manager sometimes.  I just have those two updates being kept back.

Any ideas?

Keith

---

### Post by bkeithly on 2007-01-18
Try doing the update via the command  line.


I did this and it seems to have worked:


sudo apt-get update
sudo apt-get upgrade


Presto all is well!!!

Hope it works for you

---

