---
title: "Is there a free backup program similar to aptik?"
date: 2022-11-23
forum: General Help
---

### Post by jakemaverick911 on 2022-11-23
I really need Aptik now....failing ssd drive on my Xubuntu installation. Backups are corrupted/ won't restore to new drive.....so was quite disapointed today to find Aptik is no longer free...and I really am skint. So I'm hoping somebody would know the solution to my problem?

Thanks for reading!

---

### Post by tea for one on 2022-11-23
If your hardware is failing, the first priority is to backup your personal data.
Xubuntu can be easily installed on a new disk, but your data is only under your control.

---

### Post by jakemaverick911 on 2022-11-23
> **tea for one said:**
> If your hardware is failing, the first priority is to backup your personal data.
Xubuntu can be easily installed on a new disk, but your data is only under your control.

that's exactly what i am trying to do, but without aptik....I'm at a loss on xubuntu :-(

---

### Post by tea for one on 2022-11-23
You do not need Aptik to copy your personal data.
How have you backed up your user folder previously?

---

### Post by jakemaverick911 on 2022-11-23
previously? i just backed up whole drive using Acronis...ideally i want to backup my internet/ browser history, all the apps i have installed, few downloads and a few personal docs...i'm probably going to have lose my apps and partial d/ls, but just copying home directory will get everything else?

---

### Post by tea for one on 2022-11-23
If you want to make an image of the OS (including applications), then investigate Clonezilla
[https://clonezilla.org/](https://clonezilla.org/)

First, just copy your personal date to an external device before your SSD falls over.
I would not worry about applications because it is easy to re-install them.

---

### Post by jakemaverick911 on 2022-11-23
as i say can't just clone the whole drive as it's corrupted due to ssd failure :-( Acronis true disk is best i have found....but won't restore the corrupted/ damaged files. Aptik would be perfect for what i need to do is all....still hoping there is something that will do what that does but for free....

---

### Post by tea for one on 2022-11-23
I feel that we are going around in circles at the moment.
You do not have a recent backup of personal data and you are unable to do this task?

---

### Post by jakemaverick911 on 2022-11-23
break in couple months back, all my kit stolen including backup drives....managed to get a couple of second hand pcs, both with failing ssd drives, uneconomic to return....so i lost pretty much the last 30 odd years anyway, but last couple of months of rebuilding...wd be nice to backup, fresh jellfish install and back to where i was via usb backup seems like best option atm. got rusty these last few years...with regular full system backups, no hardware failures....i've forgotten how to do a lot of stuff in linux :-(

---

### Post by oldfred on 2022-11-23
I use rsync of /home & my data which is in another partition. But to multiple drives, flash drives, and some critical data to DVDs with k3b.
I export list of installed apps, but have most in a script I use to reinstall.
Then I just do a new install, restore data & apply list of apps to reinstall.
New install with partitions created in advance & loading ISO into RAM to NVMe drive took less than 10 min. 
Rsync of data was fast. Slowest was downloading apps as I have a long list.

Simple manual rsync & rdiff theFu
[https://ubuntuforums.org/showthread.php?t=2471454&p=14078689#post14078689](https://ubuntuforums.org/showthread.php?t=2471454&p=14078689#post14078689)
Restore process TheFu
[https://ubuntuforums.org/showthread.php?t=2474107&p=14091927#post14091927](https://ubuntuforums.org/showthread.php?t=2474107&p=14091927#post14091927)
What to backup TheFu
[https://ubuntuforums.org/showthread.php?t=2456011](https://ubuntuforums.org/showthread.php?t=2456011)
[https://ubuntuforums.org/showthread.php?t=2462752&p=14040507#post14040507](https://ubuntuforums.org/showthread.php?t=2462752&p=14040507#post14040507)
Best practice for Backups - theFu
[https://ubuntuforums.org/showthread.php?t=2436006](https://ubuntuforums.org/showthread.php?t=2436006) &
[https://ubuntuforums.org/showthread.php?t=2368992](https://ubuntuforums.org/showthread.php?t=2368992) &

---

### Post by jakemaverick911 on 2022-11-24
thanks oldfred! that was really starting to solve it for me....unfortunately the failing ssd completely went part way through, so i got some but not everything....thanks for that though! i know for next time!

---

### Post by TheFu on 2022-11-24
> **jakemaverick911 said:**
> thanks oldfred! that was really starting to solve it for me....unfortunately the failing ssd completely went part way through, so i got some but not everything....thanks for that though! i know for next time!

You can boot into a "Try Xubuntu" environment and if the storage with the files is still available, pull that off.  I see oldfred has links to lots of my posts about backups.
Images are for when we are afraid and don't understand where stuff goes.  

Once you know that we don't need to backup the OS or programs, just OS settings, personal settings and personal data, there is little reason to backup much else.  I happen to grab a list of manually installed packages too.  Then review my "what to restore" and the order of the restored files.  Backups take 1-10 minutes a day, so there's little reason NOT to do them.  For a home user, backing up weekly is probably sufficient if you aren't changing much daily.  If you are making lots of files and updates daily, why wouldn't you just have daily versioned backups automatic?  Some of my systems take less than 1 minute to backup. These backups are extremely efficient with the latest version looking like a mirror. To restore 1 file or an entire directory system, cp or rsync can be used to get the latest version.  Of course, you can use rdiff-backup with a time reference to get older backups.  I keep at least 90 days for all systems, but over 180 days for some high risk systems.  The amount of storage needed for each system to have 90 days of daily versioned backups is typically 30% more than the size of the backup source files.  Say, I'm backing up 10G from my HOME. 90days of backups would need 13G.  Why wouldn't you do that?  Of course, I keep all media files elsewhere, not in $HOME, so those don't get part of the 10G. We're talking just settings, documents, presentations and active work for me in my HOME. YMMV.  BTW, I have over 40TB of storage ... but all my versioned backups fit into less than 2TB total.  That's a $50 external USB3 HDD.

Restores always begin with a fresh OS install, then I restore any HOME directories and selectively restore system-wide settings from /etc/.  We can't blindly restore everything for a number of reasons, but having everything in the /etc/ directory means we can see what the old answers were as needed later.  I usually add a comment tag to any files I change in those directories, so I can easily find them at restore time.  If my restore process takes over 45 minutes, then I've failed.  that should result in a system with all the data, all the settings and all the programs working that were on the other box.  It is my system again in that time.  Plus, my method lets completely new and different hardware be used to restore into. All that matters is that the files appear to be in the same directory with the same owners as before.  Most of the time on desktops, there aren't any issues.  With some servers, there can be complexities as old gids and uids for daemon processes don't align. This can make data that was used previous inaccessible once all the packages are installed from the list we make before each backup.  If you know about this, it isn't a big deal to look up the differences between the old and new passwd and group files and make them consistent in the new install.

Hope this is helpful for someone.

rdiff-backup doesn't have a GUI. If you need a GUI, perhaps something like Back-in-Time would be a better option?  It works in a different way than rdiff-backup. I use it for my Mom's computer backups for a few years. After setup, it is 100% automatic in the default mode.  It takes versioned backups every hour, so very little data will change from hour to hour.  The versions are stored as hardlinked versions, which is pretty efficient when files don't change.  You can look up "hardlink" in wikipedia for an explanation.  Hardlinks are cool, provided you know the limitations.  Anyway, after the hourly backups are created, as time passes they are selectively deleted.  I don't remember the exact way, but here's a guess:
* 48 hourly backups for 2 days from "now"
* 1 daily backup for 2 weeks
* 1 weekly backup for the current month (or perhaps last 6 weeks)
* 1 monthly backup for each year (the first backup for any month is retained)

In short, the longer ago it the backup is, the fewer versions there are from which to pick.
It is possible to customize the schedule and if it were my system, I'd have done more like 
* 48 hourly backups for 2 days from "now"
* 1 daily backup for 60 days
* 1 weekly backup 60 days until 52 weeks ago (about 44 weekly backups)
* 1 monthly backup any time over 52 week ago up to the space limit, which should be in the software configuration, not just "out of space" errors.

Due to file corruption, I've had to selectively restore a file form 37 days ago.  Of course, I've had OS drive failures. For those, the latest backup was used to restore. Versioned backups have 1001 uses.  With images, we need 100% of the storage for the source for each version. I don't have that sort of money, but still need the protection.

---

### Post by buellboy9 on 2023-03-09
I have the .deb for the last "free" version of aptik.  Command line only, doesn't support snap or flatpak.  I use it when upgrading from one version of Ubuntu to the next to save me the time of installing each application individually (except for those programs I have to manually install).  It still works.  For backups, though, I use Clonezilla for the ENTIRE system, and daily incrementals with Deja Dup.

---

