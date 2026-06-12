---
title: "Failure Testing of Raid-1 Array Fails"
date: 2007-08-15
forum: General Help
---

### Post by greg3000 on 2007-08-15
Hello Linux World :)  I never expected to say that, but greetings from a 2 day old ubuntu 7.04 linux server user here. Thanks for the great source of community information.  

My question is regarding Raid 1 setup and failure testing.  For the setup I used the following link: [http://users.piuha.net/martti/comp/ubuntu/raid.html](http://users.piuha.net/martti/comp/ubuntu/raid.html)

To summarize I have two 500gb drives forming a raid 1 array consisting of 3 partitions:
MD0 is a 10gb / (boot)
MD1 is a 10gb swap
MD2 is a 480gb /home

I've got this system set to boot into ubuntu desktop and I'm currently testing it for failure scenarios. 

When I unplug either my main or secondary drive of this raid 1 array, tty fails to boot, so I get a busybox shell prompt and 'cat /proc/mdstat' tells me that md0, md1, and md2 are inactive. I understand that normal operations should continue with a failed drive. Could I ask the community to help me through this?  I will quickly reply with any suggested command responses.

Thanks in advance
Greg

p.s. I have a similar message posted as a reply to an older raid thread here: [http://ubuntuforums.org/showthread.php?p=3194700#post3194700](http://ubuntuforums.org/showthread.php?p=3194700#post3194700)

Also, on a side note, could anyone comment on their experience or workarounds for using desktop drives rather than raid/enterprise drives with linux and raid?  

To quote a western digital article:
> When an error is found on a desktop edition hard drive, the drive will enter into a deep recovery cycle to attempt to repair the error, recover the data from the problematic area, and then reallocate a dedicated area to replace the problematic area. This process can take up to 2 minutes depending on the severity of the issue. Most RAID controllers allow a very short amount of time for a hard drive to recover from an error. If a hard drive takes too long to complete this process, the drive will be dropped from the RAID array. Most RAID controllers allow from 7 to 15 seconds for error recovery before dropping a hard drive from an array. Western Digital does not recommend installing desktop edition hard drives in an enterprise environment (on a RAID controller).

---

