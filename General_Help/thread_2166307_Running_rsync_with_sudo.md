---
title: "Running rsync with sudo ?"
date: 2013-08-08
forum: General Help
---

### Post by cogset on 2013-08-08
I've been doing incremental backups of my system with rsync for months now,only recently it dawned on me that by backing up the running system as normal user,I was actually leaving out a number of files with **-rw-r-----** permissions,like say the ufw configuration files among many others
```
rsync: send_files failed to open "/etc/ufw/after6.rules": Permission denied (13)
```
therefore I've resolved to use sudo when running rsync,leaving out (as I used to do already) these directories 
 ```
--exclude='/mnt' --exclude='/media' --exclude='/proc' --exclude='/sys'  --exclude='/dev'  --exclude='/tmp'  --exclude='lost+found'  --exclude='/var/run' 
```
is this a good idea? Are there any issues in running rsync as super user,and should I edit my -**-exclude** list accordingly?

---

### Post by prodigy_ on 2013-08-08
Rsync works fine with sudo. But you'll probably need to make a full backup first since your previous backups were incomplete.

---

### Post by papibe on 2013-08-08
Hi cogset.

As long as you are using 'sudo rsync' locally, there's no problem at all.

Most of the security concerns would come when you enable a system to receive root rsync connections over ssh, but that's another story.

Hope it helps.
Regards.

---

### Post by SeijiSensei on 2013-08-09
Are these backups running as a cron job, or do you have to run them manually?  If the latter, I would definitely consider putting the rsync command into root's crontab or, better yet, put the command into a root-executable script and place the script in /etc/cron.daily.  Then it will be run automatically each night. This method avoids the use of sudo entirely.

---

### Post by cogset on 2013-08-09
These are manual backups that I run locally on my system,as in manually  rsyncing the  / directory (with the exclude list posted above) of my  system on an external USB drive -ssh is  not involved at all,in fact I've actually removed it altogether (on a  side note,I still can't figure out why desktop distributions mainly  intended for home use should come with ssh installed:if someone really  needs it,I guess he'll be smart enough to know how to install it).

Automating  the whole process with a cronjob does sound really interesting,however this backup  process involves quite a lot of disk activity,and I wouldn't want it to start whilst I am doing something else-this being a desktop computer,I never leave it on overnight:if it is on,it means that I'm actually using it.

---

### Post by SeijiSensei on 2013-08-09
If you have an older machine around, say a largely unused desktop, you might consider converting it into a file server that runs continuously. Place files you want to save on that and let a cron job run a backup each night.  My server has a large external USB drive attached to which I write the backups so there's a second physical copy of every file.  (The server also runs RAID1, so each file is duplicated on two parallel hard drives as well.  But as they say, and to which I can attest, RAID is not a substitute for backups.)

---

### Post by DuckHook on 2013-08-09
> **SeijiSensei said:**
> If you have an older machine around, say a largely unused desktop, you might consider converting it into a file server that runs continuously.

+1

Another option that works quite well for me is to use an old laptop (otherwise similar setup--complete with external USB drive). Much better on the electrical bill and provides at least a modicum of battery backup.

---

### Post by cogset on 2013-08-12
> **DuckHook said:**
> +1

Another option that works quite well for me is to use an old laptop (otherwise similar setup--complete with external USB drive)

You lost me:I understand there's this second unity always running as a file server,but to run automated backups,you still have to keep your primary desktop running overnight,unless you've automated the process to shut it down once it's finished?

---

