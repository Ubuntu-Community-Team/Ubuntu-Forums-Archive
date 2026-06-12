---
title: "vmware: creating vmachine very slow"
date: 2007-04-16
forum: General Help
---

### Post by rgiskard01 on 2007-04-16
I am creating a windows xp virtual machine and the process is dreadfully slow.  I have vmserver running, and have started the process of building the vm, but it seems to take much longer in ubuntu than it did when creating under xp.

Ubuntu 6.10
Athlon 64 X2 3800+ 
1gb DDR2  800
512 Mb assigned to the VM
I've tried allocating the space upfront and not.  With sizes ranging from 8Gb to 30Gb.  

No matter the configuration, it just takes so long that I have given up and tried different setups to try and speed the process.

For example, it takes in excess of 15 minutes to go through the setting up mouse and keyboard screen and setting up the networking  components screens.

Any ideas why this is taking so long?

---

### Post by rai4shu2 on 2007-04-16
Are you using an ISO image of the install disc?

---

### Post by rgiskard01 on 2007-04-16
I have the CD-ROM in the drive...not using an ISO image.

---

### Post by rai4shu2 on 2007-04-16
Using an actual disc makes it a lot slower. Try making an ISO copy to the hard drive and using that.

---

### Post by rgiskard01 on 2007-04-16
will give that a try...thx!

---

### Post by rgiskard01 on 2007-04-16
This still did not resolve it...

I left the machine to install, it has, but the vm hardly runs at all.  I mean, it is unusable.  I cannot move the mouse very well and it is just about locked up.  This isn't a vmware tools issue.

Nothing else on my machine, which is brand new, seems to be slow or act like this.  It is a fresh Ubuntu install, with all the updates.  

Asus M2NPV-VM motherboard
WD 200Gb Sata 3.0 HDD
G.Skill DDR2 800 1Gb
Antec 500 Earth Watt PSU

I  installed VMServer using the information from:
[http://ubuntuforums.org/showthread.php?t=183209&highlight=vmware+server+install](http://ubuntuforums.org/showthread.php?t=183209&highlight=vmware+server+install)
Which seems to be running fine, outside of this vm, and I have also used this ISO many times with no issues.

I disabled AMD Live! and HPET in the BIOS as well...

Any ideas what is going on?

---

### Post by rgiskard01 on 2007-04-16
Figured it out.

It was taking snapshots in the background.  I turned off both snapshots and SSL in the host settings, and it is running nice and fast.

Interesting that taking snapshots was the default config...

Is this normal?

---

### Post by vmwdnw on 2007-04-16
How did you get VMware to install in the first place?

---

### Post by rgiskard01 on 2007-04-17
I basically followed the instructions on the how to post: [http://ubuntuforums.org/showthread.php?t=183209&highlight=vmware+server+install](http://ubuntuforums.org/showthread.php?t=183209&highlight=vmware+server+install)

However, I did have to alter it just a little.  Here are the exact steps:

1.  using Synaptic, install xinetd
2.  download VMWare server
2.b.  register for free serial
3.  cp tar file to desired directory (I used /usr/local/vmware/) and extract
4.  cd to distrib and execute ./vmware-install.pl
5.  accept all defaults, except for location of vmware machines
6.  I used /usr/local/vmware/machines
7.  enter serial number when prompted

At this point, vmware server should be installed and working...however I still encountered a few problems starting the console and creating a virtual machine.  So I did the following additional steps (in the linked How to as well):

8.  execute the following command:  sudo cp /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1/
9.  execute the following command:  sudo cp /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0/

At this point, vmserver is working.

In creating new vm's, I normally pre-allocate space, and do NOT select split into 2gb files (which may not be the most correct manner - but I understand the 2gb file limit is primarily if you are going to be using the vm with FAT32 shares...).

Additionally, from yesterday I "learned" to:
1.  in the Edit VM / Options / Snapshot / select Disable Snapshots
2.  In Host Settings, Priority, deselect Take and Restore snapshots... AND, in Connection, deselect SSL.
For the 2nd one, I have to start vmwserver with the sudo vmware command from a terminal.

That is it!  Those steps should get it installed.
Good luck.

---

### Post by rgiskard01 on 2007-04-20
Update: apparently the slowness I was experiencing was not due to  the snapshots or SSL configuration.

I run BOINC: Seti, Rosetta, and World Community Grid.  Even though I had not started the boinc mgr, a world community grid process was running and not releasing cpu cycles.  Once I Stopped the process, the vm ran smooth again.

I can not figure out why the process, even with a Nice rating of 19, was acting this way, but configuring BOINC general preferences to not run while the computer is in use has resolved the issue.

---

