---
title: "Unable to mount network drive with sshfs"
date: 2014-09-14
forum: General Help
---

### Post by kieran5 on 2014-09-14
Hi

I am experiencing difficulty automounting a network drive with sshfs via fstab. 

Background;
The drive is formatted as ext4 and located on a media server running Ubuntu 14.04 32bit
I am trying to mount it at start up on a client machine runnung Ubuntu 14.04 64 bit
The machines are configured to communicate via a ssh key/trusted machine (I have confirmed this as part of my own attempts to troubleshoot)

The drive appears to mount (albeit as a binary in /media directory) but I am denied access due to not having the required permissions. I can not check the owner or permissions from command line or nautilus. I can manually mount the drive easily. When manually mounted it mounts as the wrong UID most likely as descrepancy between server/client UIDs. 

This is my current fstab entry;

sshfs#USERNAME@192.168.1.22:/media/EXTHDD1    /media/EXTHDD1     fuse.sshfs     auto, _netdev, idmap=user, uid=499, gid=499, allow_other, user, rw     0       0

I have tried numerous options and variations to no avail. I have scoured most threads related to this and all suggestions have not worked. At my wits end!

---

### Post by steeldriver on 2014-09-14
Hello and welcome to the forums

Can you explain what you mean by "albeit as a binary file" please? Can you also confirm that you don't have spaces as shown in the list of mount options (use [CODE] tags around code snippets if possible)

---

### Post by kieran5 on 2014-09-15
When I navigate to the mount point in nautilus there is a file there called EXTHDD1, if I right click the file to inspect it it says it is a binary file and all other info is absent. It also says "permissions could not be determined"
What did you mean by spaces in the mount options list? Do you mean in the fstab entry? fstab options are separated by a comma then a space.

---

### Post by steeldriver on 2014-09-15
AFAIK the list of mount options in the /etc/fstab file needs to be comma separated with no whitespace i.e.

```

sshfs#USERNAME@192.168.1.22:/media/EXTHDD1    /media/EXTHDD1      fuse.sshfs     **auto,_netdev,idmap=user,uid=499,gid=499,allow_other,user,rw**     0       0

```

Try it and see if it makes any difference

---

### Post by kieran5 on 2014-09-15
Yep that worked an absolute treat! The drive is mounting as intended. I am mortified that I overlooked something so simple!
Thanks very much for your help.

---

