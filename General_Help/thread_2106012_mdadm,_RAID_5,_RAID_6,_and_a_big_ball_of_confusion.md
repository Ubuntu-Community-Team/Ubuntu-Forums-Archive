---
title: "mdadm, RAID 5, RAID 6, and a big ball of confusion."
date: 2013-01-17
forum: General Help
---

### Post by Roasted on 2013-01-17
As my uses for larger storage devices grows, I've been considering on switching over to a RAID setup, particularly 5 or 6. I think what I need out of it may dictate which one to go with, but I'm not sure I understand enough about both scenarios to decide where to go with it.

I'm using Ubuntu Server 12.04.1. I've used mdadm before, but only for a RAID 1 mirror in my desktop. I'm very curious about learning the pros and cons of each, so hopefully somebody can chime in here with some insight.

My target will likely be 2TB HDDs. I'm told that I can create RAID 5 with 2x2TB HDDs, which will effectively act as a mirror. Then later on I can add 2x2TBs in addition and grow the RAID 5 accordingly, bringing the total count to 4x2TB HDDs. I assume this would effectively give me 6TB to play with, with the remaining 2TB being a parity drive (3 drives data, 1 drive parity). Is this correct?

Moving along, some people also suggested RAID 6 because it utilizes two parity drives instead of one. The only really significant "con" I could brew up with RAID 5 is with resyncing the array after a drive failure. For example, if I'm running RAID 5 with 4 HDDs, meaning 3 in use and 1 as parity, and one drive dies, I'm down to 3 total. Well, 3 is required for the RAID 5 to run effectively with no data loss. If I add a brand new 4th drive in the mix, it'll of course need to resync. During this time the other 3 HDDs will be pushed pretty heavily in terms of performance, which of course heightens the chance of another failure. This is the one scenario where some people gave RAID 5 a -1 because if one of the 3 HDDs dies, I could have data loss, corruption, or worse - an entirely failed array.

RAID 6 on the other hand seems to utilize two parity drives, which takes a performance hit since you have two parities instead of one, but that's understandable. That being said, what exactly is required to run a RAID 6? Can I run a RAID 6 with 4x2TB with two parity drives? This would diminish my disk space substantially (4TB usable, 4TB parity), but can it be done?

I also understand RAID 5 can be converted to RAID 6. Can this be done with live data on the array? Of course, I'd make a backup, but if this can be done it'd be a solid bonus. That way I COULD (in theory) effectively make a 2x2TB RAID 5 array, then later add two more HDDs bringing it to 4x2TB, and convert the RAID 5 to RAID 6 and be running with two parity instead of one. Eh?

Originally I was very anti RAID with this server and figured I would simply have two hard drives... drive A and drive B. Drive A would be what is actively used, while drive B is a backup drive that drive A rsyncs to every night. The thing is, somebody asked me, "What if you want to add another hard drive for more space?" That's when it hit me that RAID just might be the ticket. After all, I could purchase another 2TB drive, add it accordingly, and I'd have more space available.

(this is also assuming I integrate LVM with this scenario, which is still an area I'm a little unsure of just yet in terms of how to implement it... but that's another topic)

Any insight?

EDIT - so I was doing some digging this evening and RAID 10 kept coming on the radar. Some people even suggested that RAID 10 has eclipsed RAID 5, and that RAID 5 is in some cases obsolete. Of course I began reading about RAID 10 more at this point, which sounds like it's effectively a pair of RAID 0 mirrors. Meaning you have drive A/B that are seen as one mirroring drive C/D that are seen as one. Everything I read suggests that RAID 10 is the better way to go in terms of performance as well as redundancy (for the most part). It sounds like RAID 6 takes a +1 in the redundancy department due to the fact RAID 6 can lose any two drives and be fine, whereas RAID 10 is only resilient against losing two drives IF those two drives aren't on the same block. That said, more reading suggested that the rebuild time for RAID 10 is significantly faster than RAID 5 and RAID 6, thereby giving more credit to RAID 10 due to its lessened HDD degredation during the sync up time.

All of this has me considering RAID 10 instead. The only downsides I'm reading are RAID 10 is a 50% volume loss (since it's effectively a mirror, so if you have 4x1TB you have 2TB usable, not 4), and the fact that if you magically lose the two drives on the same block you would thereby have data loss. That said, RAID 10 is looking more attractive. Any insight on this?

---

