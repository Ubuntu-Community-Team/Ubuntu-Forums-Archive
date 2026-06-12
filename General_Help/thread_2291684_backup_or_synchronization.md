---
title: "backup or synchronization ?"
date: 2015-08-22
forum: General Help
---

### Post by alain.roger on 2015-08-22
Hi,

i'm facing a dilema.
I'm from MS world where we used backup tool to protect our computers doing a full backup of computer HDD for example.
Some computers had a synchronization tool that allow user to have their data available on both: laptop and desktop computers.

i have to say i would need something both solution.
In fact, as i use KUbuntu 15.04 now on my main desktop computeri would like to backup my personal data (emails, documents,...), local webserver settings (apache, php, /var/www), 1 virtualbox computer, etc.
To avoid issue i would like also to have a crash/recovery system in case my computer crash and i do not want to reinstall the full kubuntu, settings, updates, etc..

To make it more interesting, my NAS has a limited free space 500GB to 1TB.

So i was wondering what would be the best solution you would advise me to cover all my needs.

thx.

---

### Post by TheFu on 2015-08-22
Not single tool/solution can over all your needs without some downsides. Sometimes that is just added complexity, other times it required downtime for the entire system (which I find completely unacceptable).

Backups need to follow a few best practices:
[LIST]
[*]    Stable / Works Every Time
[*]    Automatic
[*]    Different Storage Media
[*]    Versioned
[*]    Fast
[*]    Efficient
[*]    Secure
[*]    Offsite / Remote
[*]    Restore Tested
[/LIST]

Backups that are not versioned only get me 80% of what I required.  If the system gets hacked, being able to see the differences over time is absolutely critical. That applies to the OS, programs, and small data files.  Large media files, for example, don't pose much risk and don't change much. Having versioned backups of those will just waste storage. I use a mirror-only for large media files, but everything else is versioned, daily, with fast, efficient, remote, automatic backups.

I tried to backup VMs from the hostOS and those took longer and longer and longer until they started failing with non-trivial VM storage.  After a few yrs of fighting it, I started doing VM backups using the normal backup tools from inside the VM. Backups are 1-4 min again for each VM. Last week, I posted some backup job stats in these forums.

These methods don't work for Windows or it could be that my lack of knowledge and understanding of how Windows works limits the possible answers on that platform.  I always felt that an image was needed for Windows. 

That isn't needed on Linux. If the files appear to be where they need to be in the directory structure, with the correct owner, group, and permissions, that is the only important aspect. NOTHING needs to be in a specific disk location, except grub for booting. We can completely swap the storage around - move files from one partition to another and as long as the location in the file hierarchy is correct - it will be fine. I've used symbolic links to move /usr/local to different, networked, storage and the OS didn't care at all.  Flexibility is the cornerstone of Unix.

If uptime isn't an issue for you, a quarterly image and daily backups could be the hybrid solution that works best.  I don't know. I don't do any image-based backups for Linux, since I can reload the base OS in 15 min, then restore from whatever backup version I need in another 15 min and have the system running in 45 min.  I keep between 30 days and 120 days of versioned backups here for the different systems. Some are just processing engines, so 80MB (yes, that is correct) is all the storage needed for 120 days.  Others need 22G for 60 days of backups - it depends on the data that changes. Because I don't backup the OS or any applications installed through the package manager, about 4G per instance is saved.  Settings don't take much storage at all.

Anyway - hope this helps.

---

