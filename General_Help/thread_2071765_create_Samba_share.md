---
title: "create Samba share"
date: 2012-10-16
forum: General Help
---

### Post by Drenriza on 2012-10-16
Hey guys.

I'am trying to create a samba share for a few users.

The share is as follows
```

[video1]
   comment = 2.5_Video1_share
   path = /srv/content/2.5/video1
   read only = yes
   create mask = 0700
   directory mask = 0700
   valid users = %S

```

[homes] are commented out since it's only the video1 i want to share.

**EDIT**
In my local server1 i got 4 NIC's, where i have bonded eth1 -> 3 to bond0.

My /etc/samba/smb.conf interfaces = bond0 and i restarted the service.
But when i try and connect i get a 
mount error 6 = No such device or address error.

I have tried and googled the issue and a solution, but nothing has changed.

Anyone who can help?

The mount command i use is as follows (local server2)
```
mount -t cifs -o username=user,password=pass //ip/video1 sambaTest.d/
```

---

### Post by CrusaderAD on 2012-10-16
Can't you just make a valid group of users rather than naming each user? That might have better results.

---

### Post by Drenriza on 2012-10-17
> **CrusaderAD said:**
> Can't you just make a valid group of users rather than naming each user? That might have better results.

Wow the worlds least meaningful reply.

IF! your referring to, having a linux user which is the same as the samba user (name). Then i already have that, and i still have the issue.

**EDIT**
[B]First post is edited since the problem has changed a bit.
#2 is a answer to i had a issue where valid users was = $s and with this macro i could not connect to the samba server and got a connection refused.
This problem was solved with valid users = nice, and i asked what the $s meant.

And yes i got a linux user and samba user both called nice with sync in /etc/samba/smb.conf = yes.[/B]

---

### Post by Drenriza on 2012-10-17
Anyone who can help me out?

Skip #2 and #3 ("old" issue)

Thanks on advance.
Kind regards.

---

### Post by CrusaderAD on 2012-10-17
> **Drenriza said:**
> Wow the worlds least meaningful reply.

If you want help, you're going about it the wrong way, good luck. You're gonna need it.

---

### Post by Drenriza on 2012-10-18
> **CrusaderAD said:**
> If you want help, you're going about it the wrong way, good luck. You're gonna need it.

When i offer my help to others i don't do it in a annoying tone.

Solved
/etc/samba/smb.conf path was incorrect.

---

### Post by CrusaderAD on 2012-10-18
Guess you're right, it did sound annoying when I re-read it. That wasn't my intention. I wasn't trying to be facetious or degrading. Glad to see you fixed it.

---

