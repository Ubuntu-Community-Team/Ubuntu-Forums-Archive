---
title: "Recover Files before clean reinstall"
date: 2022-03-03
forum: General Help
---

### Post by jmcmurdo91 on 2022-03-03
Hey,

I normally boot Ubuntu from an EFI file (brub) as the only OS on my machine. It's worked fine for over a year but now it won't boot the OS at all. This morning I was getting some error messages around AppArmor failing to load but now I don't get any terminal output, just a blank screen even when I switch between ctrl + alt + f1/f7

I have Ubuntu on a USB so I have no issue just doing a clean re-install but I really do need to recover some files beforehand. Is there anyway, when booting from a USB or doing a re-install, I can get my files back from the currently installed version of Ubuntu?

Thanks

---

### Post by yancek on 2022-03-03
This is why users should do regular backups so you have your personal data which you can restore.  

Yes you can do that.  Have another device which you wish to copy the data to available, boot the USB, mount the partition(s) on which you have the data on the installed Ubuntu and simply copy it to the other device.   You could get detailed explanations by searching for backups on Ubuntu or similar.

---

### Post by wyattwhiteeagle on 2022-03-09
> **jmcmurdo91 said:**
> Hey,

I normally boot Ubuntu from an EFI file (brub) as the only OS on my machine. It's worked fine for over a year but now it won't boot the OS at all. This morning I was getting some error messages around AppArmor failing to load but now I don't get any terminal output, just a blank screen even when I switch between ctrl + alt + f1/f7

I have Ubuntu on a USB so I have no issue just doing a clean re-install but I really do need to recover some files beforehand. Is there anyway, when booting from a USB or doing a re-install, I can get my files back from the currently installed version of Ubuntu?

Thanks

I've recently began experiencing something like this.
Except mine is a full minimal install to a laptop internal HDD

In my experience, you have two options...
(Both require a Live Session)

Method 1. Repair the partition's
Method 2. Transfer files you want to save

Method 1. Repair the partition's> 
1. Boot from a Live Session
2. Open Gparted
3. click on the partitiopn(s) of the drive that contains the files
4. Click on Partition at the top
5. Click on "Check"
6. Click on the green check mark at the top to apply the pending operations
7. Reboot the system (should reboot only normal enough)


Method 2. Transfer files you want to save> 
1. Boot from a Live Session
2. Open the partition where the files are located
3. Create a new folder somewhere on the partition such as the Desktop on the partition
4. Right-click on each file or folder you want to save
5. Click on "Copy to..." or "Move to..."
6. Navigate to and open the folder you just created
7. Click Select at the top right
8. After moving all items to that folder, "Copy to..." or "Move to..." a flashdrive, external, or "secondary" HDD or SSD

---

### Post by Quarkrad on 2022-03-10
Sound advice.  I would suggest you perform Method 2 first followed by Method 1 - always better to secure your personal files first before doing anything else.

---

### Post by ActionParsnip on 2022-03-10
I also suggest you review your backup regime. It is clearly ineffective

---

### Post by wyattwhiteeagle on 2022-03-10
> **ActionParsnip said:**
> I also suggest you review your backup regime. It is clearly ineffective

Ineffective only if the OP does any backups at all or doesn't know how to restore from a backup.

This may be the OP's way of "backing up".

Others view  this way of "backing up" as a "no real solution".

---

### Post by ActionParsnip on 2022-03-10
> **wyattwhiteeagle said:**
> Ineffective only if the OP does any backups at all or doesn't know how to restore from a backup.

This may be the OP's way of "backing up".

Others view  this way of "backing up" as a "no real solution".

A none existant backup is the least effective solution

---

### Post by wyattwhiteeagle on 2022-03-10
> **ActionParsnip said:**
> A none existant backup is the least effective solution



Very true

We can lead a horse to water but we can't make it drink.

Here again, the OP may choose to do no backups at all.
We know better than to do "non-existant backups".

Hopefully, the OP will learn soon.

---

### Post by ActionParsnip on 2022-03-10
> **wyattwhiteeagle said:**
> Very true

We can lead a horse to water but we can't make it drink.

Here again, the OP may choose to do no backups at all.
We know better than to do "non-existant backups".

Hopefully, the OP will learn soon.

People will insist on learning the hard way

---

### Post by mIk3_08 on 2022-03-10
> **jmcmurdo91 said:**
> Hey,
I normally boot Ubuntu from an EFI file (brub) as the only OS on my machine. It's worked fine for over a year but now it won't boot the OS at all. This morning I was getting some error messages around AppArmor failing to load but now I don't get any terminal output, just a blank screen even when I switch between ctrl + alt + f1/f7
I have Ubuntu on a USB so I have no issue just doing a clean re-install but I really do need to recover some files beforehand. Is there anyway, when booting from a USB or doing a re-install, I can get my files back from the currently installed version of Ubuntu?
Thanks
If you wanted to do a re-install I suggest that go for the installation where new Ubuntu install over the old Ubuntu installed. Or just try to create a new partition to the disk without touching the old Ubuntu installed in your disk. In this cased, i assumed you have other Ubuntu running pc. So good luck and cheers.

---

