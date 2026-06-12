---
title: "Creating RAID 1 over existing LVM on running system disk"
date: 2014-08-24
forum: General Help
---

### Post by Blowfish0815 on 2014-08-24
Hi all,
I'm running Ubuntu 14.04 LTS and currently have a 250GB system disk with 3 partitions. 
```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000bbc34

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758   488396799   243947521    5  Extended
/dev/sda5          501760   488396799   243947520   8e  Linux LVM

```

Now i want to move this disk completely to a 2 TB disk (empty) and build a RAID 1 with a second 2TB disk.

I tried with copying the whole disk with dd to the new disk, formed 3 RAIDs for the 3 partitions and wanted to add the /dev/sda partitions to the running RAIDs, which doesn't work because the devices are busy.
Can this work anyway? May i add the /dev/sda partitions to the array with a livesystem, so that the partitions are not mounted? Or is this a complete wrong way?

---

### Post by Blowfish0815 on 2014-08-25
Nobody any ideas? I'm still quite desperate with it.

---

### Post by nerdtron on 2014-08-25
You want the OS to be in the 250GB and then create a RAID1 for the 2x2TB disk?
Or you want to create a new RAID1 of 2x2TB disk that will that will copy all data of the current 250GB and then remove the 250GB disk?

My suggestion:
1. Disconnect the 250GB drive.
2. Connect the 2x2TB drives, configure RAID1, setup partitions, install the OS.
3. Boot into this new OS in RAID1 just to confirm you successfully installed the OS and RAID is running corectly.
4. Shutdown, connect the 250 GB drive, but don't boot into this drive.
5. Boot into the new OS with RAID1.
6. Mount the 250GB drive LVM partition to be able to copy the data. Since this is an LVM partition, normal mounting procedures won't apply. You'll also need the LVM packages to be able to mount/read it.
7. Once the LVM partition is mounted, Copy all its data to the new RAID1 patitions.
8. Shutdown and disconnect 250 GB drive. 
9. Boot again on the RAID1 drives and see all your data.

---

### Post by Blowfish0815 on 2014-08-25
I want to replace the old 250GB disk with existing data and move them to a RAID 1 consisting of 2x2TB disks.

---

### Post by nerdtron on 2014-08-25
See my updated post above.

---

### Post by Blowfish0815 on 2014-08-25
My concern is that the machine is a server host for two virtualbox maschines, which shouldn't have too much downtime.

Would all the programs and config run without any problems or would be a clean install easyier?

Just for information: if there would be no LVM would I be able to create the RAID during the running system?

---

### Post by nerdtron on 2014-08-25
It has two Virtual machines? That would even be easier. Just reinstall the new Ubuntu with RAID 1 and then install virtual box, then import the VMs disk, run them again.
Or you can shutdown VMs, copy them to another server and run them in there. On your current server, install Ubuntu with RAID1.
Shutdown the VMs on the other machine and copy them back to the new installed server. Run them again in here.

Basically, the VMs have virtual hard drive that are saved on the host machine with a single image which can be transferred and run on other servers.

PS: You are running production virtual machines on virtual box and you are using Ubuntu Desktop edition? This is a combination that is only suited for testing purposes. You should be using Ubuntu server edition and KVM for virtual machines on production environments.

---

### Post by nerdtron on 2014-08-25
> if there would be no LVM would I be able to create the RAID during the running system?
I always question people why they need LVM? We'll I think you can setup RAID1 on the 2x2TB drives while the system is running. But it would result on just a single disk with no data, how would you install the OS? You won't remove the 250Gb drive?

---

### Post by Blowfish0815 on 2014-08-25
With your postings in think now that a clean new install of a ubuntu server edition would be the better choice. I did the install of ubuntu desktop because i thought i would ne a GUI from the begin, which was false but i never changed the system and just updated from LTS to LTS. The system runs now at least for 5 years.

I thought a LVM would be better, because it's the only possibility to increase the partitionsize lateron without deleting the partition and setting it up new?
I wan't to get rid of the 250GB drive. Finally in the server there should be 2x2Tb and 2x3TB each in a RAID 1.

Concerning your question/suggestion about KVM. Until now i only knew of VMWare, which I didn't want to use when installing the servers. 
What are the big advantages of KVM over VirtualBox and can the machines be converted or would I also have to reinstall them completely?

---

### Post by nerdtron on 2014-08-25
Hhmmm.... In my opinion, if you don't plan to increase your storage in the long run, you don't have to LVM, especially if you have RAID configured, it would be difficult, if not impossible to add another hard drive without reinitializing the RAID.

For your setup. Just plain RAID would be enough on the HOST Ubuntu Server since it will not do anything except holding the images of the Virtual machines. LVM do makes sense to use on the VMs because if a VM has a shortage on hard drive space, you can just create a virtual hard drive and add it to the LVM of the Virtual Machine.


KVM is short for **Kernel-based Virtual Machine** and makes use of hardware virtualization. It is the virtualization standard built onto the linux Kernel. Basically, think of it as the Virtual Box for servers. 

Setting up KVM on Ubuntu has two parts, the KVM-server itself which will run the virtual machine (this alone can be used to run virtual machines without GUI, can be controlled on the command line) and the other part is a GUI (the GUI can be installed on any Ubuntu desktop - this one is really good if you want to control a remote KVM server). The GUI part is strictly not KVM but rather a Virtual Machine Manager (virt-manager for short). 
Here is a good link to get you started: [http://www.howtogeek.com/117635/how-to-install-kvm-and-create-virtual-machines-on-ubuntu/](http://www.howtogeek.com/117635/how-to-install-kvm-and-create-virtual-machines-on-ubuntu/)
Do not install virt-manager on the server since this will require a GUI. Install virt-manager on your desktop so that you will control the KVM server remotely.


 Next, what is the format of your Virtual Box images? I'm guessing they are .vdi files. If so, you can convert them to .raw to .qcow2 so that KVM can read them and run the virtual machines. Here's the link for conversion [http://www.randomhacks.co.uk/how-to-convert-virtualbox-vdi-to-kvm-qcow2/](http://www.randomhacks.co.uk/how-to-convert-virtualbox-vdi-to-kvm-qcow2/)
Step 3 on that link is optional since KVM can read .img files as well as .qcow2 files.
After you converted the .vdi images to .raw, you can import them on the Virt-Manager GUI of Ubuntu.

---

### Post by mira2 on 2014-08-25
<a href="http://www.real-wishes.com" title="real wishes granted" name="real wishes granted"><img src="http://www.real-wishes.com/images/wish-3.jpg" alt="real wishes granted" title="real wishes granted" /><br>real wishes granted</a>

---