### Post by sciguy125 on 2013-01-18
This is my favorite source for mdadm:
[https://raid.wiki.kernel.org/index.php/Linux_Raid](https://raid.wiki.kernel.org/index.php/Linux_Raid)

You seem to be factually correct on most things.  I'm not sure about converting RAID 5 to 6, and I'm reasonably sure that a RAID 5 with only 2 disks doesn't offer any redundancy.

Personally, I use RAID 5 because I only use a few drives (as you plan to).  In my opinion, it offers the best balance between redundancy and available capacity.  RAID 5 capacity is n-1 (e.g. a 4 drive array has the capacity of 3 drives).  RAID 6 is n-2 (e.g. a 4 drive array has the capacity of 2 drives).  6 offers better redundancy because you can survive 2 simultaneous drive failures.

It's true that another drive could fail while rebuilding the array.  But, think about what the likelihood of that is.  On my system, it takes about a day to resync a 3x2TB RAID 5 array.  There's a total of ~15 drives in all the systems I take care of, and I see a drive failure once every ~5 years.  If you think it's likely that you will see a second drive fail in the day or so that it takes to replace a failed drive, then you might be more comfortable with RAID 6.  However, I'd rather have the extra capacity and take the risk.

---

### Post by bab1 on 2013-01-18
> **Roasted said:**
> As my uses for larger storage devices grows, I've been considering on switching over to a RAID setup, particularly 5 or 6. I think what I need out of it may dictate which one to go with, but I'm not sure I understand enough about both scenarios to decide where to go with it.

I'm using Ubuntu Server 12.04.1. I've used mdadm before, but only for a RAID 1 mirror in my desktop. I'm very curious about learning the pros and cons of each, so hopefully somebody can chime in here with some insight.

My target will likely be 2TB HDDs. I'm told that I can create RAID 5 with 2x2TB HDDs, which will effectively act as a mirror. Then later on I can add 2x2TBs in addition and grow the RAID 5 accordingly, bringing the total count to 4x2TB HDDs. I assume this would effectively give me 6TB to play with, with the remaining 2TB being a parity drive (3 drives data, 1 drive parity). Is this correct?

Moving along, some people also suggested RAID 6 because it utilizes two parity drives instead of one. The only really significant "con" I could brew up with RAID 5 is with resyncing the array after a drive failure. For example, if I'm running RAID 5 with 4 HDDs, meaning 3 in use and 1 as parity, and one drive dies, I'm down to 3 total. Well, 3 is required for the RAID 5 to run effectively with no data loss. If I add a brand new 4th drive in the mix, it'll of course need to resync. During this time the other 3 HDDs will be pushed pretty heavily in terms of performance, which of course heightens the chance of another failure. This is the one scenario where some people gave RAID 5 a -1 because if one of the 3 HDDs dies, I could have data loss, corruption, or worse - an entirely failed array.

RAID 6 on the other hand seems to utilize two parity drives, which takes a performance hit since you have two parities instead of one, but that's understandable. That being said, what exactly is required to run a RAID 6? Can I run a RAID 6 with 4x2TB with two parity drives? This would diminish my disk space substantially (4TB usable, 4TB parity), but can it be done?

I also understand RAID 5 can be converted to RAID 6. Can this be done with live data on the array? Of course, I'd make a backup, but if this can be done it'd be a solid bonus. That way I COULD (in theory) effectively make a 2x2TB RAID 5 array, then later add two more HDDs bringing it to 4x2TB, and convert the RAID 5 to RAID 6 and be running with two parity instead of one. Eh?

Originally I was very anti RAID with this server and figured I would simply have two hard drives... drive A and drive B. Drive A would be what is actively used, while drive B is a backup drive that drive A rsyncs to every night. The thing is, somebody asked me, "What if you want to add another hard drive for more space?" That's when it hit me that RAID just might be the ticket. After all, I could purchase another 2TB drive, add it accordingly, and I'd have more space available.

(this is also assuming I integrate LVM with this scenario, which is still an area I'm a little unsure of just yet in terms of how to implement it... but that's another topic)

Any insight?

EDIT - so I was doing some digging this evening and RAID 10 kept coming on the radar. Some people even suggested that RAID 10 has eclipsed RAID 5, and that RAID 5 is in some cases obsolete. Of course I began reading about RAID 10 more at this point, which sounds like it's effectively a pair of RAID 0 mirrors. Meaning you have drive A/B that are seen as one mirroring drive C/D that are seen as one. Everything I read suggests that RAID 10 is the better way to go in terms of performance as well as redundancy (for the most part). It sounds like RAID 6 takes a +1 in the redundancy department due to the fact RAID 6 can lose any two drives and be fine, whereas RAID 10 is only resilient against losing two drives IF those two drives aren't on the same block. That said, more reading suggested that the rebuild time for RAID 10 is significantly faster than RAID 5 and RAID 6, thereby giving more credit to RAID 10 due to its lessened HDD degredation during the sync up time.

All of this has me considering RAID 10 instead. The only downsides I'm reading are RAID 10 is a 50% volume loss (since it's effectively a mirror, so if you have 4x1TB you have 2TB usable, not 4), and the fact that if you magically lose the two drives on the same block you would thereby have data loss. That said, RAID 10 is looking more attractive. Any insight on this?

