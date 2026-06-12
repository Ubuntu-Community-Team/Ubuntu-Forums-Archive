---
title: "Best way to Remote My Document Storage? (low power consumption if possible)"
date: 2013-10-08
forum: General Help
---

### Post by 777funk on 2013-10-08
I am wanting to get all of our home network's Documents on a single remote location and I'd like to do it without running a dedicated machine if possible (in order to save electricity costs). Is it possible to run a bunch of hard drives without adding a desktop? Maybe I should just put the storage in machines that are already on. But I'm looking to see if there are other options. I'd like to have about 10TB worth of storage for our videos, pictures, music, etc.

So I guess this is a hardware question more than anything. 

On the software side, I have felt Ubuntu is a more stable (and faster) operating system than XP was (in my experience so far). I'd like to point all of the document folders in Ubuntu to these main document folders. How would I do this? The folders would be shared by Win and Linux machines so I guess that would mean NTFS format.

---

### Post by Lars Noodén on 2013-10-08
The drives have to go into a computer of some kind.  If you can add them to one that is usually on then you save some power.  But the drives themselves will consume electricity.   Also, be sure to have a backup plan for the server and implement it.  If you are worried about drive failure, you could go RAID 1, but that would be supplemental to a backup plan. 

If you're connecting a mixture of Linux and legacy machines you could use NFS or Samba.  Both will do the job.

---

### Post by CharlesA on 2013-10-08
> **Lars Noodén said:**
> The drives have to go into a computer of some kind.  If you can add them to one that is usually on then you save some power.  But the drives themselves will consume electricity.   Also, be sure to have a backup plan for the server and implement it.  If you are worried about drive failure, you could go RAID 1, but that would be supplemental to a backup plan. 

If you're connecting a mixture of Linux and legacy machines you could use NFS or Samba.  Both will do the job.

Pretty much nailed it. You'd definitely need a 4 (or more) bay NAS if you don't want it hooked up to a "computer".

I'm running my NAS on a home built box, but it's also being used as a VM host and not just for file storage. It's running RAID6 with 5 3TB drives, but I would suggest looking into [SnapRAID]("http://zackreed.me/articles/72-snapraid-on-ubuntu-12-04") if you want a DIY solution.

---

