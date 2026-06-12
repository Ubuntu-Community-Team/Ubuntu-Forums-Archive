---
title: "Change local folder permissions on Samba Share"
date: 2014-01-15
forum: General Help
---

### Post by drexlock on 2014-01-15
I recently replaced my home server running Server 2008r2 with an Ubuntu 12.04 Server. So far I've managed to get everything I need up and running without issue except for local folder permissions on my Samba share. My Samba shares are all under /media/Raid5 (Made a Raid5 array using mdadm) and I can access them over the network and make changes without issue. But when I'm logged in locally on the server any changes I make to the shares need to be run as root. 

How do I correct the local permissions so I can make changes without running as root? and will changing local permissions cause any issues with my existing Samba Shares?

---

### Post by tfrue on 2014-01-15
When I set up Samba I also set up a Samba user account so I can authenticate access for shares on my server. I set the account to the same as my local user account on my server so there wouldn't be any issues. I would say try and make the owner and group to your local account with *chmod* and see what happens, or try and add a Samba account.


It might also be important to note that you may have mounted the  share with root. sudo mount /dev/sda3 /media/Raid5, or however you  mounted the device since you use *sudo* it will mount the device with root permissions. You might be able to change the mount on fstab to look like:
```
#Raid5 mount on /media/Raid5
/dev/sda3 /media/Raid5 ext4 rw,user,exec,dev,suid,async 0 0 
```

That will allow any user to mount the device.

To change the owner and group of a file, type (Change chris to your username): 
```
sudo chown chris.chris /media/Raid5
```

You will need to changed the security under Authentication in smb.conf to *security=user*, you might just have to uncomment the line.

To add a Samba user, type:
```
sudo smbpasswd -a chris
enter password
re-enter password
```

Then under the share you defined in smb.conf, add "*valid users = chris*"  Which will allow only chris to have access to that share.

Hope this helps
Chris

---

### Post by tfrue on 2014-01-15
This is what my share with an external drive looks like just as a refernce:

```
[FreeAgent]
    comment= External Drive
    path= /share/free
    read only= no
    guest ok= no
    valid users= chris
    browsable= yes
    writeable= yes
```

---

