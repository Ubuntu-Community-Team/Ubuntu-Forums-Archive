---
title: "How many user can Samba service for?"
date: 2015-01-23
forum: General Help
---

### Post by Nguyen_Phi_Long on 2015-01-23
Dear all,

I'm using Samba for my office.
Now It's serving about 1000 Users, (connect same time).
it's download and upload speed is more slower when it serviced for about 500-600 users.

I don't know how many user Samba can service.
I have tried to find answer on google, but now I can not get this info.

Anyone, Please kindly let's me know How many users can Samba service for?

Thank you so much.
Have a good time.

---

### Post by HermanAB on 2015-01-23
There is no definite answer.  It depends on what the users are doing.  However, I would not use a single Samba server for more than 500 users.  You need to figure out how to spread the work load over 3 or more machines.

---

### Post by Nguyen_Phi_Long on 2015-01-23
Thank Herman so much.

---

### Post by SeijiSensei on 2015-01-23
Are you running Gigabit Ethernet?  See any bandwidth or collision problems?  If you transfer files directly from one client to another with Windows networking, are the speeds dramatically better?

---

### Post by Nguyen_Phi_Long on 2015-01-24
Thank SeijiSensei,

We are using Gigabit Ethernet, I checked bandwidth of Samba server network, it is usually used about 50% only. 
About slow speed, I can see that bottleneck at Read/Write Disk storage. WaitIO CPU is hight, it's about 40%, when I check iotop command, there many users are read/writing disk.
Storage: XFS filesystem
Mount options: xfs (rw,noatime,nodiratime,nobarrier,logbsize=256k,allocsize=512M,inode64)

Please kindly give me your advise how to improve read/write disk speed.

Thank you so much.

---

### Post by SeijiSensei on 2015-01-24
I'm not an XFS fan, so I can't help with that.  Is the storage medium a RAID array or a single drive?  RAIDs tend to have faster read performance, but slower write performance, than single drives.

In terms of speeds, are you using 15K drives, or slower 7200 or 5400 rpm drives?  Faster drives in a RAID array might help.

Another question is why there is so much continuous traffic? Most of the time people will read a file from storage, work on it, then write it back.  For so many users to be engaged in continuous disk usage suggests this a feature of whatever applications you are using. If these are commercial "enterprise" apps, have you spoken with their support people about methods to improve performance?

---

### Post by SeijiSensei on 2015-01-25
Also how beefy is the server hardware?  For 1,000 simultaneous users with all that disk activity you probably should be looking at something in [this ballpark](http://configure.us.dell.com/dellstore/config.aspx?oc=bect34r&model_id=poweredge-t320&c=us&l=en&s=bsd&cs=04).

---

