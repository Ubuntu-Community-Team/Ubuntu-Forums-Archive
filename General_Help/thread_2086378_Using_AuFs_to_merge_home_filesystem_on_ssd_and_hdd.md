---
title: "Using AuFs to merge home filesystem on ssd and hdd"
date: 2012-11-20
forum: General Help
---

### Post by spirytusick on 2012-11-20
I have recently bought a ssd of 240GB. It hosts my root ubuntu fs + a separate partition for /home filesystem (both on ext4). My previous setup had 1TB /home filesystem on a hdd. I wanted to have the benefits of speed of an ssd and cheap storage of a hdd.

My idea was to do the following:

most . directories + .files will be on ssd + few selected media directories (those less data heavy)

Most of the media containing directories are on the hdd (such us Music, Videos, Documents, etc...) + ~/.local/share/wineprefixes

The relevant part of my fstab is:

```
UUID=2071f6ee-ee0d-4ec6-bc65-798788daaa9a	/union/sissd	ext4		discard,noatime,nodiratime			0	2
UUID=19175b78-7cba-45dc-a3a0-4450bf5065d2 	/union/sihdd    ext4    	discard,noatime,nodiratime			0       3
none						/home/skosecki	aufs		dirs=/union/sihdd=rw:/union/sissd=rw		0	0
```

Now, it works pretty much flawlessly but there are a couple of annoying issues with this solution. 

First, Dropbox keeps on triggering its first run wizard every time I log in, complaining that it has not been installed in the correct way and it has to be manually logged on and configured again(settings are preserved though). 

Secondly, as I have mentioned earlier, .local directory exists both on ssd and hdd. All of its sub-folders except share/wineprefixes exist on ssd. 
Upon first mount during boot process, /home.skosecki/.local/share/wineprefixes folder is not showing under aufs filesystem. After a manual umount /home/skosecki followed by mount /home/skosecki everything is back to normal and wineprefixes folder appear as expected.

Now what I would like to achieve is a fully "coherent" mount straight from fstab, without having to resort to umount/mount combo afterwards and of course fix dropbox although I can probably live with this for a while. 

I have read aufs documentation but I am afraid is a tad difficult to understand as the underlining filesystem concepts are not explained in great detail.

Perhaps someone in Ubuntu comunity has tried similar setup and overcome the problems? 

Thanks in advance,

---

