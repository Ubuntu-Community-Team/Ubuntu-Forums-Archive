---
title: "Remotely reboot into the windows loader being linux always the default grub option"
date: 2014-11-13
forum: General Help
---

### Post by vic_ser on 2014-11-13
Hi everyone.

I want to solve a problem of a next reboot selection. I use a Remote PC to perform bioinformatics tasks. Currently I've been using olny windows software (for remote connection and the bioinformatics tasks), but in the near future (when this question is solved) I will need to switch from ubuntu to windows and back to ubuntu regularly, allways trough Remote connection. 
What I want is to Remotely connect to the PC while it is on ubuntu, and through command line reboot into windows for only the next reboot. In other words: having ubuntu as the default grub option allways, but also having the ability to select the next reboot option (in this case the windows loader); and of course, when rebooting from windows, the ubuntu loader remains as the default grub option.

In understand that some will ask why not to be physically present to reboot the computer, well, because the remote pc is at an Institute two hours from here in a car trip (4 hrs round trip) for a simple grub selection. Perhaps others will try to solve this, simply by virtualizing windows within ubuntu, which isn't good enough since the bioinformatics tasks (at either win or ubuntu) are 48 to 60 hours long with a quadcore i7 8gb RAM at 85%; therefore virtualizing will double or triple the calculations time.

 I really would like to solve this, I dont know, maybe through a grub modification for a only once fashion each time I need the windows reboot. In the past I've screwed the grub a couple of times, with the undesirable effects this conveys, so I rather ask for your helpfull opinions. Thanx for reading. 

update1. Its is a BIOS system. Thanx oldfred for the observation.

---

### Post by Paulgirardin on 2014-11-13
There is probably an easier,more elegant way to do this,but one option would be to install Grub Customiser and change the grub menu order when you need to.

---

### Post by oldfred on 2014-11-13
Is it an UEFI system. That has a one time reboot as an option. And you can use efibootmgr to set that.

With BIOS it is not particularly easy. You just about have to install grub to a NTFS or FAT32 partition and write scripts for both Linux & Windows to edit boot option. Windows cannot edit grub boot option in the Linux partition.

---

### Post by vic_ser on 2014-11-13
I'm sure somewhere there is something like an argument for a transient modification for a grub-like program or version. Honestly, haven't found it. Thanx for your reply Paulgirardin, I'll keep searching.

---

### Post by vic_ser on 2014-11-13
Its a BIOS... the efibootmgr -n <number of win loader> would resulted nice and neat. Running a scrip at each reboot, may increase the probability of a catastrophe given my personal record (incompetence) with grub. Anyway I'll do it as a plan B scenario, thanx a lot oldfred for your excelent idea.

---

### Post by vic_ser on 2014-11-13
> **Paulgirardin said:**
> There is probably an easier,more elegant way to do this,but one option would be to install Grub Customiser and change the grub menu order when you need to.

I'm sure somewhere there is something like an argument for a transient modification for a grub-like program or version. Honestly, haven't found it. Thanx for your reply Paulgirardin, I'll keep searching.

---

### Post by vic_ser on 2014-11-13
> **oldfred said:**
> Is it an UEFI system. That has a one time reboot as an option. And you can use efibootmgr to set that.

With BIOS it is not particularly easy. You just about have to install grub to a NTFS or FAT32 partition and write scripts for both Linux & Windows to edit boot option. Windows cannot edit grub boot option in the Linux partition.

Its a BIOS... the efibootmgr -n <number of win loader> would resulted nice and neat. Running a scrip at each reboot, may increase the probability of a catastrophe given my personal record (incompetence) with grub. Anyway I'll do it as a plan B scenario, thanx a lot oldfred for your excelent idea.

---

