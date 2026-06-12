---
title: "Clone OS drive?"
date: 2013-02-14
forum: General Help
---

### Post by spacecakes on 2013-02-14
Hi, i run linux on a 640gb drive and i got a 40gb ssd not being used so i thought i would change it, is there a way to just clone an entire os drive with partitions and all to another drive and just replace them?

---

### Post by howefield on 2013-02-14
What exactly is it that you want to do ?

Is your intention to take the contents of the the 640 gig drive and clone to the SSD ?

---

### Post by Bufeu on 2013-02-14
Yes, it's, of course, possible. Use the command *dd*.

---

### Post by Zteam on 2013-02-14
Don't use dd, it's very slow and will clone everything on the drive (included unallocted memory)

Use Clonezilla instead.

---

### Post by Bufeu on 2013-02-14
> **Zteam said:**
> Don't use dd, it's very slow and will clone everything on the drive (included unallocted memory)

Use Clonezilla instead.
No, actually *dd* is quite good, and you'll get everything on the drive. You can, though, set it to not clone unallocated space.

---

### Post by howefield on 2013-02-14
> **Zteam said:**
> Use Clonezilla instead.

Clonezilla won't go from big drive to smaller ?

Otherwise, I'd agree :-)

---

### Post by oldfred on 2013-02-14
dd will not go from big 640GB drive to 40GB SSD either. :)

Actually dd is designed for same size to same size drives. And its nickname is data destroyer as any typo can cause major issues.

Is it just / (root) that you want to copy and you have seperate /home?

If you do any type of clone you will have issues of duplicate UUIDs and have to change UUID, then edit fstab and reinstall grub2.

I generally suggest a new install is easier.

       [https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)

---

### Post by howefield on 2013-02-14
> **oldfred said:**
> I generally suggest a new install is easier.

+1 

Shiny new SSD and shiny new pristine install sounds pretty decent :-)

---

### Post by Bufeu on 2013-02-14
> **oldfred said:**
> dd will not go from big 640GB drive to 40GB SSD either. :)

Actually dd is designed for same size to same size drives. And its nickname is data destroyer as any typo can cause major issues.

Is it just / (root) that you want to copy and you have seperate /home?

If you do any type of clone you will have issues of duplicate UUIDs and have to change UUID, then edit fstab and reinstall grub2.

I generally suggest a new install is easier.

       [https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
No, *dd* can clone to drives with same size or bigger. Same thing with any cloning tool; if you are doing wrong, you get problems.

---

### Post by spacecakes on 2013-02-14
thanks for the answers guys! i think ill go with a new install, backup what i need from the old one and just do a new :)

---

