---
title: "How To Uninstall"
date: 2008-05-20
forum: General Help
---

### Post by Amnesia180 on 2008-05-20
Hi All,

I have read tutorials saying I need the WinXP CD... I have an Acer system and I have inserted the CDs it told me to create when I first bought the system.

But this does not give me the option of "repair" it only gives me the option to format the system.

I want to totally un-install linux, and start afresh, choosing a different partition etc.

Any help would be great.

Thanks.

---

### Post by danwood76 on 2008-05-20
When you say uninstall how have you installed it?
If youve used WUBI I believe you can uninstall through Add/Remove programs.

Also if you are reinstalling GNU/Linux then you dont need to uninstall it first. (unless youve used WUBI)
You can merely reinstall it over the old one.

---

### Post by Amnesia180 on 2008-05-20
Hi,

I installed ubuntu via the CD from start up and followed the on screen instructions. 

I want to change the size of the partition I have it too... It has only left my C drive with 300 mb (taking 20 GB) when I only wanted to leave it with 10 GB. 

So I think a whole uninstall and then a fresh one is the best way forward, or if I run the installation CD again, will it ask me what size partition and I can just ammend it?

Thanks,
Amnesia

---

### Post by cdtech on 2008-05-20
If you just want to resize the partition, use gparted. That works really well for what you want to do.

No need to reinstall. I used it on my 250G hard drive with windows and it went well, a little time consuming but worth it.

---

### Post by Amnesia180 on 2008-05-20
Hi,

Thanks for the hint, all I want to do is resize the 22GB partition down to 10GB, then I can spend time ironing out the rest of the problems like my resolution issue etc. 

However, the problem I get is I can't even log into my ubuntu anymore so I want to do a fresh install of it.

---

### Post by Amnesia180 on 2008-05-20
Also, I forgot to mention that the partition does not show up in my windows. It only shows c drive and d drive... Not the third one for ubuntu.

---

### Post by danwood76 on 2008-05-20
If you do a fresh install it will give you the partitioning options how you had before. No need to uninstall first.
With this you can tell it to resize your linux partitions and possibly your windows partition aswell.

---

### Post by danwood76 on 2008-05-20
Yeah windows doesnt like linux filesystems ;)

---

### Post by Amnesia180 on 2008-05-20
Ok,

I am back at the installation screen where it gives me three options. 

Under the guided - resize partition 5 and use freed space, it only let's me select new partition size between two ubuntu disks. 

How would I then give my c drive back those 10 gigs I lost if I can't view them under windows? :(

---

### Post by Amnesia180 on 2008-05-20
Ok,

I have just reduced my ubuntu partition using the ubuntu manual option. 

I reduced it by 10GB. It now displays 9993mb of free space, so I click edit on my fat32 partition and try to add the 9993mb by increasing the file size, but it just keeps reverting back to the original size. 

Is there any way I can add the 10GB back to my first partition?

---

### Post by danwood76 on 2008-05-20
You can in windows, but only if you create the linux partitions at the end of the drive.
I hope that makes sense.

I think gparted allows resizing of fat partitions so it might be worth quitting the installer and doing the same through gparted instead.

---

### Post by Amnesia180 on 2008-05-20
Right,

I have reduced the ubuntu partition to 10GB and it leaves me with about 12GB in 'free space'. 

If I download g parted will this let me put my 12GB of 'free space' back onto the C drive?

Also, with the 10GB of ext3 that has one ubuntu install already on it. I have made sure there is a tick under 'format' so this should delete my previous install and add another one of the top right?

Lastly, I have chosen to import my documents for my windows profile, is this copying them all? Or just pointing ubuntu to their destination?

If I delete the files that are being imported, will they delete from my windows document folder?

Thanks!

---

### Post by danwood76 on 2008-05-20
Do the re partitioning with Gparted.

First I would just delete your current linux partitions, then extend the fat partition to leave you 10GB of free space for ubuntu to use.

Save the partitioning then start the installer, when required tell the installer to use the free space.

Ubuntu will just copy the files from your windows partition, it wont link to them as it uses a different file structure and file system to the windows ones.
You will still be able to access your windows files though, of course you wont be able to access your linux files from windows.

---

