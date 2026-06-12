---
title: "NFS: where is most recent online documentation?"
date: 2015-02-07
forum: General Help
---

### Post by Old Jimma on 2015-02-07
Hi Community:

I wanto to use nfs to share folders between my ubuntu computers.

Can someone please point me to where I can find the most recent and easy to understand documentation?

I'm not a brainy Ubuntu guy, so a simple howto would be great! :)

Many thanks,
Old Jimma from the Old Country

---

### Post by ajgreeny on 2015-02-07
From Sept 2014 [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

---

### Post by Old Jimma on 2015-02-09
Hi Community:

When I followed the instructions at [https://help.ubuntu.com/community/SettingUpNFSHowTo]("https://help.ubuntu.com/community/SettingUpNFSHowTo"), on the client  when I issue the command

> 
# mount -t nfs -o proto=tcp,port=2049 192.168.1.67:/ /mnt


I get the message "access denied" even after rebooting the server. :?

Also, when I add the line
> 
192.168.1.67:/   /mnt   nfs    auto  0  0

to /etc/fstab nothing happens, even after rebooting the client.

](*,)

Any thoughts what may be wrong??

Thanks,
Old Jimma from the Old Country

---

### Post by Old Jimma on 2015-02-10
Well, Community!

I found out what was wrong!

In your /etc/exports make sure that your path names are spelled correctly!!

):P

Sincerely,
Oldest of the Old Jimmas from the Ancientest of Old Countries

---

