---
title: "How to backup and restore?"
date: 2020-02-13
forum: General Help
---

### Post by jasper1378 on 2020-02-13
Hello all,
I have an old laptop running Ubuntu that is my main computer. A family member gave me a slightly less old used laptops that will be my new main computer. So I'm wondering how to backup the entire system on the old one and then restore it to the new one. I don't want to have to install every piece of software and change every setting again. I have an external HDD if that helps.

Thanks!

---

### Post by oldfred on 2020-02-13
I am a believer in new clean install. Only if you have terribly slow Internet may you not plan on a new install. New install removes all the cruft.
And you can export a list of the applications you have installed to make it easy to reinstall. If you have used a lot of ppa, bit more complicated. But if a newer version of Ubuntu, you should disable ppas anyway as new version may not have them.

Some like full image backups, but they are outdated minutes later.
       If you install your own system you are the system admin
Sysadmins: Everything they told you about backup WAS A LIE
[http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/](http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)
Best practice for Backups - theFu
[https://ubuntuforums.org/showthread.php?t=2368992](https://ubuntuforums.org/showthread.php?t=2368992)& 
[https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986](https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986)
More backup info from 1clue
[https://ubuntuforums.org/showthread.php?t=2377810](https://ubuntuforums.org/showthread.php?t=2377810)
[URL="https://askubuntu.com/questions/569679/whats-a-good-back-up-strategy-for-1-desktop-pc"]https://askubuntu.com/questions/569679/whats-a-good-back-up-strategy-for-1-desktop-pc

      [/URL]
 discussion of alternatives/strategy backups
[https://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224](https://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224)
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[https://help.ubuntu.com/community/CategoryBackupRecovery](https://help.ubuntu.com/community/CategoryBackupRecovery) 
    [URL="https://askubuntu.com/questions/569679/whats-a-good-back-up-strategy-for-1-desktop-pc"]
[/URL]

---

### Post by TheFu on 2020-02-13
Here's a more concrete backup example for a desktop: [https://ubuntuforums.org/showthread.php?t=2436006](https://ubuntuforums.org/showthread.php?t=2436006) with some specific discussions.

---

### Post by ra7411 on 2020-02-13
Fred and Fu both know what they are talking about in here.

Try what Fu recommends and if it works and the install runs well -great, and you've become familiar with the method.
If you run into problems either with a workable install, or an install that seems slow and problematic - reinstall, no big deal. A newer machine will probably reduce the tedium of reinstalling o/s and apps and redoing apps settings.

---

### Post by HermanAB on 2020-02-14
Hmm, in my experience, spending hours and hours to restore an old an tired version of Linux is a bit silly, if you can install the latest and greatest version in half an hour.

The secret is to have a good set of backups of your data and if you have special software, save a copy of "apt list --installed > packages" and a tar ball  of /etc as well, then you have everything you need to redo your personal setup very quickly and easily.

Here is an example of how to make differential backups of your data:
[https://www.aeronetworks.ca/2019/08/differential-backups-made-simple.html](https://www.aeronetworks.ca/2019/08/differential-backups-made-simple.html)

---

### Post by TheFu on 2020-02-14
Herman, how do we re-install the software from the **apt list --installed > packages** easily on a freshly installed box?

---

### Post by HermanAB on 2020-02-15
I have not tried it on Ubuntu - it works with dnf on Fedora - but it would be something like:

$ sudo apt list --installed > packages

and later one day you do a minimalist install to get a basically working system, then follow with:
$ sudo apt install < packages
or

Become root first then:
# cat packages | apt install 

There is always MTOWTDI, but the important point is that packages that are already installed will simply pass and whatever isn't installed yet, will be added to your system.

The way to test it is to make a package list to see what is in it, then copy one or two lines of something innocent to a new file and experiment, by removing and re-installing it till you got the syntax right.  I am not running Ubuntu at the moment, so I would need to make a VM.

Sometimes when doing development, you need to ensure that two machines are 'the same'.  You can do that by getting a list on one machine and installing on the other, then get a new list and redo on the first.

Another trick that I remember from dnf and yum: If the list includes the version numbers of the files, then the system will try to install the same version.  If you delete the version numbers, then it will install the latest version - there should be a way to make a list without the numbers.  The Ubuntu apt should work similarly since it solves the same problem - the trouble is just with getting the command syntax right.

Read this:
[https://askubuntu.com/questions/541781/install-list-of-packages-using-apt-get](https://askubuntu.com/questions/541781/install-list-of-packages-using-apt-get)

That guide suggests this command syntax:
$ sudo apt-get install $(cat pkglist)

TIMTOWTDI and YMMV!

---

### Post by TheFu on 2020-02-15
I used to use the dpkg --get-selections method to save the list, then use --set-selections to reload them for installation.  It worked ok, but included all packages, not just those I'd manually added.

Then came across **apt-mark showmanual** which only lists manually installed packages, which is much less than the total list. Sometimes package dependencies change, so there are sometimes packages in the full list that aren't really needed and I'd rather not have all of them marked as "manually installed."  To restore/install packages on the restored system (last step in recovery process), use:
```
######[ to restore pkgs ]#######
 sudo apt-mark manual $(cat apt-mark.manual)
 sudo apt-get -u dselect-upgrade
```

Guess in the big picture, it doesn’t matter exactly how it is done, provided the method works.
The package list saving command used in my backups is:
```
/usr/bin/apt-mark showmanual > /root/backups/apt-mark.manual
```
System admin scripts are kept in /root/ on my systems for consistency.  The  /root/backups/ holds backup data that might be helpful later:
```
root@hadar:/root/backup# ls
apt-mark.auto    crontab.tf    dpkg.list      pvdisplay.txt
apt-mark.manual  crontab.root  lshw.list      vgdisplay.txt
blkid.txt        df.txt        lvdisplay.txt
```
Everything there is updated nightly, just before the backups are performed.  Sometimes those commands are easier to use than the config data in /etc/, which is always part of backups too.  I use lvm extensively, especially for VM storage.  I should probably add **parted -lm** and **lsblk -o name,size,type,fstype,mountpoint** to those files. Having the exact partition layout can be helpful, though I've never needed it.

Anyway, for me the actual backup of files is just the last part of the backup process.  Getting current information about the system, users, settings, and either deleting or ignoring useless cache stuff happens just before.  After all, there is little use in backing up ~/.Trash/, right?

---

### Post by Artim on 2020-02-15
Wow.  In spite of all the very good advice above, I think that if I simply wanted to make a copy of an existing system on a bootable media like a thumb drive for one-time use, I would simply use [SystemBack]("https://www.linuxbabe.com/ubuntu/install-systemback-ubuntu-18-04-bionic-18-10") and be done in a few minutes.

---

### Post by TheFu on 2020-02-15
> **Artim said:**
> Wow.  In spite of all the very good advice above, I think that if I simply wanted to make a copy of an existing system on a bootable media like a thumb drive for one-time use, I would simply use [SystemBack]("https://www.linuxbabe.com/ubuntu/install-systemback-ubuntu-18-04-bionic-18-10") and be done in a few minutes.

> The author of Systemback stopped its development in 2016  Unsupported software. Not good. Hacks to get it installed **will** break the package dependencies, at some point.

For a while, there was a tool called **aptik** which new users seemed to like. I played with it a few times before deciding it was just to inefficient.  It was using tar.  Tar is a terrible backup tool when compared to almost any of the modern solutions.

For 1-time, I'd use **ddrescue** - boot from a Try Ubuntu flash drive. Can't use it directly on the running system to clone everything due to some special files.  It wouldn't be a few minutes - more likely about 45 for the programs, settings, and data to be copied. Sure, it would be 3 minutes of my time, but the wall clock matters too.
If I needed to clone 20 systems only 1 time, I'd use **fsarchiver**. Again, it has to be booted from alternate media to work. If I needed to clone 20 systems monthly, I'd use **cobbler** + **ansible**.  Happy that isn't me.

But since daily, versioned, backups are not optional here, we have them and use them.  Why not use the solution already available that takes 2-4 minutes daily, automatic, to work?  Why have 5 different methods when 1 covers everything?
It could be as easy as
```
sudo rdiff-backup --exclude-special-files --include /    --exclude '**'    /    /Backups/
```
But that is crazy wasteful.  Basically the same as ddrescue, but it can be run on live, non-DBMS systems with reasonable safety.  The restore would be ```
sudo rdiff-backup -r  /Backups/ /path/on/new/file-system/
```  Using this once is effectively a slightly smart rsync.  Using it 2-150 times, is where the real power of versioned backups shines.

While the steps seem complex, it really isn't. They are just tuned from decades of real-world use.  My goal is to have everything needed to make a fresh system, on new hardware, within 1 hour, with 90-180 daily, automatic, versioned, network, backups. The backup process needs to be efficient, and downtime limited if any is needed at all.  Not wasting storage is important too.  Why use a solution where 3 backups requires 3x the storage when we can have 180 versions for 1.4x the storage?

Just yesterday a user deleted 5 important files from a project directory. Claimed it was an accident.  Their entire team was stuck, not able to work.  3 minute later and the files from 3:32am were back, everyone working again.  Sometimes I'm the guy who deleted the wrong files too, so there's no grief given out for the first 5 mistakes yearly.

Everyone has different needs. Usually, it takes a huge data loss event for people to get backup religion.  That's what happened to me.  Then there was an attack and the last backup was corrupted too. That's when I decided that versioned backups were needed. Then something else happened, so I tweaked the backups a little ... and something else .... and something else .... and something else.  

Why not learn from someone else's failures?  Getting an optimized solution from the start is much easier.

---

### Post by HermanAB on 2020-02-15
"Just yesterday a user deleted 5 important files from a project directory. Claimed it was an accident. Their entire team was stuck, not able to work. 3 minute later and the files from 3:32am were back, everyone working again. Sometimes I'm the guy who deleted the wrong files too, so there's no grief given out for the first 5 mistakes yearly."  -- Maybe you should use Subversion.

---

### Post by TheFu on 2020-02-15
> **HermanAB said:**
> "Just yesterday a user deleted 5 important files from a project directory. Claimed it was an accident. Their entire team was stuck, not able to work. 3 minute later and the files from 3:32am were back, everyone working again. Sometimes I'm the guy who deleted the wrong files too, so there's no grief given out for the first 5 mistakes yearly."  -- Maybe you should use Subversion.

Small video files.  

We use a local git repo for software stuff, but avoid putting binaries there.

---

