---
title: "Copying the contents of one hard drive to another?"
date: 2007-10-24
forum: General Help
---

### Post by Opeth on 2007-10-24
I've got a laptop and a desktop. I want to transfer all of the data from my laptop to my desktop computer. How would I go about doing this? It would save me a lot of time because I wouldn't have to set everything up again. Even if it's just copying the entire /home directory... how would I do it?

My laptop is Ubuntu 6.10, and my desktop is Ubuntu 7.04. 


Thank you.

---

### Post by ofb on 2007-10-24
Just to be clear - you just want to move data (personal files) over? Or do you mean system and application configurations?

A simple data transfer is just drag'n'drop. Set up SMB or NFS. What have you got for connection?

SMB is just like Network Neighborhood in Windows. NFS mounts the remote folder locally, like your harddrive and cdrom are mounted. SMB is probably the way to go for this single use, but either is fine. Do a little search for the HowTo's.

Note: if you copy your /home/user_name folder to overwrite the /home/user_name folder on the target machine, then you'd be overwriting all the hidden files and directories that begin with a '.'. Those are your configuration files, and that would mess up the config of the target machine. You just want to drag over the files that aren't hidden.

Fire up nautilus, then Ctrl-H to show hidden files so you can see what I mean.

---

### Post by az on 2007-10-24
> **Opeth said:**
> I've got a laptop and a desktop. I want to transfer all of the data from my laptop to my desktop computer. How would I go about doing this? It would save me a lot of time because I wouldn't have to set everything up again. Even if it's just copying the entire /home directory... how would I do it?

My laptop is Ubuntu 6.10, and my desktop is Ubuntu 7.04. 


Thank you.

- Connect the laptop's hard disk to the desktop using an external enclosure.

- Boot the live cd.

- Copy the root partition to the destination partition on the desktop using dd.  

ex:

dd if=/dev/scd1 of=/dev/sda1


- Chroot into the partition on the desktop.

sudo mount /dev/sda1 /mnt

sudo chroot /mnt


- Reconfigre X for the new hardware

dpkg-reconfigure -phigh xserver-xorg


- and reinstall grub

grub-install /dev/sda


All this is assuming the target is sda1 and the source is scd1...!

---

### Post by Nunu on 2007-10-24
That sounds a bit iffy to me why not just reinstall the desktop?

---

