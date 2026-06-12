---
title: "Attaching Physical RAID Array to Virtualbox Guests"
date: 2018-05-27
forum: General Help
---

### Post by Robert_Boutin on 2018-05-27
Hi, could use some advice. I run a small business out of my house and I need to beef up my data storage and backup.

I have a physical machine i3, 16GB, 64 bit.  I have three 1TB HDDs installed.  One (sdb) runs Ubuntu 16.04 Desktop with Virtualbox.  I am running several Ubuntu 16.04 guests - an Apache web server, an email server (Perfect Server Setup), a cloud server running Nextcloud, a VPN server running OpenVPN, and a CRM server running SugarCRM.

Everything has been running off the single HDD which has worked fine but is incredibly risky - if my drive fails, I'm sunk.  I set up the other two drives with single partitions (sda1 and sdc1) as a RAID 1 array (md127).  Until I add NAS later this year, my idea is to use the RAID array to (1) hold the live data folders for the email, cloud, and CRM servers, and (2) store weekly VBox images of the guests (not snapshots).  Once the NAS is added, my plan is to use the RAID array just for the live folders and store backups of those and the guest images just on the NAS.

Is this a reasonable plan for a small home-based business to reduce the risk of data loss?

If so, I need to understand how to get the guest servers to attach to the physical RAID array, not for boot, just mounted for attached storage.  I've been googling trying to find a solution that fits my circumstance but I haven't found anything yet.  Any suggestions?  Thanks.

---

### Post by SeijiSensei on 2018-05-27
Install the Extension Pack and use "Shared Folders."  This method enables you to mount directories on the host machine into the filesystem of the virtual guest.  You can create entries in /etc/fstab to mount the shared directories at boot.

[https://www.virtualbox.org/manual/ch04.html#sharedfolders](https://www.virtualbox.org/manual/ch04.html#sharedfolders)

---

### Post by Robert_Boutin on 2018-05-27
Thanks Sensei.  I downloaded the Extension Pack and it is telling me I need to upgrade from VBox 5.1 to 5.2 which I will do.  But as I was working on this, it occurred to me to put each individual guest server on my RAID 1 array and just have VBox read and write there (instead of for example putting just the /var/vmail folder with my emails onto the RAID array).  That should give me an extra layer of safety while negating the need to attach my RAID array to my guest servers.  Sorry that only just came into my mind.

So I would have my single HDD running Ubuntu and VirtualBox (easy to replace and rebuild if HDD failed), all my guest servers on RAID 1 where they would be mirrored on an ongoing basis, and then in a few months I'll add a NAS where I could copy my Vbox folders, say weekly.

Does that seem like a reasonable way to protect my data?

---

### Post by SeijiSensei on 2018-05-27
I assumed you wanted transparent read/write access to the files on the array from inside the virtual machines.  There's no reason not to keep the VMs themselves on the array, of course.

Wouldn't you need to access /var/mail from mutilple VMs?  Any files like that would need to be in a separate directory that all the VMs can mount.

---

### Post by Robert_Boutin on 2018-05-28
I thought that's what I wanted, but then realized I'm better off putting the VM's in their entirety on the array.  I didn't actually need to access my /var/mail directory from multiple VMs, only from my mailserver.  So with everything on the array, and with soon adding a NAS elsewhere in the house (maybe in a fireproof box) for backing up the guest folders, I think I'll be in decent shape to recover from most events.

Thanks for tolerating my inexperience.

---

### Post by SeijiSensei on 2018-05-31
There's nothing keeping you from having your cake and eating it too.  You could install LVM on top of the RAID array and create two virtual "volumes" that can be mounted separately.  Then you could have a bigger volume with the VMs on it, and a smaller volume with files that you'd like to see from all the VMs.  I've used LVM on top of RAID1 in the past, but less so today because physical devices are so large.

General overview: [https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)

LVM on RAID1: [https://wiki.archlinux.org/index.php/Software_RAID_and_LVM#LVM_installation](https://wiki.archlinux.org/index.php/Software_RAID_and_LVM#LVM_installation)

You could, of course, repartition the devices holding the array and create two separate arrays instead of using LVM.  Using LVM is just quicker since you wouldn't need to recreate the arrays.  It's also more flexible if you think there's a chance you might want to resize these volumes some day.

I would hardly call you "inexperienced," and if I wasn't interested in helping I wouldn't be here!

I back up everything, including selected content on my remote servers in the cloud, to an inexpensive 4 TB external USB drive.  I've lived for nearly 70 years without a fire so that's not on my list of concerns.  I lost a couple of PostgreSQL databases powering websites some years back; won't let that happen again!

---

### Post by Robert_Boutin on 2018-06-23
Thanks Sensei for the guidance.  Because all my VMs were dynamically allocated virtual hard drives, I didn't realize how large they had grown over time, consuming nearly 900GB.  I added a 2TB RAID1 array, moved them all there, and converted all to fixed disk size.  At some point I'll need to research how to shrink them.  Everything seems to be working just fine so I'm relieved that by moving my VMs to the RAID array, I've added one layer of safety for my data.

Now I have three 1TB drives still in the machine.  One is the OS for the host (16.04 Desktop) with Virtualbox.  The other two are the 1TB RAID1 array I'm no longer using.  It's beyond the scope of my original question, but..  I think it could be a worthwhile activity to move the OS to RAID 1 for added safety.  My understanding is that for the OS, RAID would need to be managed by the BIOS or by a physical RAID controller.  Do you have any thoughts on the merits of either?

Thanks as always for your insight.

---

### Post by SeijiSensei on 2018-06-24
Personally I never run the OS on a RAID array. In the couple of cases over the decades when I had a drive failure, I've just reinstalled and copied over the backup.  If you want to give booting from RAID a try, take a look at [https://askubuntu.com/questions/660023/how-to-install-ubuntu-14-04-16-04-64-bit-with-a-dual-boot-raid-1-partition-on-an](https://askubuntu.com/questions/660023/how-to-install-ubuntu-14-04-16-04-64-bit-with-a-dual-boot-raid-1-partition-on-an)

Seems like way too much work to me.

---

### Post by Robert_Boutin on 2018-07-05
As always, you're right.  I went out to MicroCenter (love that store) and bought a 250GB Samsung M.2 PCIe SSD for my OS.  I installed it on the motherboard and loaded up Ubuntu.  It saw my RAID arrays immediately, I just needed to add them to mdadm.conf and fstab so the mounted on startup.  I installed Virtualbox, rebooted, and was then able to add my VMs on my RAID array.  Super easy, was clear there was really no benefit to running the OS on RAID.  And it freed up the 1TB HDD I was running the OS on to add a 3rd drive to my 1TB RAID 1 array.  Thanks again!

---

