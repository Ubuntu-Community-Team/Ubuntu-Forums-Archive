---
title: "Permission issues on CIFS/NFS share"
date: 2020-12-29
forum: General Help
---

### Post by zaraki1311 on 2020-12-29
Hello,

I am running out of ideas on this issue. I have an Ubuntu 20.04 server setup with Docker installed. I am trying to mount a share from my QNAP so that a few of my dockers can read/write to it. On my QNAP I have Windows sharing enabled and NFS. The folder I am sharing has all the read write permissions set, I have set the NFS permissions to R/W NO_ROOT_SQUASH and set the uid/gid to a user and group with R/W access to the share.

If I mount with NFS I am able to write to the share with sudo from my user account but my dockers do not have permissions to write to the share but can read. I have tried setting the dockers to privileged but no luck. So I have tried mounting the share with cifs but writing to the share is a 100% no go no matter what I try, but reading seems to work fine. I am using the same creds as my windows machines that have no issues.

Any thoughts would be greatly appreciated. Below are my 2 different fstab lines.

192.168.0.225:/Video /Docker/movies nfs auto,nofail,noatime,nolock,intr,tcp,actimeo=1800 0 0

//192.168.0.225/Video/ /Docker/movies cifs rw,credentials=/etc/creds,uid=1000,gid=1000,file_mode=0660,dir_mode=0770 0 0

---

### Post by zaraki1311 on 2020-12-29
And after looking at the Share on the QNAP all the subfolders had broken permissions

---