Using RAID is guaranteeing failure when using large drives.  You are better off using a good backup scheme.  See [**_[COLOR="Blue"]here[/COLOR]_**]("http://storagemojo.com/2012/07/23/the-post-raid-era-has-begun/") for more info.

---

### Post by Roasted on 2013-01-18
> **bab1 said:**
> Using RAID is guaranteeing failure when using large drives.  You are better off using a good backup scheme.  See [**_[COLOR="Blue"]here[/COLOR]_**]("http://storagemojo.com/2012/07/23/the-post-raid-era-has-begun/") for more info.

Can you elaborate a bit? Why do you say that?

---

### Post by bab1 on 2013-01-18
> **Roasted said:**
> Can you elaborate a bit? Why do you say that?Read the article (hyperlink) and and come to your own conclusions.

RAID is more for high availably/performance rather than for safety of the data.  I would include LVM in the same catagory as RAID with big drives.  If you have a drive failure you are best off recreating the structure (RAID or LVM) and restoring the data from backups.  Neither of these schemes are failsafe strategies.  

If you want data integrity try ZFS.  Nothing will take the place of a good backup system IMHO.

---

### Post by Roasted on 2013-01-19
> **bab1 said:**
> Read the article (hyperlink) and and come to your own conclusions.

RAID is more for high availably/performance rather than for safety of the data.  I would include LVM in the same catagory as RAID with big drives.  If you have a drive failure you are best off recreating the structure (RAID or LVM) and restoring the data from backups.  Neither of these schemes are failsafe strategies.  

If you want data integrity try ZFS.  Nothing will take the place of a good backup system IMHO.

Yeah, I hear you there. The one advantage to having two drives simply rsync instead of being a live raid is if my main drive goes down I can remount the backup drive as main and everything would work fine. Then just replace the drive and redo the rsync and I'm back. Sure it's not real time but it's pretty hassle free aside from remounting the drive which is cake. I guess I just kept looking at this as a poor solution when other alternatives are readily available, like raid etc., but I guess weighing in the con's can paint a different picture. It just makes me think the fuss isn't worth it for a setup like this. I sure am happy with my software raid mirror in my desktop but I think a mirror is a different beast than a four drive raid 6 instance. 

I'll definitely have to give this more thought. In reference to wanting 4tb of space, even if I went with 4x2tb with no raid v I would have two usable 2tb drives with the other two being nightly syncs. I would just have to adjust my storage with "what goes where" since I'll be dealing with two 2tb drives instead of a single 4tb array. 

Hmmmm....

---

### Post by Roasted on 2013-01-20
New question. I was reading about raid on the wiki page and I came across this section. 

RAID 6 provides protection against data loss during an array rebuild, when a second drive is lost, a bad block read is encountered, or when a human operator accidentally removes and replaces the wrong disk drive when attempting to replace a failed drive.

Is that to say if I have a failed drive and I pull the wrong drive I just killed my array? Or can I get away with putting that drive back in and hope it self corrects once it sees the good drive back in action?

---

### Post by Roasted on 2013-01-21
For what it's worth, I figured out how you can isolate which drive is the bad drive. Once smartmontools is installed, run smartctl -i /dev/sdX against the failed drive. You can find the serial number in the listing, then compare it to the physical HDD and pull accordingly.

New question - while I've been toying with RAID 6 and RAID 10 quite a bit, I doubt I'll be going with them as the reality has set in of just how much it'll cost me to do a 4x2TB RAID setup. Instead, 2x3TB is looking to be far more attractive since I can get two 3TB HDDs for 200 dollars less than four 2TB HDDs (same brand, model, etc., just 2TB vs 3TB). As a result, a RAID 1 mirror is looking more logical. Plus, since 3TB is more than I need anyway, it's still future proofing me quite a bit.

The only last question I have is in regard to a URE landing during a resync. Say I lose a drive, so instead of having A/B, I'm down to A. I pop in a new drive to take B's position and the sync takes over. A URE lands. What happens? Does my array fail right then and there? Do I just end up with a bad block of data? What's the end result?

Disclaimer: I will have backups, so I'm not trying to excuse RAID 1 for a backup solution. I'm just curious if a URE landing during a RAID 1 sync is just as detrimental as having a RAID 5 with no remaining parity and you hit a URE, because I understand in the RAID 5 scenario with no parity and a new drive installed, a URE during the sync process would halt the array. 

Thoughts?

---

