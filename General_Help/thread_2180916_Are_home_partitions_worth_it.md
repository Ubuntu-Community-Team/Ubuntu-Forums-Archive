---
title: "Are /home partitions worth it?"
date: 2013-10-15
forum: General Help
---

### Post by maerlyn-broadbent on 2013-10-15
I'm new to the Linux world and whilst I've been learning the ropes, I've read some conflicting opinions regarding the creation of separate partitions for /home and other directories during OS install.


Some say that having these directories in separate partitions allows you to reinstall without losing your data. Others say that it adds pointless complexity to the system and that some unwanted files from old installations linger after new installs.


What do you people think about this?


If storing certain directories on separate partitions is a good idea, why is this the case? Would it be better to use completely different drives?


Is this different from distro to distro?


Thanks in advance.

---

### Post by drmrgd on 2013-10-15
I have never heard anyone say that installing /home on the same partition as root is a bad idea.  That's kind of odd as it's far more common to install it to a different partition.  Really, that it's very easy to just back up /home and reinstall the OS is alone reason enough to go that way.  There have been a couple instances where I've needed to reinstall the OS or something similar, and beyond a few config files in /etc, just backing up /home was enough to have me back up and running in no time.

---

### Post by slickymaster on 2013-10-15
With a separate /home you can easily install a newer Ubuntu version, or any Linux distro for that matter, without losing most of your custom settings, configurations, downloads, etc, since such a step usually involves wiping out the existing system/boot partitions. You simply choose to preserve your /home in the partitioner during install, and you're set.
It makes data retrieval easier in the case of a crash. If you suffer from a failed release upgrade for example, the /home partition will be untouched and you can easily recover by installing or re-commencing the upgrade without being too concerned about your data. It also makes resizing/migrating to a larger home partition easier, if you ever need more space.

---

### Post by CatKiller on 2013-10-15
As others have already pointed out, a separate /home is handy if you can be bothered. If you can't be bothered, it's not really a big deal. There's no real conflict here.

---

### Post by maerlyn-broadbent on 2013-10-15
So it's pretty much just done to preserve data when everything crashes and for new OS installs? If I back up all of my data to a cloud service or a different drive would You say that having /home on a different partition is pointless? If instead of a partition on the same drive, I use a completely different drive, do you think I'd see any speed increases by not having to wait for one drive to access all of the data?

When I reinstall an OS I usually prefer to remove everything and start fresh. I'm in the middle writing a bunch of scripts to automatically do all the config and software removal/install that I need so If I have my data backed up somewhere else it seems that I don't need a separate /home partition.

Are there any other directories that are commonly placed on separate partitions?

---

### Post by slickymaster on 2013-10-15
It won't speed up file access much, unless the partition the /home is on is on a faster device like an SSD hard drive. It does allow for separate buffering though, so I guess there would be a minor speed increase from that.

---

### Post by PJs Ronin on 2013-10-15
I don't have a great deal in my /home... just some conky stuff and some fonts. I, for one, don't put data anywhere near my /home or any of my linux/windows partitions. In fact, all of my data is on a separate hard drive well away from where I can stuff things up. So for me, /home doesn't really amount to a hill of beans.

---

### Post by Morbius1 on 2013-10-15
The following is based solely on my own experiences over the years.

I'm in the "Others say that it adds pointless complexity to the system and that some unwanted files from old installations linger after new installs" camp with emphasis on the second part of that statement rather than the added complexity part. What I do is create 3 partitions: /, swap. and /Data.

In the /Data partition I create subfolders of the major subfolders of the home folder ( Music, Documents, etc... ) and then "bind" them back to the home folder. You can also use symlinks if you don't have a home network and use Samba.

As far as creating even more partitions for the other subdirectories off root the only thing that will do is guarantee that you will eventually be back here asking how to resize these partitions because of system errors saying you are running out of space.

Now the way I use Ubuntu may be part of the reason I follow this approach and it may differ from what you want from your OS. Ubuntu now "releases" a new edition every 6 months but they are for me a waste of my time since they are just betas which are only maintained for 9 months. So I install only LTS releases which occur every 2 years. If I had a separate home partition containing all sorts of settings and configurations for one LTS it likely won't work for the next LTS.

