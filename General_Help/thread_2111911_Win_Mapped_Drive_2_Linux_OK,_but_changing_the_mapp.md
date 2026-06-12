---
title: "Win Mapped Drive 2 Linux OK, but changing the mapped drive to an other Win PC  Not OK"
date: 2013-02-03
forum: General Help
---

### Post by Carlo Jongen on 2013-02-03
I need to move a mapped drive called "renderfarm_cfg" from a computer called:
=> 3D_PC ( Win7 64bit ) with **IP:192.168.2.2** ( This config works but I need to change it )
to an other computer called:
=> LICENSE_SERVER ( Win7 32bit ) with ** IP:192.168.2.3**

So I moved the map "renderfarm_cfg" to LICENSE_SERVER and shared it, I un-Shared this map in the 3D_PC.

Now to mount this on the Linux machine I tought I just replaced the IP address in the last line of the "fstab" from the first code to the second one ( see below ).

```
//192.168.2.2/renderfarm_cfg /media/winshares/renderfarm_cfg cifs auto,credentials=/etc/smbcredentials,workgroup=UPG_Network,gid=smb,uid=1000,file_mode=0770,dir_mode=0770,rw 0 0
```

change to

```
//192.168.2.3/renderfarm_cfg /media/winshares/renderfarm_cfg cifs auto,credentials=/etc/smbcredentials,workgroup=UPG_Network,gid=smb,uid=1000,file_mode=0770,dir_mode=0770,rw 0 0
```

But apparently this doesn't work.
Why doesn't this work? What else do I need to change for this mapped drive to work?
It works when the map is shared on the 3D_PC but not when it is shared on the LICENSE_SERVER.
The workgroup and the credentials (/etc/smbcredentials) are the same for both systems.
I disabled the fireWall to make sure this was not blocking the communication.

Trying to manually connect to this shared map with the next code worked, but this doesn't work in the fstab.

```
sudo su
mount -t cifs //192.168.2.3/test /media/winshares/test -o username=myusername,password=mypassword
```

Anybody have a tip on how to solve this issue.


--------------------------------------------------------------------------------------------------
Freelance 3D animation at [www.c3d.be](www.c3d.be)

---

### Post by Carlo Jongen on 2013-02-11
Apparently this code works:
```
//192.168.2.3/test /media/winshares/test cifs users,uid=1000,rw,suid,credentials=/etc/smbcredentials,workgroup=UPG_Network 0 0
```

---

