---
title: "Where Is My Space Going? - Files Consuming 3x Their Size On Disk"
date: 2013-09-14
forum: General Help
---

### Post by Kirk Schnable on 2013-09-14
Earlier this week, I finally figured out how to use my new Linux file server as an iSCSI target for VMWare ESXi.  Now, however, I'm running into an issue with the file storage.


I created some VM file stores, using commands like:
```
dd if=/dev/zero of=/alpharaid/iscsi/esxiA51.iscsi bs=1M count=102400
dd if=/dev/zero of=/alpharaid/iscsi/esxiServers1.iscsi bs=1M count=409600
```
```
root@Nautilus:/alpharaid/iscsi# du -c *
104857612	esxiA51.iscsi
419430444	esxiServers1.iscsi
524288056	total
root@Nautilus:/alpharaid/iscsi# du -ch *
101G	esxiA51.iscsi
401G	esxiServers1.iscsi
501G	total
root@Nautilus:/alpharaid/iscsi# 
```


I created two large files on my RAID to use as fileio paths for iSCSI.  But when you look at how much space they're using, something doesn't add up...


```
Filesystem                Size  Used Avail Use% Mounted on
/dev/mapper/sdc1_crypt     20T  501G   18T   3% /alpharaid
```


So where is all my space going?  I thought maybe this was just some bad math from df, so I tried without the -h.


```
Filesystem                 1K-blocks      Used   Available Use% Mounted on
/dev/mapper/sdc1_crypt   20429878724 524288140 18880009068   3% /alpharaid
```


Nope... still doesn't add up.  20429878724KB-524288140KB=19905590584KB
So where's the other 1025581516KB (978.071GB) going?


I assume I've made a terrible mistake with block sizes or something, but I'm not sure what I need to do about it.  I'm willing, at this point, to wipe out the entire filesystem and start over, but without knowing what mistake I'm making, I'll just do it again.


Any ideas?  Please let me know if pasting output from a command will help you, I'll be happy to do so.


Thanks,
Kirk

---

### Post by mcduck on 2013-09-14
What filesystem are you using? If you take a close look, the *used* space actually matches with your files, it's only the *available* where you see a difference. And assuming you are using Ext4 (or some other version of the Ext filesystem), that's easily explained: 5% of space on Ext filesystems is by default reserved for root user only, and thus doesn't count as available for any other user.

0.05 * 20429878724KB =  1021493936.2KB, the rest would be explained by normal filesystem overhead.

The amount of reserved space can of course be changed, and of course on such a large volume the 5% would be overkill. The main reason for the reserved space is that it makes sure normal users can never fill the drive up to a point where the OS wouldn't be able to create the files it needs on boot. So for non-root partitions you might even want to disable the reserved space completely (although you probably wouldn't want actually fill your Ext filesystem over 95% anyway since it will start to suffer from file fragmentation when too full).

---

### Post by Kirk Schnable on 2013-09-14
> **mcduck said:**
> What filesystem are you using? If you take a close look, the *used* space actually matches with your files, it's only the *available* where you see a difference. And assuming you are using Ext4 (or some other version of the Ext filesystem), that's easily explained: 5% of space on Ext filesystems is by default reserved for root user only, and thus doesn't count as available for any other user.
You are correct that I'm using an Ext filesystem (ext4).

> **mcduck said:**
> 0.05 * 20429878724KB =  1021493936.2KB, the rest would be explained by normal filesystem overhead.
I was sort of wondering if some other factor (I suspected the ext journal, though) might be consuming this space.  Your explanation makes sense.  I assume you're talking about "reserved block count":
```
Inode count:              320495616
Block count:              5127907584
Reserved block count:     256395379
Free blocks:              4976397646
Free inodes:              320495587
```

> **mcduck said:**
> The amount of reserved space can of course be changed, and of course on such a large volume the 5% would be overkill. The main reason for the reserved space is that it makes sure normal users can never fill the drive up to a point where the OS wouldn't be able to create the files it needs on boot. So for non-root partitions you might even want to disable the reserved space completely (although you probably wouldn't want actually fill your Ext filesystem over 95% anyway since it will start to suffer from file fragmentation when too full).
I actually believed that during setup I set the reserved blocks to 0%, but perhaps I overlooked it for this FS.


Do you believe that's where the space is going, then?  I'd be OK with that... especially if I can turn off the reserved space later.

Thanks,
Kirk

---

### Post by mcduck on 2013-09-14
yeah, reserved blocks are the same thing. It can be defined as blocks, or using a percentage or bytes. But since you seem to have reserved blocks on the FS, it clearly isn't 0%.

You can use *tune2fs* command to change the reserved amount whenever you want. No need for formatting and the filesystem can be mounted when you do it so it's easy to change if you ever need to.

---

### Post by Kirk Schnable on 2013-09-14
> **mcduck said:**
> yeah, reserved blocks are the same thing. It can be defined as blocks, or using a percentage or bytes. But since you seem to have reserved blocks on the FS, it clearly isn't 0%.

You can use *tune2fs* command to change the reserved amount whenever you want. No need for formatting and the filesystem can be mounted when you do it so it's easy to change if you ever need to.

I will confirm that I was able to use tune2fs to reduce the reserved blocks on the filesystem, and that doing so did appear to resolve my missing space.   

Thanks for your insights, mcduck. 

[SIZE=4]**Thread solved.**[/SIZE]

---

