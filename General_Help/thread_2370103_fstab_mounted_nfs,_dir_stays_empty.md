---
title: "fstab mounted nfs, dir stays empty"
date: 2017-08-30
forum: General Help
---

### Post by evillian on 2017-08-30
Hello Everyone, 

I have a NAS with NFS shares. I have the following in /etc/fstab:

```

# Remote shares
192.168.1.10:/Public /home/evillian/Shares/Public nfs defaults 0 0
192.168.1.10:/homes /home/evillian/Shares/homes nfs defaults 0 0

```

To make sure it´s not a permissions thing, i gave 777 to every of these dirs on the client PC.
After boot they seem mounted, but the dirs are empty. If i remove these lines from the fstab file, reboot, add them to fstab and use ´sudo mount -a´ it is working okay.
The funny thing is: My laptop has everything the same and it works (Wifi)

I thought it has to do with fstab loading before the network, but that does not make sense because they seem to mount.

Anyone ideas?

---

### Post by TheFu on 2017-08-31
It is usually a bad idea to mount storage under a HOME directory.  Mount it somewhere else and make symbolic links FROM the HOME directory to make it easier to access, if you must.

2nd, the last number shouldn't be 0 on those lines in the fstab. 2 is what they should be.

3rd 777 is a terrible idea.  For testing, I suppose it is fine, but not longer than a few minutes. 

Ok, onto gathering data so we can actually help.
Please run these commands and post both the command and the output using "code tags" --- like this:
```
$ mount |grep 192.168.1.10
$ df | grep 192.168.1.10
$ ls -l /home/evillian/Shares/Public /home/evillian/Shares/homes
```

Seeing the owner of the mount points AFTER they are mounted is important.

---

