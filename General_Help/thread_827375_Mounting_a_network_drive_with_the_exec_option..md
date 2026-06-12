---
title: "Mounting a network drive with the exec option."
date: 2008-06-12
forum: General Help
---

### Post by trentrolf on 2008-06-12
I have added an entry in my /etc/fstab that mounts a network drive to my /mnt/ folder.  I want to execute scripts from this mount, so I added the 'exec' option like this (x's to hide ip address): 

//x.x.x.xxx/trolf /mnt/smb/bssbuild smbfs rw,auto,exec,users,noatime,uid=1000,gid=1000,workgroup=dbxeng,credentials=/home/trolf/.cred_bss 0 0

I mount using "sudo mount -a"

Then if I type 'mount' from the command line I get:

//xx.x.x.xxx/trolf on /mnt/smb/bssbuild type cifs (rw,mand,noexec,nosuid,nodev)

Notice the NOEXEC!!  What is going on?

---

