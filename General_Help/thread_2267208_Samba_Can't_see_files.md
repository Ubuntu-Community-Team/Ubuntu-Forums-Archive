---
title: "Samba: Can't see files"
date: 2015-02-28
forum: General Help
---

### Post by cackles on 2015-02-28
I say I've tried everything and if I haven't ... I must be pretty close ...

I have two samba drives /mnt/hgfs/store /mnt/hgfs/share

Every single file and directory in them is -rwxrwxrwx 1 root root.

I can see every single file and directory in store, but only half in share.

I have tried ...

sudo chmod -R a=rwx /mnt/hgfs/shared
sudo chmod -R a+rwx /mnt/hgfs/shared
sudo chmod -R 0777 /mnt/hgfs/shared

And all manner of other variations ... forward slash on, off etc. etc.

I've opened up my samba config to 0777 in create mask and directory.
My user privileges are working fine, I've had them up and down, full access and read only and I don't get it.
It just doesn't make any sense to me why half the files I transferred show up and the other half don't and yet every single newly created file shows fine in share.

Its past 8:30am, I've been up all night ... is the answer staring me in the face? And why-oh-why didn't I just get a drink last night since its the weekend?

Any help appreciated.

---

### Post by cackles on 2015-02-28
I think I've found a workaround (only took like 12hrs). If it works I will post it later since there are another 3 gazillion threads asking the same thing.

---

### Post by cackles on 2015-03-03
OK, so there was no workaround. It was a simple case of me being a dumbass. I hadn't formatted the drive to ext4, it was NTFS. That meant I couldn't change permissions -even though Ubuntu said it was doing it, which in turn meant any users I added to Samba were pretty much useless. The files that Samba could see were ones that I transferred onto the drive before I setup Ubuntu.

I am now in the process of transferring 6TB of files (for the 3rd time) so will update when/if it works.

---

