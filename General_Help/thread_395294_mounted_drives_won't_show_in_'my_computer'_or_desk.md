---
title: "mounted drives won't show in 'my computer' or desktop"
date: 2007-03-28
forum: General Help
---

### Post by chucklarge on 2007-03-28
Hello,
  I have 3 internal drives that I had mounted under /media  .  For no real reason, i decided to change the mount points to /mnt .   Now, the drives no longer show up under 'computer' nor do they show on the desktop.
here is what i have.  Keep in mind that this worked before i changed 'media' to 'mnt'

created 3 directories under /mnt
sudo mkdir /mnt/download
sudo mkdir /mnt/files
sudo mkdir /mnt/media

gksudo gedit /etc/fstab
..
/dev/hdb1 /mnt/download ext3 defaults 0 2
/dev/sda1 /mnt/files ext3 defaults 0 2
/dev/sdb1 /mnt/media ext3 defaults 0 2

sudo chown -R chuck /mnt/download
sudo chown -R chuck /mnt/files
sudo chown -R chuck /mnt/media

sudo mount -a

this did mount the drives on the desktop, didn't check 'computer' however, when i rebooted, the drives no longer were showing up. 

i CAN access the drives through their mount points, they are just not showing up in 'computer' or the desktop

any ideas?
chuck

---

### Post by chucklarge on 2007-03-28
Well, I moved the mount points back in /media and they show up on the desktop and in computer.
 
so is there a way to get ubuntu to show mounted drives not in /media to show up on the desktop?

---