### Post by SeijiSensei on 2013-08-12
I have both my workstation and laptop configured to mount an NFS-exported directory on the server at boot.  Any files I want to save permanently get written there.  The server runs a nightly script that backs up those directories to an external hard drive.  The server runs constantly (it's also a mail server for a few domains), but the client machines can be shut down since any important files are already on the server and will be backed up automatically.

There are many other solutions to this.  For instance, you can add a [script that runs at shutdown]("http://ubuntuforums.org/showthread.php?t=2049855&p=12205356&viewfull=1#post12205356") to back up specific directories before turning off the machine.

---

### Post by DuckHook on 2013-08-12
I was just riffing off of SeijiSensei's suggestion to use an old desktop as a file server. By substituting an old laptop instead, you get lower electrical usage and battery backup (the laptop still runs even in a short power outage). However, the laptop, like the desktop, would have to be left on all the time.

It is true that you would have to leave your primary desktop running overnight if you want the rsync process to run when no one is around. However, I can't help asking why you get so much disk activity if rsync is run daily (as would be the case with a cron job)? The beauty of rsync is that it syncs only changed files. My own experience is that it runs a disk-intensive sync the first time, and is relatively quick and easy thereafter, unless you have massive amounts of changed files each day. Therefore, if you schedule the sync to occur every day at, say, lunchtime, it should be hardly noticeable.

---

### Post by Dave_L on 2013-08-12
> **cogset said:**
> 
is this a good idea? Are there any issues in running rsync as super user,and should I edit my -**-exclude** list accordingly?

System backups *should* be done as root.

[on Ubuntu 12.04] I do backups with rsnapshot, which is a Perl script that uses rsync. I back up these directories and exclude everything else:
/bin, /boot, /etc, /home, /lib, /lib64, /opt, /root, /sbin, /selinux, /srv, /ubiquity-apt-clone, /usr, /var

---

### Post by cogset on 2013-08-13
> **DuckHook said:**
> However, I can't help asking why you get so much disk activity if rsync is run daily (as would be the case with a cron job)? The beauty of rsync is that it syncs only changed files. My own experience is that it runs a disk-intensive sync the first time, and is relatively quick and easy thereafter, unless you have massive amounts of changed files each day. Therefore, if you schedule the sync to occur every day at, say, lunchtime, it should be hardly noticeable.

That's an interesting point:admittedly,I'm lazy about backups (I know...),so I'm not backing up the entire system daily (other stuff,as Firefox profile and email,I backup separately almost daily)-still,I find that full system backups after say a week or more take at least 15-20 mins,and that is excluding some virtual machines that I have installed,because I've found that those take ages.

Maybe I'm just overcautious,but do you people still use your computer whilst a backup process is running? Is that safe?
I close all other applications when running rsync,I'm not comfortable with using the system whilst the disk is so busy-maybe I just have a noisy/slow disk.

---

### Post by DuckHook on 2013-08-13
> **cogset said:**
> ...full system backups after say a week or more take at least 15-20 minsThis won't be the case if you back up daily, which, I gather, is the point with rsync running as a cron job.> ...that is excluding some virtual machines that I have installed,because I've found that those take ages.You may wish to exclude VMs from your rsync backups altogether and use a different backup strategy for them. The reason for this is that VMs are basically one big file, so even the act of just booting them up, without any changes to the VM OS itself counts as a "changed" file to rsync. I run close to 2 dozen VMs (I like to tinker), so cannot possibly include them in scheduled backups without going crazy. VMs that can be easily reinstalled (Linux, BSD, Unix) are non-issues so I don't back them up. My Windows VMs are backed up manually once every six months. The *contents* within are backed up much more frequently on a schedule, but using Windows backup software to an external file server. This way, I keep daily rsync backup volume to tiny little nibbles.> ...do you people still use your computer whilst a backup process is running? Is that safe?I find that this depends a lot on HW. On old HW, backing up while other programs are running tends to slow the system to a crawl and I get the same fears that you get. On my newer and far more powerful systems though, the backup process is hardly noticeable even when I am running VMs etc. so I don't worry about multitasking. It's true that you may have some files locked and therefore not backed up, but the nice thing about a daily cron backup is that those files get picked up the next day, so there is really very little exposure. In short, only you can decide what your comfort level is, but in theory, there isn't much that can go wrong if you continue working while rsync is running.

---