I suppose if I keep upgrading my install every 6 months then the changes each time wouldn't be that great but now Linux has become a hobby and the care and feeding of that OS is the main goal. I don't use Linux that way. I use Linux as a platform to get something else done.

---

### Post by maerlyn-broadbent on 2013-10-15
Thanks for your replies everyone.

I also read that having a separate /home partition mounted in a specific way can enhance security by disallowing the execution of s-bit programs, although I don't know exactly what s-bit programs are.

> Now the way I use Ubuntu may be part of the reason I follow this approach and it may differ from what you want from your OS. Ubuntu now "releases" a new edition every 6 months but they are for me a waste of my time since they are just betas which are only maintained for 9 months. So I install only LTS releases which occur every 2 years. If I had a separate home partition containing all sorts of settings and configurations for one LTS it likely won't work for the next LTS.
This is another thing I've been thinking about. I need my computer to be stable so I'm leaning more towards using LTS releases or maybe even switching to Debain. I haven't decided yet, I'll see what happens when 14.04 comes along.

---

### Post by Bucky Ball on 2013-10-15
Try this. If you decide you want to install MORE than one OS, that means you are going to need a heap of /home partitions. Or, a /home directory in each. Waste of time for personal data. Duplication and other issues. 

I personally have a data partition for all installs. In there, I have the regular directories like /Documents, /Music, etc. Everything you would find in a regular Ubuntu default /home partition or directory.

Now, when I install an OS, I let /home install as a directory inside /, BUT I then delete the directories inside the /home directory (eg /Documents, /Videos, etc.) and create symlinks to the folders which already exist on my /data partition.

All information can be used and accessed by any install, anytime, and all installs can be totally wiped and reinstalled without ever going anywhere near the actual data partition. If I make a change to something while running in one install (and this happens) when I boot to ANY of the other installs it accessing the SAME data and therefore the same changes. 

Easy? Hope you understand where I'm coming from. ;)

But to answer the original question: yes, I always recommend /home partition for a regular install, even when backed up to cloud or anywhere else. I'm old school and the rule was 'grandfather, father, son'. You have the original, a backup and a backup of that. And if I was going by the same book, it is a no-brainer that the absolute safest is to have one backup on an external drive that lives off the premises for the rest of the week, one backup that lives on a separate drive, not just partition, and the original.

But most people generally don't go to these lengths in a domestic setup now. You would generally have two backups if you were running a business (at least two and if you were running a tight one, that is). ;)

There are many aspects to this, and many no longer relevant (due to advances in technology and the fact we are talking LInux, not Win). In the olden days (!) drive speed mattered and think about it: if you have the OS in a single partition just big enough to hold it the drive arm doesn't need to cover the whole disk (or better still, stick the OS on a 20Gb disk). Faster. No-brainer. Consequently, OS on one drive, data on another, two lasers is better than one, faster. No brainer. These issues aren't quite as pressing now. But if you were working in high-end audio/visual you would generally not do it any other way still. OS on one drive, record to another, data on another. Rule of thumb.

---

### Post by Bucky Ball on 2013-10-15
Try this. If you decide you want to install MORE than one OS, that means you are going to need a heap of /home partitions. Or, a /home directory in each. Waste of time for personal data. Duplication and other issues. 

I personally have a data partition for all installs. In there, I have the regular directories like /Documents, /Music, etc. Everything you would find in a regular Ubuntu default /home partition or directory.

Now, when I install an OS, I let /home install as a directory inside /, BUT I then delete the directories inside the /home directory (eg /Documents, /Videos, etc.) and create symlinks to the folders which already exist on my /data partition.

All information can be used and accessed by any install, anytime, and all installs can be totally wiped and reinstalled without ever going anywhere near the actual data partition. Easy? Hope you understand where I'm coming from. ;)

---

### Post by Morbius1 on 2013-10-15
The only s-bit thing I'm familiar with is the "sticky bit" ( or maybe the setgid bit ) and I'm not sure I get the connection - one way or the other - to a separate home partition.

As for using Debian you have another dilemma - which Debian? Debian has 3 repositories:

Unstable - You have become an unpaid tester for Debian. Thank you. Your efforts are appreciated by all users of Debian like Ubuntu.
Testing - Notice it's a gerund: Testing - not Tested. You are in hobby mode big time with that one.
Stable - The good news is that it's been tested to death. The bad news is that stable releases follow US presidential cycles so don't expect new releases often.

