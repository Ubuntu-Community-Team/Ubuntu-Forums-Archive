---
title: "Grub Update After New UUID Change"
date: 2014-04-15
forum: General Help
---

### Post by Redalien0304 on 2014-04-15
Made a Copy (using Gparted) of my Ubuntu 13.10 Partition, gave my Old Partition (ubuntu 13.10) a New UUID. Reinstalled Grub on New Copy of Ubuntu 13.10 using "sudo grub-install /dev/sda". Boots Just fine. Is there an Easy way change my UUID for my Older Ubuntu 13.10? Do i change them in boot/grub/grub.cfg & etc fstab? can i use Grub Customizer? or is there a diffrent way? Any Help is Appreciated. Thanks

---

### Post by Redalien0304 on 2014-04-15
Bump Anyone? can Boot-repair deal wit UUiD changes? came across this Link [http://askubuntu.com/questions/171446/how-to-fix-the-uuid-in-grub-after-restore-from-another-machine](http://askubuntu.com/questions/171446/how-to-fix-the-uuid-in-grub-after-restore-from-another-machine)

---

### Post by monkeybrain20122 on 2014-04-15
boot from a live usb, run
```
sudo blkid 
```
this will show the new uuid of your partition
edit /etc/fstab and /boot/grub/grub.cfg for that partition so that the uuid match the output from blikd. For boot/grub/grub.cfg it is easiest to do it with gedit and the 'replace all' function. Make sure you edit the correct files because the live usb has files with the same names and you want to edit the files for the installed version of Ubuntu, which will be in /media... when you view them from the live usb.

That's it, there is no need to reinstall grub, you can run 
```
sudo update-grub
```
when you reboot into the Ubuntu installed on the partition whose uuid has changed. But that may not be necessary

---

### Post by DogMatix on 2014-04-15
If you want to be able to boot your old 13.10 from the GRUB installed on your new 13.10 can you not just run 

```
sudo update-grub
```

from your new install.

If you want to actually customise the UUID maybe this will help [How do I change UUID of a disk to whatever I want?](http://askubuntu.com/questions/132079/how-do-i-change-uuid-of-a-disk-to-whatever-i-want?answertab=votes#tab-top)

---

### Post by monkeybrain20122 on 2014-04-15
> **DogMatix said:**
> If you want to be able to boot your old 13.10 from the GRUB installed on your new 13.10 can you not just run 

```
sudo update-grub
```

from your new install.

If you want to actually customise the UUID maybe this will help [How do I change UUID of a disk to whatever I want?]("http://askubuntu.com/questions/132079/how-do-i-change-uuid-of-a-disk-to-whatever-i-want?answertab=votes#tab-top")

Well no, if you change the uuid of the partition without making the changes in fstab and grub.cfg it wouldn't boot.

---

### Post by oldfred on 2014-04-15
Generally you are not supposed to edit grub.cfg.
But your case is an exception. 
I would only modify the first entry as when you boot into your system run sudo update-grub it will totally overwrite grub.cfg and will then have all the correct entries thoughout.

 Change example sda6 to your Ubuntu partition
sudo mount /dev/sda6 /mnt
gksudo gedit /mnt/boot/grub/grub.cfg 

      
 #May have to do this first as it is write protected also:
sudo chmod +w /mnt/boot/grub/grub.cfg
#Or even this first:
sudo chmod 777 /mnt/boot/grub/grub.cfg

---

### Post by DogMatix on 2014-04-15
> **monkeybrain20122 said:**
> Well no, if you change the uuid of the partition without making the changes in fstab and grub.cfg it wouldn't boot.

You don't have to have a disk's UUID in fstab to boot to it.

---

### Post by Redalien0304 on 2014-04-15
What about Grub Customizer? Can i just Remove the Old Grub Ubuntu 13.10 Enties from Grub Customizer, & Restart & run sudo update-grub?

---

### Post by DogMatix on 2014-04-15
Running *sudo update-grub* will give you a fresh *grub.cfg* file which should list both your old & new 13.10 installs.

Is this what you are trying to achieve?

---

### Post by Redalien0304 on 2014-04-15
yep i have ran sudo update-grub twiced. both grub entries boot me Ubuntu 13.10 which is Bigger in Size. My other Ubuntu 13.10 Old is smaller in Size.
Have not made any changes except give Ubuntu 13.10 Old a New UUID.Also made Ubuntu 13.10 New Bigger & Made it the Default Os by Running "sudo grub-install /dev/sda"

---

### Post by DogMatix on 2014-04-15
So you have two GRUB entries for 13.10?

---

### Post by Redalien0304 on 2014-04-15
yep i have 2 Grub Entries for 13.10 yes. both boot me into my Newer 13.10

---

### Post by monkeybrain20122 on 2014-04-15
Do what I told you to.

---

### Post by monkeybrain20122 on 2014-04-15
> **DogMatix said:**
> You don't have to have a disk's UUID in fstab to boot to it.

Maybe not in OP's setup. But I only give instructions for what I have done so I know for sure that it would work. In my setup I definitely have to change fstab because I have a separate /home and I changed the uuid for both / and /home. Without editing fstab it won't boot because it could not find the /home partition.

---

### Post by DogMatix on 2014-04-15
> **monkeybrain20122 said:**
> Maybe not in OP's setup. But I only give instructions for what I have done so I know for sure that it would work. In my setup I definitely have to change fstab because I have a separate /home and I changed the uuid for both / and /home. Without editing fstab it won't boot because it could not find the /home partition.

Ah! O.K. point taken.

---

### Post by Redalien0304 on 2014-04-15
The new UUID appears in grub.cfg mor than 22 times? Will Grub Customizer work if i f remove the old 13.10 Entry? Save & Restart & run "sudo update-grub" create new entry?

---

### Post by QIII on 2014-04-15
Have you tried

```
sudo apt-get autoremove
```

to see if some of those 22 are older kernels?

---

### Post by Redalien0304 on 2014-04-15
it is a new install like yesterday. just ran nothing to remove.

---

### Post by QIII on 2014-04-15
Hmmm...

Fresh install or upgrade?

In your grub.cfg, are all those entries associated with the same kernel version?

---

### Post by Redalien0304 on 2014-04-15
should be cause it is copy of the original partition. which was a fresh install

---

### Post by Redalien0304 on 2014-04-16
Ok ran Grub Customizer Removed Old (extra) Ubuntu 13.10 Entries, Saved. Restarted. Ran sudo update-grub, no second entry for Ubuntu 13.10 on sda3. My (im on it now) copied Ubuntu 13.10 is on sda1. Grub is installed on Sda.

---

### Post by Redalien0304 on 2014-04-17
Ok solved this problem by Starting all over of Fresh Re-Install Ubuntu 13.10 & 14.04. Reformatted disk & fresh grub install.

---

