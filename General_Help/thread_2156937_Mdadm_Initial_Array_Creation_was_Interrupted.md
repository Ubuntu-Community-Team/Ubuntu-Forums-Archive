---
title: "Mdadm Initial Array Creation was Interrupted"
date: 2013-06-23
forum: General Help
---

### Post by boshkash1151 on 2013-06-23
I am trying to create a new 3-Disk S/W RAID 5 configuration using mdadm, but while the process of building the array was running the system froze and I had to force restart the system. 

Would interrupting the initial sync mess the parity blocks and result in future data corruption when recovery is needed ?

Thanks for your help

---

### Post by SaturnusDJ on 2013-06-24
Yes.
[https://raid.wiki.kernel.org/index.php/Initial_Array_Creation](https://raid.wiki.kernel.org/index.php/Initial_Array_Creation)

---

### Post by boshkash1151 on 2013-06-24
> **SaturnusDJ said:**
> Yes.
[https://raid.wiki.kernel.org/index.php/Initial_Array_Creation](https://raid.wiki.kernel.org/index.php/Initial_Array_Creation)


but i did not skip the initial step and when I tried to use the --assemble the mdadm continued creating the parity where it left


I could not start the process of creating the array from scratch all over again because it takes about 66 hours and there is high possibility of black outs during that period that even a UPS won't sustain. Therefore how could I ensure that everything is fine and the array is consistent ?. 

In other words, how could I create a RAID5 array using mdadm where the process won't be performed in a single shot ?

---

### Post by SaturnusDJ on 2013-06-24
I guess it's okay if it continues where it left...but why at all setup a computer with RAID if you can't ensure basic stability...

---

### Post by boshkash1151 on 2013-06-24
> **SaturnusDJ said:**
> I guess it's okay if it continues where it left...but why at all setup a computer with RAID if you can't ensure basic stability...

I can't ensure the electricity stability which is something I have limited control over (UPS can't totally solve the problem). Also the blackouts risk the hard disk sustainability and so a form of redundancy is needed.

How can I check that data integrity is OK? and no future corruption would occur ?

---

### Post by SaturnusDJ on 2013-06-24
According to the website you should setup a degraded three disk RAID5. 
Then I would enable bitmap first ([https://raid.wiki.kernel.org/index.php/Bitmap](https://raid.wiki.kernel.org/index.php/Bitmap)).
After that, add the third disk, causing a recovery.

That way it must be save.

To test, you can force a disk to fail and check if the data is still intact. Then add the drive back (will go super fast with bitmap enabled), and fail another and check if the data is still intact.

---

### Post by boshkash1151 on 2013-06-24
> **SaturnusDJ said:**
> According to the website you should setup a degraded three disk RAID5. 
Then I would enable bitmap first ([https://raid.wiki.kernel.org/index.php/Bitmap](https://raid.wiki.kernel.org/index.php/Bitmap)).
After that, add the third disk, causing a recovery.

That way it must be save.

To test, you can force a disk to fail and check if the data is still intact. Then add the drive back (will go super fast with bitmap enabled), and fail another and check if the data is still intact.


but based on the website, bitmap just speed the process of recovery by resyncing only changed blocks, but how could it ensure the data integrity ?

---

### Post by SaturnusDJ on 2013-06-24
By the test I told.

---

### Post by boshkash1151 on 2013-06-24
yes but that would test the portion of data that I had written which is based on my case might be in the blocks that was synced before the first black out. In other words I could not guarantee that any data placed for test would be placed within the blocks that were impacted by the blackout.

Is there a way for example to recompute the parity again ?. I know that there is a check command that could be executed using the checkarray script installed with mdadm, would that script guarantee a consistent array ?

---

### Post by SaturnusDJ on 2013-06-24
If you know where the sync was at the moment of the outrage, you can create a partition there, write data and test.

I don't know for sure about the check command, but thinking about it, what else but parity is there to check at a mdadm array?

---

### Post by rubylaser on 2013-06-25
The mdadm check is going to verify the parity, and would be one way to verify the data. Another way, would be to md5sum some of the files and verify that are the same after the sync.  

If power is really this inconsistent, I would definitely invest in a UPS, and I'd be using SnapRAID for home vs. mdadm.  mdadm is fantastic, and I'm a big advocate for it, but in this case, SnapRAID will likely be a better choice.  Each disk contains it's own filesystem, and it's initial sync will be nearly instantaneous on empty disks.  I have setup directions in my signature.

---

