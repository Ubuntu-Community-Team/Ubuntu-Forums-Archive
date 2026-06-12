---
title: "Cant make directories or pastefiles even if mounted as readwrite"
date: 2018-01-07
forum: General Help
---

### Post by kuskusk265 on 2018-01-07
Hello, today I formatted my partition as ext4 and edited fstab to mount it as readwrite and everything seemed to work. But asi I tried to  copy some files into it it didnt work and I couldnt even make folders(that menas only one thing) so i opened terminal made directory on the HDD an it worked. folder is here. I cant make directories with Nautilus but with terminal I can. also when i open Lost + Found folder which got probably generated automatically the "Make Folder" button isnt suddenly greyed out but when I try to make the directory it says that its readonly. Does someone know what to do? I tried remounting it again as read write and nothing.

---

### Post by TheFu on 2018-01-07
When you mount new linux file systems in the "normal way", you need to change the ownership/permissions to whatever you need. By default, they are owned by root:root, so without very open/poor permissions, normal users can't write to that storage.  I suppose a GUI tool that does mounting might automatically make the user/owner the current userid.  I consider this to be a huge security risk for some good reasons.  The power to mount is the power to destroy, so I don't want non-root accounts to have that ability.

If you aren't good with Unix permissions, it is time to learn. There are tutorials all over the internet.  If you just want to know what to type, post the output from ```

$ ls -la
$ id

```

I don't have any idea why using a shell works when nautilus doesn't. Are these running under the same userid?

---

### Post by Impavidus on 2018-01-07
The lost+found directory (mind the exact spelling, Linux is case sensitive) is created automatically. It's used during file system repairs to put files of which the repair tool doesn't know where else to put them. As this "lost property" can belong to any user, it's best to make that directory accessible only to the root user (that is, the system admin).

---

### Post by kuskusk265 on 2018-01-07
I switched to Linux two months ago so i am definitely still a noob and eager to learn. 
Anyways the output is:

ls -la: *deleted*

id:

```
uid=1000(kuskus3) gid=1000(kuskus3) groups=1000(kuskus3),4(adm),20(dialout),24(cdrom),27(sudo),30(dip),46(plugdev),118(lpadmin),128(sambashare)

```

Oh, and when I type aaand understand it correctly then after writing ```
ll /media/
``` the /hdd (the /dev/sda1 partitoin mountpoint) is undeer root ownership, so I am supposed ot change this thing right?

---

### Post by kuskusk265 on 2018-01-07
Hmm, after changing owner using chown the ***_ll_*** command now shows that i am the owner (kuskus3) but even after rebooting the machine in Nautilus when i right click on mountpoint and click properties it says it still belongs to root, what am I doing wrong?

---

### Post by TheFu on 2018-01-08
Sorry I wasn't clear.  Never know what the other side of the conversation knows.

The **ls -la** is needed on the mount point for the disk.  You can see that using 'df' or 'mount' commands. It needs to be mounted to see anything useful.  It needs to use a real mount, not some GUI-gfvs mount thingy.

Please post both the command and the output using 'code tags' so things line up.

If you want a beginning level book/reference that is no-hassle and free, try:
[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)  - read the first 200 pgs for the background, then skim the rest (2 sec per page) to get a feel for what other things are included/possible.  Pay specific attention to the user/group and permissions stuff.  Linux is multi-user from top to bottom, always. Playing around with all the permissions in a shell for an hour with 3 userids, 3 groupids and temporary files is the best way that I know to get the "click" light bulb of understanding.

---

### Post by kuskusk265 on 2018-01-08
Haha, yes, I thought that I have to post the** ls - la** on the mountpoint on the disk. Nevertheless, I got it working by playing around with chmod (I set it to 754. even though I am and will be this PC only user.) Now I guess ill start to learn, thank you for the book recommendation :) If you still need the **ls -la** output here it is, but I think it is useless now 

```
 total 32
drwxr-xr--  5 kuskus3 kuskus3  4096 led  8 16:06 .
drwxr-x---+ 4 root    root     4096 led  8 15:56 ..
drwx------  2 root    root    16384 led  7 01:18 lost+found
drwxr-xr-x  2 kuskus3 kuskus3  4096 led  8 16:06 test
drwx------  4 kuskus3 kuskus3  4096 led  8 16:01 .Trash-1000



```

---

### Post by TheFu on 2018-01-08
Actually, you set the directory to 754 and the "test/" subdir to 755.  

It is really important that you learn Unix permissions ASAP.  If you don't, trivial things like this will drive you nuts for hours, days, weeks, months.  Having just 1 person using it means nothing.  Linux/Unix is multi-user, even if you aren't.  To learn, create 3 temp accounts, 3 groups, and mix and match membership in those groups among the 3 userids.  Spend 60 min playing with different directories, owners, groups, and settings for files and directories.  For as simple a system as the permissions are, there are huge capabilities.  If those aren't sufficient, there are always ACLs which can setup anything, exactly as you need.  In 25 yrs, I've used ACLs 3 times for some very odd, specific, needs.  So, you probably don't need to learn ACLs, just know they exist. Standard owner, group, other permissions should be sufficient.

BTW, you might want to make the directory permissions 750 and g+s.

---

