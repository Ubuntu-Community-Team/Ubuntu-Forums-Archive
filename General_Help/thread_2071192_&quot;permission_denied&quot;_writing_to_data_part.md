---
title: "&quot;permission denied&quot; writing to data partition. fstab?"
date: 2012-10-14
forum: General Help
---

### Post by bennypr0fane on 2012-10-14
Hello, I have a problem with my fstab, I suspect.
I have a data partition mounted in fstab but it seems I cannot write downloads to it. Dropbox is on that partition and it does sync.
here's my fstab: [http://pastebin.com/vhPCmSsi](http://pastebin.com/vhPCmSsi)
and blkid: [http://pastebin.com/uF5t7Yey](http://pastebin.com/uF5t7Yey)
...the reason I suspect there is a problem in fstab is that I get a permission denied error for the downloads.
Also, I can't copy local files to that partition. but then how is Dropbox granted permission?
Thanks, Ben

---

### Post by marinara on 2012-10-14
[http://www.linuxquestions.org/questions/linux-general-1/write-permission-to-every-user-in-ext4-fstab-831446/](http://www.linuxquestions.org/questions/linux-general-1/write-permission-to-every-user-in-ext4-fstab-831446/)

most likely the directories on that mount dont allow you to save new files.  
i'm not an expert, but could you list the access rights and permissions of the directories you want to write to?

we need to see if your user is able to write to those directories.

---

### Post by Insomn1a on 2012-10-14
> **marinara said:**
> [http://www.linuxquestions.org/questions/linux-general-1/write-permission-to-every-user-in-ext4-fstab-831446/](http://www.linuxquestions.org/questions/linux-general-1/write-permission-to-every-user-in-ext4-fstab-831446/)

most likely the directories on that mount dont allow you to save new files.  
i'm not an expert, but could you list the access rights and permissions of the directories you want to write to?

we need to see if your user is able to write to those directories.

/\/\/\
You might have to CHOWN/CHMOD the folders like he is implying, also I would look at the documentation for this.

[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

---

### Post by bennypr0fane on 2012-10-15
I did this yesterday:

 ```
sudo chown -R USERNAME:USERNAME /media/mynewdrive
```

applied to my computer translates to:

```
sudo chown -R ben:ben /media/LinuxData
```

To check if it had taken effect, I checked the permissions under properties in Pcmanfm: it says owner of the directory is ben, owner has read and write permissions. After I ran this, yesterday it *still* did not work.
However, today it does :rolleyes:

Well, solved I guess! :lolflag:

---

