---
title: "Permissions to access NTFS....?"
date: 2005-10-24
forum: General Help
---

### Post by Randy Sparks on 2005-10-24
On a default install I find an icon on the desktop letting me access my XP NTFS permission. But when I click on it, I'm told I don't have sufficient permission. Can anybody help?

---

### Post by aysiu on 2005-10-24
[http://www.ubuntuguide.org/#windows](http://www.ubuntuguide.org/#windows)

---

### Post by zenodaddy on 2005-10-24
Only thing that I can think of is that the drive has a password protected share on the windows side, or you need the root to access.

---

### Post by Randy Sparks on 2005-10-24
Apologies - perhaps I didn't make myself clear.

This is an AUTOMATIC mount under 5.10. I didn't mount it. This icon on the desktop appears straight after first boot. 

It's a mount of the NTFS partition on the same HD as Ubuntu. it's not a network share. There's no password protection on the NTFS drive (I'm not even sure if that's possible - the only protection NTFS offers AFAIK is encryption... and it isn't an encrypted partition).

So it appears there's a bug in 5.10 that means the drive is automatically mounted but the permissions aren't correct. 

My main question is whether I'm missing something important. I can fix this quite easily by a changed fstab entry, but I want to know how it's supposed to work.

---

### Post by Kyral on 2005-10-24
I wish to see your fstab. (Can't tell you what to modify if I don't know what is there)

---

### Post by aysiu on 2005-10-24
We understand your situation, but an icon on the desktop doesn't mean it's mounted. The /etc/fstab is the only thing that counts here. Please read the link I posted earlier.

---

