---
title: "Cannot access network  share Ubuntu--&gt;Ubuntu"
date: 2018-10-11
forum: General Help
---

### Post by lsutiger on 2018-10-11
I created a network share as per [these instructions]("https://www.howtogeek.com/176471/how-to-share-files-between-windows-and-linux/"), and reading a lot of other posts across the web on the subject once it failed - seems like there are plenty about Ubuntu<-->Win but not much about Ubuntu<--->Ubuntu. I have this setup in fstab at work between several systems but cannot get to work here at home for whatever reason.
When I try to access via Nautilus-->Connect to Server it brings up a login prompt. I input my username and password but it just pops back up.  
In the end what I am trying to do is have a MotioneyeOS system write files to this share,but I cannot even get two of the same versions of Ubuntu to share.
My smb.conf is the sample plus the lines from the link. 
Any thoughts?

---

### Post by SeijiSensei on 2018-10-12
For file sharing when both machines are running Linux, you should use NFS, not Windows CIFS.  

Any machines sharing files will need to install nfs-kernel-server.  Any client machines without a server need nfs-common.

See the instructions here for more details:  [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

---

### Post by Morbius1 on 2018-10-12
I have some questions:

[1] Are you saying that this share is accessible at work from Windows and Linux machines in that network but not at home?

[2] Which version of Ubuntu are you using on the server and client? Ubuntu 16.04, 18.04, ...?

[3] So if you go to the server and run this command:
```
testparm -s
```
Is this how samba sees your share definition:
> [Share]
    path = /home/geek/Desktop/Share
    valid users = geek
    read only = No
    guest ok = Yes
And did you add the valid user to the samba password database:
```
sudo smbpasswd -a geek
```

If you get warning or errors or if you share definition does not look like what I posted above post the entire output of:
```
testparm -s
```

---