---

### Post by maerlyn-broadbent on 2013-10-15
Thanks Bucky Ball.

I do understand where you are coming from and you make a lot of valid points.

I've been convinced; when I reinstall I'll create a /home partition and beef up my back up strategy. Thanks your your help everyone.

---

### Post by maerlyn-broadbent on 2013-10-15
> The only s-bit thing I'm familiar with is the "sticky bit" ( or maybe the setgid bit ) and I'm not sure I get the connection - one way or the other - to a separate home partition.
I don't understand this either. I was just told that this was the case by a user on a different forum; I'll have to do more research.

> As for using Debian you have another dilemma - which Debian? Debian has 3 repositories
If I'm not mistaken then Ubuntu itself is based on Debian Testing as is Linux Mint Debian Edition. Debian Testing seems to be as stable if not more stable than a lot of other operating systems.

The main reason I was considering the move to Debian is because I like the idea of being on the source distro without a lot of extra stuff added that I don't need. The outdated repositories are definitely a drawback but if I get more reliability out of my desktop then it may be worth it. I'm also not a fan of where Unity is going with all of the online search results being added into regular searches. I'm using Cinnamon with Ubuntu at the moment which is working really but I'd prefer a proper Cinabuntu variant since there are a few left over programs from the base install which I'm not sure how to remove - I currently have two different settings programs.

---

### Post by mastablasta on 2013-10-15
> **Bucky Ball said:**
>  

I personally have a data partition for all installs. In there, I have the regular directories like /Documents, /Music, etc. Everything you would find in a regular Ubuntu default /home partition or directory.

Now, when I install an OS, I let /home install as a directory inside /, BUT I then delete the directories inside the /home directory (eg /Documents, /Videos, etc.) and create symlinks to the folders which already exist on my /data partition.

All information can be used and accessed by any install, anytime, and all installs can be totally wiped and reinstalled without ever going anywhere near the actual data partition. If I make a change to something while running in one install (and this happens) when I boot to ANY of the other installs it accessing the SAME data and therefore the same changes. 



perhaps it should be one of install options. people usually have sommething similar in windows. at least i always made a system drive and data partition so they are separated. i upgraded form win 3.11 to win 95 to win 98 to winxp and all was good. data was there, ok there werre new settings and stuff but not that new.

---

### Post by Morbius1 on 2013-10-15
> If I'm not mistaken then Ubuntu itself is based on Debian Testing as is  Linux Mint Debian Edition. Debian Testing seems to be as stable if not  more stable than a lot of other operating systems.
Ubuntu is a fork of Debian which is why not all Debian packages will work with Ubuntu.

Many different distros that use Debian have to come to terms with how Debian operates. Some walk towards the light and point to Debian Testing directly in the belief that eventually things will work out. Ubuntu starts with Debian and then modifies it and adds packages that will not work in Debian and vice versa.

Mint goes even further. It modifies Ubuntu and even sets limits on what can be updated. By default there are no kernel updates in Mint. The user has the power to override that default of course.

---

### Post by Bucky Ball on 2013-10-15
> **mastablasta said:**
> perhaps it should be one of install options.

Interesting, and interestingly, it kind of is. But you need to choose 'Something Else' when you get to the partitioning section of the install. You will find /home in there as a default mount point for a new partition, along with other things like /boot, etc. So, while not exactly obvious, it is there ... sort of! ;)

