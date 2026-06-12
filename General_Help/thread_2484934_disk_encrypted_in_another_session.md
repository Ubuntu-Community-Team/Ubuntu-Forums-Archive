---
title: "disk encrypted in another session"
date: 2023-03-14
forum: General Help
---

### Post by jose_fley on 2023-03-14
Hi, I have 3 drives in my computer, 1 with Linux and 2 encrypted. One with ext4 and one on NTFS. The encryption password works perfectly, but now I have created a new user and since that session he tells me that the password I am entering is wrong, I have checked it a thousand times and it always tells me that it is wrong

Thanks

---

### Post by MAFoElffen on 2023-03-14
Curious how you encrypted those drives...Usually a drive is encrypted by the system (root), not as per user... And usually the encryption for ntfs is bit-locker, which Linux cannot handle.

I am only thinking on this, because there are missing details on how you did this, and just how you set that up...

If you somehow encrypted an ext4 drive as per user, then it might be a permissions thing, where the original user is the owner and it's personal group is the owner group... I'm thinking that, if so, then if the group ownership was changed to a new group, that both users were members of, then both might have permission access to that drive.

I would like to know "how" you did that, so I could replicate that on a VM, to test what is going on, and how to correct that... That way, I could see what works, before recommending something, that might not work, and possibly lock you out of your drive. Better to be careful, and know before-hand. 

Please provide some details.

---

### Post by jose_fley on 2023-03-25
Hi,
sincerly, i not remenber very good when i incrypted the ext4 disk... When i did you use Linux Mint, Manjaro.... I honestly couldn't tell you exactly which operating system i did encrypted the ext4 disk
The second disk (ntfs) has been encrypted for more than 10 years. Kubuntu (the system I'm currently using) can decrypt it automatically, no need to use bit locker.

I will try to give privileges to the second user, maybe that will solve the problem of access to the club.

Rergards

---

