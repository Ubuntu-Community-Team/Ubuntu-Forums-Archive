---
title: "symlinking to a remote folder"
date: 2005-09-16
forum: General Help
---

### Post by Haegin on 2005-09-16
I want to be able to symlink the music on my sisters computer to my /usr/share/mpd/music directory so I can play it using mpd without having to use any more hdd space - is this possible?

Thanks

---

### Post by professor_chaos on 2005-09-16
I think the only way is mount the filesystem folder from your sisters PC to yours. 
If She is using Windoze, you will use samba.
something like "smbmount //her_computer_IP/Shared_folder /place_on_your_local_drive"
you can add this to your /etc/fstab file to make it do it automatically.

If She is using linux, then you will use NFS(network filesystem).

---

### Post by Haegin on 2005-09-17
She is on linux (ubuntu) but I think we are using samba anyway (she appears under smb://192.168.1.3). What line do I put in the fstab to automatically mount
```
smb://192.168.1.3/Jess'Share/moosic
``` to ```
/usr/share/mpd/music
``` ?

Thanks again

---

### Post by professor_chaos on 2005-09-18
something like....

```
//192.168.1.3/Jess'Share/moosic     /place_you_want_2_mount_on_local_drive     smbfs  auto,username=***,password=***  0  0
```

Putting the password unencrypted in fstab is not secure (but easy). You can find more secure ways of saving the password for samba, just do a google.

Oh, and lot's of times I try and mount other filesystems into either /mnt or into my home folder somewhere. Like /home/username/smb/etc...For organization purposes.

---

