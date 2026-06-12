---
title: "Sharing folders on network"
date: 2007-09-19
forum: General Help
---

### Post by rmausser on 2007-09-19
Ok, so this is a bit of a problem i've had for a while, and i've just ignored it by doing things backwards, but I cant seem to share files from my ubuntu computer.

The weird thing is, I can see my ubuntu computer on the windows network, access it from any windows computer, and even access windows computers and their files from it. 

So, I can transfer files say, but I have to share a folder on my windows Pc and drop files INTO it from the ubuntu computer. So files will move in that direction, I just cannot seem to successfully share a folder so that I can see it from the windows PC, and drag the files out of it.

I can right click on a folder and access the share utility, and I tell it to share on the SMB windows network. After I click OK, nothing happens. The folder doesn't appear to be shared, and when I check the network, it is not. THe only thing shared is my printer and some old folder that I deleted long ago, but is still being shared from when I was able to.

Can someone please help me? I went over the tutorial on Samba on Youtube with no sucess.

Thanks.

---

### Post by ecor6633 on 2007-09-19
Sharing folders are configured in /etc/samba/smb.conf.

Have a look at that file.
You can change your workgroup if needed :
```
     workgroup = MS_HOME
```
You can enable or disable diffrent name resolving systems:
```
    name resolve order = lmhosts host wins bcast
```

At the end of the file i place this to share a folder :
```

[shared]
   path = /home/login/shared
   available = yes
   browsable = yes
   public = yes
   writable = yes
   valid users = login,dropbox,guest,nobody

```

After that you have to create a user and set its samba password.
I personnaly created a user with adduser (see man adduser) who hasn't any home folder and cannot login.

To change its samba password see man smbpasswd

I hope it will help you.



If someone can explain which user we should create so that MS Windoze can login whitout asking password, I'm interested.

---

### Post by adza on 2007-11-20
hi there, i think this is fits in this thread.. i am trying to setup a samba share to see it on my xbox media centre... i've done the entries as suggested, is there some way i can verify that this is correct? Do i need to restart the samba server for example??

---

