---
title: "Windows share problem"
date: 2007-02-03
forum: General Help
---

### Post by DrClaw27 on 2007-02-03
I have a 2003 DC running active directory that has some shares I need to access. I put the following file in my fstab and I have no problem accessing, deleting or opening any files on the share

//192.168.0.4/share$ /media/share cifs username=NAME,password=PASS,domain=DOMAIN 0 0

The problem is when I open and save a file or create a new one it becomes read only and I can't make anymore changes to it but I can still delete it or rename it.  I'm really stuck on this one and any help would be great.

---

### Post by DrClaw27 on 2007-02-06
How about this... does anyone have it working in the above configuration?

---

### Post by Buck2348 on 2007-02-07
> **DrClaw27 said:**
> How about this... does anyone have it working in the above configuration?
I'm far from an expert, but I seem to remember similar difficulties when I first mounted Windows shares, with the fix being to give myself ownership of them.  Here is the line in my /etc/fstab for one of the shares:

```
//fezzik/SharedDocs /mnt/fezzik/SharedDocs  smbfs  gid=46,uid=1000,user,username=share,password=    0    0
```

The "uid=1000" is what I think is the relevant part.  Your user id is 1000 also if you were the first user on the system.  If you're not sure of your uid, type "id" in a terminal.  If this doesn't fix it it at least should do no harm.

Buck

---

### Post by DrClaw27 on 2007-02-07
Thank You! Thank You! Thank You! I was really stating to think that nobody was going to be able to help me. The only thing different in my setup is I'm using cifs instead since I could never get smbfs to work at all. I know what the gid and uid are but how do you determine the number for each?

---

### Post by Buck2348 on 2007-02-08
> **DrClaw27 said:**
> Thank You! Thank You! Thank You! I was really stating to think that nobody was going to be able to help me. The only thing different in my setup is I'm using cifs instead since I could never get smbfs to work at all. I know what the gid and uid are but how do you determine the number for each?
You're very welcome.  I hope this will solve your difficulty.  You can find your uid and the gid for every group of which you are a member by entering "id" in a terminal.  As best I can recall I used the gid=46 because it was there already on my other mounted partitiions.  Your uid is "1000" if you are the original user who installed your system.

Regards,
Buck

---

