---
title: "Sharing NTFS mount over Samba hates me"
date: 2007-08-29
forum: General Help
---

### Post by justinlindh on 2007-08-29
I have an NTFS drive mounted via ntfs-3g that I'm trying to share on my SMB network. I've Googled the crap out of this, and failed to find anything that looked like it could help me, so here I am.

Here's the drive mounted in /etc/fstab:

# /dev/sdb1
UUID=F636425336421551 /media/sdb1     ntfs    defaults,nls=utf8,umask=022,gid=46 0       1

Here's my smb.conf entry for this mount:
[Music]
path = /media/sdb1/Music
available = yes
browsable = yes
public = yes
guest ok = yes
writable = no

Yes, I'm trying to share without login/pass (secured wired network, I don't mind). If it's relevant, here's the guest setting:
   guest account = nobody

The share is visible, but requires login beyond guest/<no pass>. I'm not even able to figure out which login it's looking for; my user account's doesn't work, neither does root.

Can someone please help? This is my last major frustration with getting this box set up perfectly.

---

### Post by justinlindh on 2007-09-03
Selfish bump; still haven't been able to figure this one out. Anybody?

---

### Post by qpieus on 2007-09-03
Since you don't want a password, go into /etc/samba/smb.conf and change the line that says

security=user

to 

security=share

That should allow for sharing without passwords.

---

### Post by justinlindh on 2007-09-05
> **qpieus said:**
> Since you don't want a password, go into /etc/samba/smb.conf and change the line that says

security=user

to 

security=share

That should allow for sharing without passwords.

Right, but I actually already have that. It looks like my non-NTFS mounts are sharing fine without authentication, it's just that my NTFS mount isn't.

Thanks for the help, though! Any other ideas?

---

### Post by inque_54 on 2007-09-05
@ Justin

May I ask how are you connecting to your music folder from your NTFS mount?

Have you tried connecting by putting the ip add of the box?

ex: //192.168.1.5/music

---

### Post by justinlindh on 2007-09-05
> **inque_54 said:**
> @ Justin

May I ask how are you connecting to your music folder from your NTFS mount?

Have you tried connecting by putting the ip add of the box?

ex: //192.168.1.5/music

You know, immediately after posting that reply, I tried accessing the shares again and it went through! I still have zero idea as to what was going on, but am just happy that it's working.

Thanks for the help. I wish I could post what I had done to make it work in case somebody else ran into the same problem, but I have no idea!

---

