---
title: "auto-repair for fstab - surely I am missing something obvious"
date: 2007-09-06
forum: General Help
---

### Post by ctsdownloads on 2007-09-06
Obviously, there is no way new users have an interest in learning to repair a corrupt fstab - it's just silly as most people simply want function, not an education. So what would the suggested method for restoring or auto-repairing fstab be? I am sure there is a way, considering it is so badly needed. Again, not trying to put anything down, but good gravy, editing something as important as fstab from scratch is completely unrealistic for new users.

I am almost sure I had a method any one point, but cannot remember it for the life of me...

Thanks

---

### Post by reckless2k2 on 2007-09-06
umm...i just edit fstab using sudo nano /etc/fstab. if you understand a little about fstab then you should be fine. is there an auto repair feature? i don't think so. i could be wrong.

---

### Post by Jose Catre-Vandis on 2007-09-06
What is wrong with your fstab?

Detail the contents of your fstab here, explain what you are trying to acheive, and we can hopefully help to resolve your issues :)

---

### Post by Steve1961 on 2007-09-06
I've never seen an automatic repair method either.  I think most of us just edit it as necessary - all part of the learning process.

---

### Post by reckless2k2 on 2007-09-06
that eye is hypnotizing me.

---

### Post by Steve1961 on 2007-09-06
> **reckless2k2 said:**
> that eye is hypnotizing me.

LOL :)

---

### Post by ctsdownloads on 2007-09-07
Thanks all. 

No, nothing is wrong with my fstab right now. However I am  rather disappointed that there is not a repair feature available.  That is a lot for a new user to deal with, despite it being part of the learning curve during the switch.

Question: Would it be possible to grab the fstab from the LiveCD to replace a damaged one? Again, just thinking there has to be a simpler way that is not so likely to create user frustration during their first few weeks of Ubuntu.

Thanks

---

### Post by merlinus on 2007-09-07
IIRC, fstab on the live cd is quite sparse, since very little is automatically mounted.

And unlike xorg.conf, it does not seem to make automatic backups.

-merlin

---

### Post by confused57 on 2007-09-07
> **ctsdownloads said:**
> Thanks all. 

No, nothing is wrong with my fstab right now. However I am  rather disappointed that there is not a repair feature available.  That is a lot for a new user to deal with, despite it being part of the learning curve during the switch.

Question: Would it be possible to grab the fstab from the LiveCD to replace a damaged one? Again, just thinking there has to be a simpler way that is not so likely to create user frustration during their first few weeks of Ubuntu.

Thanks
There's no automated method to "reconstruct" or repair fstab...the only way I'm aware of is to create a backup of a working fstab:
```
sudo cp /etc/fstab /etc/fstab_backup
```
then to restore it:
```
sudo cp /etc/fstab_backup /etc/fstab
```

Since there is a chance that you can't boot your system with an incorrect fstab, you should be able to mount the root partition, using the live cd, then restore the backup from there:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

---

