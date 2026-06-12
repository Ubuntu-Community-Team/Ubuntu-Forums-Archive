---
title: "Issue with copying files to Windows from Ubuntu 18.10"
date: 2019-01-20
forum: General Help
---

### Post by tsynkzzz on 2019-01-20
Hi, I have been having this issue on Ubuntu 18.10 and I cannot find a solution to fix it. Anyway, I want to move some files over to my Windows partition of my HDD, I was able to do this at some point (before I was using Ubuntu 18.04 LTS) without having the read only issue. I don't have Windows in hibernation, it's fully shutdown and I still cannot move files over to that partition of my HDD. I want to get it out of this copy protection so that I can have space on Ubuntu, I don't have a large partition for Ubuntu and moving files to Windows was a huge help. Please and thanks.  
[ATTACH=CONFIG]282250[/ATTACH]

---

### Post by TheFu on 2019-01-21
There are 2 possible causes for a read-only NTFS partition.
a) the disk is failing and Linux is forcing read-only mode to prevent even more data loss.
b) Windows has left the file system **opened** using quick-start/fast-start or hibernation or sleep settings. If you google "sharing NTFS with Linux" the names that MSFT uses for those things and how to disable them should come up.

You can see the SMART data for the HDD using smartctl, assuming the BIOS on the machine has it enabled.  Inside there are 30+ data items which give an overview of how the drive is doing.  About 78% of the time, SMART data will show a failing disk before it actually fails.  But, 22% of the time, there isn't any warning and data loss happens.

Regardless, how good are your backups for all the data you don't want to lose?  Storage is always going to fail. It never fails when it is convenient.  I've had storage fail after 5 days, 1 month, 13 months, 3, 5, 10 yrs.  I have some storage that is 13 yrs old and doesn't show **any** failure predictors, so I keep using it for minor, unimportant data transfers.  I have backup religion for all important data. Got burned. Learned my lesson.

---

### Post by HermanAB on 2019-01-21
Hmm, +100 for the backup lesson above.

I would not save Linux data on a Windows partition, since the chances of it breaking the system is too high for my risk level.  I've been there and witnessed the mutilated bits - it is really scary...  

One can get enormous SD cards and USB sticks nowadays, so I'd suggest you rather get a big fat new widget (256 or 512 GB), format it with ext4 and leave it in the machine permanently.

---

### Post by tsynkzzz on 2019-01-21
That would be great and everything, HermanAB, but, I don't have the funds to buy what you are telling me. 

TheFu, I have done tests before on my disk and they all come up as okay. I also keep an eye on it to make sure it's okay. Perhaps it's just Windows leaving things opened. I boot to Windows every now and then to keep check on it, loads up just fine, everything is still there, the only issue that I have is that the time is off or Windows Update reenables itself other than that, it runs like it always did. I have more concern with my mom's laptop than my own, since her laptop is older than mine. I also keep an ear on my HDD, listening for those failing clicks, which that hasn't happened. I keep an eye on stuff like that. I threw all of my pictures, documents, music, etc. onto my Google Drive since I couldn't get it over to Windows.

---

### Post by oldos2er on 2019-01-21
How are you mounting this partition? I'm assuming it's NTFS?

---

### Post by TheFu on 2019-01-21
> **tsynkzzz said:**
>  the only issue that I have is that the time is off or Windows Update reenables itself other than that, it runs like it always did.

This is known to have happened.  Ensure that Windows isn't leaving the file system marked as "open", or Linux won't mount it read-write.

Noisy disks is an issue, but I haven't heard a failing disk in a long time. Gotta watch the SMART data and monitor how fast the 5 (or so) bad numbers change from week to week.

BTW, you know that google closes accounts without warning all-the-time, right?
Sometimes they delete the account too.  Google: *google account disabled*

---

### Post by Mark Phelps on 2019-01-21
Windows 10 has something known as Fast Startup -- which is a new form of hybrid sleep/hibernation -- which is enabled BY DEFAULT in Win10.

And, even though you can manually disable it, it's not unusual for a Windows Update to then re-enable it without telling you.

So, you should boot back into Windows and confirm it is still disabled.

---

### Post by tsynkzzz on 2019-02-15
This issue seems to be fixed. I was having another issue and instead of coming here, I went to #Ubuntu on Freenode and asked for help there, an user walked me through to fix another issue I was having and ever since then, I have been able to write to my Windows partition now, it's no longer read only. I also have Fast Startup disabled, I did that first thing before installing Ubuntu.

---

### Post by oldos2er on 2019-02-15
Would you please mark this thread 'Solved' under Thread Tools at the top of the page? It helps others who may be having the same problem.

---

### Post by tsynkzzz on 2019-02-15
Sure will.

---

