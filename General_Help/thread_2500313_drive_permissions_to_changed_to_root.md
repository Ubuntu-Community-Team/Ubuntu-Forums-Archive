---
title: "drive permissions to changed to root"
date: 2024-08-29
forum: General Help
---

### Post by akirwin on 2024-08-29
I transferred my Ubuntu drive and secondary drives to a new machine, but now the drive permissions have defaulted to root, and I'm unable to change them back to my username.

I have two secondary drives that are combined into a single logical volume group using LVM2 (Logical Volume Management).

I have tried changing ownership 

sudo chown username /mnt/drive name/


sudo chown username:username /mnt/drive name/


sudo chown -R username:username /mnt/drive name/


sudo chown -R userid:userid /mnt/drive name/

---

### Post by TheFu on 2024-08-30
If there is a space in the "drive name" part, you need to quote that.
```
sudo chown username "/mnt/drive name/"

```
Best not to allow spaces in filenames or directory names - or always use tab-completion to have your shell do it for you.  If you are using LVM at this level, I would normally assume you know this, so if that isn't really what is happening, please post the actual output from the commands:
```

\ls -al  /mnt/driv*
\df -Th /mnt/driv*
```

So we can understand what is really happening.  And whenever posting terminal/CLI commands+output, please use **forum code tags** so columns are maintained and easier to read.

---

