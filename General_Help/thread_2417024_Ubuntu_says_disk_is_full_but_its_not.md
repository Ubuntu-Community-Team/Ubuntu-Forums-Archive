---
title: "Ubuntu says disk is full but its not"
date: 2019-04-19
forum: General Help
---

### Post by mastershin19 on 2019-04-19
[COLOR=#242729][FONT=Arial]Very complex situation.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]My main server is in a 5TB raid.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I'm currently on holiday so I use Teamviewer and ssh to remote into my server.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]2 Days ago I ran a backup which was configured to be stored to my external hard drive. (10TB)[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Backup started successfully and I left it to backup.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]However later at night I had errors everywhere, here is what I noticed.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]External drives aren't mounted. No connection to network. (though I can ssh) Teamviewer stopped working. All critical applications stopped working. (virtualbox for example) Package Manager stopped working. ran df and all kinds of disk utilities in ssh to see what was taking up the drive.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]But the confusing part is that the drive isn't even full. Trash is empty. All partitions aren't even past 50% full.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Now back to when I ran that backup. I thought maybe I accidentally routed the backup to store on the main drive. But there is no signs of the backup at all.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I've scanned and rebooted multiple times however it shows that the disk isn't full. But linux still says its full.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I have attached some images to give a better understanding. 
[SIZE=3]
[IMG]https://i.stack.imgur.com/4dm1R.png[/IMG]


[IMG]https://i.stack.imgur.com/cch7f.png[/IMG][/SIZE][/FONT][/COLOR]
[COLOR=#242729][FONT=Arial][SIZE=3][/SIZE]Not referring to the images above but I have tried df without -i which says /dev/sdb1 (mounted on /) is 100% in use, however all the folders in / all total up to around 2-3TB. (and the drive is 5TB) Edit: I'm using su so I don't think there is any hidden folders which it can't read.[SIZE=3]

[/SIZE]I was wondering if the /dev/loopx partitions in the image could be the issue but I'm not sure what to do with those.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Any ideas anyone?[SIZE=3]
[/SIZE][/FONT][/COLOR]

---

### Post by CatKiller on 2019-04-20
If your external hard drive got unmounted, you might have run the backup to the mount point. Remounting the external drive would then cover up those files. You may find that unmounting the external drive will reveal them.

The /dev/loops are snaps.

---