Also, point to remember: If you are installing second OS, if you choose 'Something Else' and set an existing /home partition to 'use' but NOT ticked to format, it will automatically use that as the /home partition and NOT create a new /home directory inside /. For the record. This, though, will set up 'User A' (which is from the first install) in one directory (/User A) and /User B, BOTH inside the /home directory. Okay, but not ideal for sharing data (which is why the symlink idea is better in the multi-boot situation.

---

### Post by CaptainMark on 2013-10-16
> **Morbius1 said:**
> If I had a separate home partition containing all sorts of settings and configurations for one LTS it likely won't work for the next LTS.
I agree with most things you say but this is absolutely absurd, I have had the same /home partition since 2008 on my main desktop it has been re-used for many Ubuntu versions and many other distros as well and I have never had an issue with configuration files not working with updated software versions and I have never heard of someone who has. Configuration files are always backwards compatible, the only way this would cause a problem is if you are downgrading a distro to an older one because software makers rarely consider forwards-compatibility

---

### Post by Morbius1 on 2013-10-16
This is how I use the /Data partition to bind subfolders in that partition to my home directory:

[U][I]I recreate the major home subdirectories in /Data:
[/I][/U]/Data/Documents
/Data/Downloads
etc...

_*I create my own upstart job at /etc/init/homebind.conf to bind those subdirectories to their corresponding subdirectories in the home folder:*_
```
# Remount home directories from /Data partition using bind
#
description "Bind Data Partition Subdirectories to My Home Directory"

start on stopped mountall

script
mount --bind /Data/Documents /home/morbius/Documents
mount --bind /Data/Downloads /home/morbius/Downloads
end script
```
[COLOR=#0000cd]"For the love of all that's holy why don't you use symlinks - it's way simpler"[/COLOR]

You are correct disembodied voice it is way simpler but I use Samba and Samba is designed not to follow symlinks. You can override that default but Samba doesn't recommend it because of a security bug. Samba doesn't have a problem with a bind.

[COLOR=#0000cd]"An upstart job seems like overkill why not add the appropriate lines in rc.local or even fstab."[/COLOR]

Once upon a time the boot process was an elegantly simple thing ( comparatively speaking ) but all the folks who knew how all that worked are either retired now, moved on to write iOS apps for Fortune 500 companies, or dead. I have found timing issues ( tries to execute the bind before the partition holding the data is mounted ) when using rc.local or fstab [COLOR=#0000cd]*which may very well be unique to my system*[/COLOR] but is the reason I now use upstart. The "start on stopped mountall" entry in the upstart job instructs the system to execute the binds only after everything else has been mounted.

---

### Post by Bucky Ball on 2013-10-16
Samba IS a security bug. ;)

---

### Post by The Cog on 2013-10-16
> **CaptainMark said:**
> > If I had a separate home partition containing all sorts of settings and configurations for one LTS it likely won't work for the next LTS.I agree with most things you say but this is absolutely absurd, I have had the same /home partition since 2008 on my main desktop it has been re-used for many Ubuntu versions and many other distros as well and I have never had an issue with configuration files not working with updated software versions and I have never heard of someone who has. Configuration files are always backwards compatible, the only way this would cause a problem is if you are downgrading a distro to an older one because software makers rarely consider forwards-compatibility
If you wait around long enough, you will find this is not always true. I have seen problems where the GUI won't even start and it crashes back to the login prompt because of gnome settings preserved from one version to the next (two or three times, I think). Things like this seem to happen less than they used to, but it is certainly not "absolutely absurd" to think that they can. I have in the past had to rename my user directory, create a new one and just move my data and settings for chosen apps over, abandoning lots of old settings. Gnome seems to be the worst offender I have found for these upgrade problems.

That said, I generally keep my /home partition between OS upgrades, and generally don't see any issues. Issues are rare enough that I prefer to find and delete the offending config files/folders than to reconfigure all the settings in every app. And I do generally upgrade every 6 months.

---

### Post by CaptainMark on 2013-10-17
Perhaps I should have been clearer, the part I thought of as absurd was the claim that upgrading from one [modern] LTS to another is more likely to break your system than upgrading from a normal distribution, really if it's going to happen it could happen at any upgrade. But still you're the first person I've ever heard complain that a /home partitioned upgrade didn't work for _this_ reason, you see it all the time with in place upgrades or when something else goes wrong.

---

### Post by James Wilde on 2013-10-17
It's a religious thing.  I worship at the separate /home partition church.  On Solaris, FreeBSD, OpenBSD or any linux distro I'll usually create a separate home partition the first time up.  Sure you can back up a home directory before reinstalling, and reload it afterwards, but you're saved two operations if you reinstall or upgrade.

Sometimes I lapse, especially with virtual machines, which are more for experimental purposes anyway.

---

### Post by CaptainMark on 2013-10-17
I would definitely say it becomes more useful to have a /home partition to bigger your home folder gets, with a small sub 10gb home folder its not too much hassle to back up and restore it across distributions or installs, but if you're having to copy 10,50,100+ GB to reinstall a system then it's a long wait to backup and restore it all

---

