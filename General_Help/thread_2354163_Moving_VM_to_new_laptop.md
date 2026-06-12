---
title: "Moving VM to new laptop"
date: 2017-02-28
forum: General Help
---

### Post by robertzito on 2017-02-28
Because the external drive I am using to back up my files is partitioned as fat32 I can not export my VM guests to be imported to my new VM because the files are to large, I get the split error once I get over 4gb. In my home directory is a file VirtualBox VMs with all my VM guests. If I copy these folders to the same directory in my laptop will everything work as before or does anyone hae any suggestions on how I can export these large files to be imported in into the new laptop or just moving the files over in the same directory are fine? Also I will be going from Ubuntu 14.04LTS tp 16.04LTS if that makes a difference.

---

### Post by HermanAB on 2017-02-28
Format the external drive with a proper file system.  Anything from this century will work.

---

### Post by Impavidus on 2017-02-28
You can also split the files into smaller bits and merge them after transferring to the new computer. Try **split** and **cat**.

---

### Post by kingneutron on 2017-03-01
--1st, make sure *all* of your Virtualbox VMs are POWERED DOWN, not Suspended. Obtain your Virtualbox VM directory from File \ Preferences \ General \ Default Machine Folder and make sure you setup the Virtualbox on the new laptop the same way.

--2nd, if you have 2 laptops, you should be able to transfer the files directly over the network easily with netcat without using an intermediate backup drive.

(on NEW laptop)
# Make sure Virtualbox is NOT running 1st!
$ /sbin/ifconfig      # make note of your IP address - obviously you will need to have both laptops on the same network and turn off firewall temporarily or allow port 32100

$ cd vmdirectory     # obtained from virtualbox as described above - you may need to "mkdir" first
$ nc -l 32100 |tar xpvf -     # have netcat listen on port 32100 and output data stream to tar extract

(on OLD laptop)
# Make sure Virtualbox is NOT running 1st!
$ cd vmdirectory     # obtained from virtualbox as described above
$ tar cpvf - *  |nc -w 10 ipaddressofnewlaptop 32100    # substitute IP address of the "listening" laptop

--Once the files are done transferring, start Virtualbox and you should hopefully see everything. If not, you may have to Export all your VMs on the old laptop (Virtualbox File \ Export appliance ) and Import the .OVA files in Virtualbox on the new laptop. In that case, once you are done Exporting everything, you can use the above instructions but substitute the last line with this:

 $ tar cpvf - *.ova  |nc -w 10 ipaddressofnewlaptop 32100    # substitute IP address of the "listening" laptop

REF:
[http://superuser.com/questions/633431/whats-the-recommended-way-to-move-a-virtualbox-vm-to-another-computer](http://superuser.com/questions/633431/whats-the-recommended-way-to-move-a-virtualbox-vm-to-another-computer)

[http://ccm.net/faq/40899-virtualbox-how-to-transfer-a-virtual-machine-to-another-host-computer](http://ccm.net/faq/40899-virtualbox-how-to-transfer-a-virtual-machine-to-another-host-computer)

---

### Post by Habitual on 2017-03-01
> **robertzito said:**
> Because the external drive I am using to back up my files is partitioned as fat32 I can not export my VM guests to be imported to my new VM because the files are to large, I get the split error once I get over 4gb. In my home directory is a file VirtualBox VMs with all my VM guests. If I copy these folders to the same directory in my laptop will everything work as before or does anyone hae any suggestions on how I can export these large files to be imported in into the new laptop or just moving the files over in the same directory are fine? Also I will be going from Ubuntu 14.04LTS tp 16.04LTS if that makes a difference.
Alternatively, you could export to OVA file in Virtualbox and move file.ova to new host and import there.
Alternatively, you could
copy ~/.VirtualBox/ and ~/"Virtualbox VMs" directories to new host.

Rsync comes to mind also. [http://rsync.net/resources/howto/rsync.html](http://rsync.net/resources/howto/rsync.html)

---

### Post by dajavex71 on 2017-03-01
First, are both machines or will both machines be connected to the same network at the same time?
if not already, install openssh-server on both machines
> sudo apt-get install openssh-server

Determine the IP of both machines:
> ifconfig

The on the target machine:
mkdir mynewvmfolder ; replace with your preferred path - /home/user/mynewvmfolder

> scp -4r username@sourceipaddress:/home/user/currentvmfolder/* /home/user/mynewvmfolder

it will prompt for the connecting username's password from sourceipaddress

-4 - means to use ipv4 address only
r - recursive; if used without the -4, needs to be speciied as -r
sourceipaddress would be your OLD workstations IP Address

---

