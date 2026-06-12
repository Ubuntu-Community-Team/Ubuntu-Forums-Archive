---
title: "All Users Samba Share Stopped Working"
date: 2013-09-27
forum: General Help
---

### Post by firebadger on 2013-09-27
Hi,

I'm stumped with a samba problem. I've got a share defined like this that has worked fine for years but after a recent update no longer allows anybody to connect. Any ideas?

```
[all_users]
   comment = All users
   path = /home/shares/all_users
   valid users = @users
   force group = users
   force create mode = 0660
   force directory mode = 0770
   writable = yes
```

I'm running Ubuntu 12.04.3 LTS on the server.

Thanks!

---

### Post by bab1 on 2013-09-28
> **firebadger said:**
> Hi,

I'm stumped with a samba problem. I've got a share defined like this that has worked fine for years but after a recent update no longer allows anybody to connect. Any ideas?

```
[all_users]
   comment = All users
   path = /home/shares/all_users
   valid users = @users
   force group = users
   force create mode = 0660
   force directory mode = 0770
   writable = yes
```

I'm running Ubuntu 12.04.3 LTS on the server.

Thanks!
I have 2 Ubuntu 12.04.3 servers with Samba Server running on them.  I use the user group *users* also.

Are you saying that you (or anyone else in the group users) can't authenticate to the share?  What diagnostic tests have you run?  Have you checked the group membership```
getent group users
```...are all the users in this group?  How about the smbpasswd database?  You can check that like this```
sudo pdbedit -L
```

Have you set the debug on to check any failures?  I do this to check the authentication```
smbclient -d3 -u /NETBIOS_NAME/SHARE
```...you can substitute the IP address if you want.

Post your results here.  Then we can help you.

---

### Post by firebadger on 2013-09-29
Hi Bab1,

Thanks for the help.

I didn't post much additional information because I suspected it must be an update problem as it was working and I'm fairly sure that nothing has changed since then bar installing updates.

However, the group membership looks fine. All users present and correct.

Everybody is also in the smbpass database. Thanks for that command - I didn't know about it.

I do no more about the extent of the problem though. I have several shares, some for specific users and some for specific groups. It seems that the only problem is for shares for this users group. The problem also seems limited to the cifs mounts in my fstab and a Windows machine. I was able to access them using the smbclient command and also by browsing to them in Dolphin. All mechanisms were working until a week or so ago.

I'm going to experiment a bit and if I resolve it I'll post an update. In the meantime, if you have any further thoughts I'd be very happy to hear them. Thanks again.

Alan

---

### Post by firebadger on 2013-09-29
Well, seem to have it cracked. Seemed to be a permissions problem on the directory itself. Was pretty sure nothing could have changed there, but clearly it did.

Thanks again,
Alan

---

