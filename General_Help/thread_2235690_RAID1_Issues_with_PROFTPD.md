---
title: "RAID1 Issues with PROFTPD"
date: 2014-07-22
forum: General Help
---

### Post by Gieter on 2014-07-22
Hello all,

Got a quick question. I've set up a RAID 1 with 1 TB discs, which is working fine. 

Although when i want to use the RAID (it is mounted to /media/%Usernam%/) i need to be logged into the system. 
If i am not logged in, i cant login with my FTP client. It gives me a "[SIZE=1][COLOR=#008000][SIZE=1][COLOR=#008000]530-Unable to set anonymous privileges. [/COLOR][/SIZE][/COLOR][/SIZE][SIZE=1][COLOR=#008000][SIZE=1][COLOR=#008000]530 Login incorrect." 
[/COLOR][/SIZE][/COLOR][/SIZE]although, when i log in to ubuntu on the PC, i am able to login.

I need to specify: I am able to connect to the RAID with ftp when logged in (locally) and opened the mounted RAID at least once. 

Maybe its possible to use a simple home directory of a user and then move the uploaded files  to the RAID with a sort-like script, but it seems like a unnecesary work around. 

If you need more information let me know. I think it has something to do with the permission, but i am not sure at this point.

---

### Post by steeldriver on 2014-07-22
Hello and welcome to the forums

Things in /media are usually the result of automounts - they belong to the session/user that's logged into the machine locally. For something like a RAID you should probably mount it as a proper system volume using /etc/fstab - that way it will be available regardless of the local session

---

### Post by Gieter on 2014-07-22
steeldriver,

Thank you for the information. Im still a bit rusty regarding linux. Been ages since ive worked with it. 
I will look into that. 

Thank you!

---

