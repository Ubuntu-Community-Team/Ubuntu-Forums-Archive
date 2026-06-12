---
title: "Migrating data from SSD to HDD?"
date: 2013-04-02
forum: General Help
---

### Post by Calinou on 2013-04-02
Hi, I currently have a 2TB HDD and a 256GB SSD (Samsung 840 Pro to be exact).

I installed Xubuntu 12.10 (64 bit) on the SSD, then I tried to copy my whole /home directory to it. Once I rebooted, I couldn't login, every time I pressed "enter" after inputting my password, it went back to the login menu.

Note that on the HDD, I have a 30GB / partition and a ~2000GB /home partition, on the SSD I only have a ~250GB / partition.

So, how can I migrate all my stuff without breaking everything like I did?

---

### Post by btindie on 2013-04-02
So do you want to move EVERYTHING from the SSD to the HD or just /home ?

Your best option is to boot a live CD, mount both home directories and use rsync to copy from one to the other.
```
sudo mkdir /mnt/{old-home,new-home}
sudo mount /dev/sda5 /mnt/old-home
sudo mount /dev/sdb5 /mnt/new-home
rsync -avh --progress --stats /mnt/old-home/ /mnt/new-home/
sync
sudo umount /mnt/old-home
sudo umount /mnt/new-home

```
Change sda5/sdb5 to your correct partition.

Once done you'll also need to update /etc/fstab so it uses the correct partition UUID value
```
sudo blkid -s UUID -o value /dev/sdb5
```
Replace sdb5 with the partition of your new home partition.

---

### Post by oldfred on 2013-04-02
So did you try to copy your 2TB /home into your 256GB SSD?

I only have a 64GB SSD, but I put two 27GB / (root) partitions on it, one current 12.04 and the other 12.10. Each has /home included, but all data is still in data partitions on my hard drives. My goal always is that every drive has an operating system and that system is fully configured to boot from just that drive. Data may then be on any drive. That way when one drive fails, I can still boot another, even if some data is not mounted from a failed drive.

---

### Post by Slim Odds on 2013-04-02
I have a 128G SSD with a separate / and /home

But I removed the folders for Pictures, Music, Download, Videos and replaced with symbolic links to the HDD for those BIG folders.

---

### Post by Calinou on 2013-04-03
So I've copied my /home and /, but the /home landed in a directory named "old-home" in the SSD's /home partition. And of course, the SSD refuses to boot.

---

### Post by oldfred on 2013-04-03
The SSD still should boot. It just will create a new /home if you have not added the correct entry for you /home into fstab. Did you change your /home entry in fstab with your new UUID?

When you copied did you preserve ownership & permissions?

---

