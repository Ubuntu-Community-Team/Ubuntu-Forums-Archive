---
title: "Permanetly Mounting NFS from FreeNAS"
date: 2015-04-19
forum: General Help
---

### Post by danny7 on 2015-04-19
I've tried both this 
[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

and this
[https://help.ubuntu.com/14.04/serverguide/network-file-system.html](https://help.ubuntu.com/14.04/serverguide/network-file-system.html)

and I'm for some reason not able to mount the share. Usually it's share does not exist/not found. So can I type in the IP of the server followed by the share name or what's the command here?!

```
danny@UbntVM:~/Desktop$ sudo mount 10.0.0.20/nas:/ubuntu /local/ubuntu
mount.nfs: mount point /local/ubuntu does not exist


```

or is it

```
danny@UbntVM:~/Desktop$ sudo mount freenas/nas:/ubuntu /local/ubuntu
```

Neither works. I've also created a local/ubuntu directory on the root of the share. 

I've read that I should do NFS instead of SMB, if so then I suppose I should stick with that. Both services are enabled in the FreeNAS but I'm not able to permanently mount either. Though I am able to find and navigate the SMB share.

---

