---
title: "How to check for and remove folders older than x days?"
date: 2018-10-07
forum: General Help
---

### Post by Robert_Boutin on 2018-10-07
Hi, I have a VirtualBox VM named 3-Share that I want to back up daily, but I only want to keep 10 days of backups and delete anything older than that.  In cron.daily I created file "vmbackup" with 755 permission and running as root.  I have these instructions in the file:

#!/bin/bash
now=$(date +"%Y_%m_%d")
sudo mkdir /mnt/raid2tb/Backups/$now
sudo -u vmuser VBoxManage controlvm 3-Share acpipowerbutton
sudo -u vmuser rsync -avz /mnt/raid/LiveVMs/3-Share /mnt/raid2tb/Backups/$now/
sudo -u vmuser VBoxManage startvm 3-Share

I've confirmed the first three lines are creating the folders daily.  I'll check tomorrow but I'm pretty sure the rest of it will change from root to vmuser, shut down 3-Share, backup the complete 3-Share VM folders to my backup array in my newly created folder /mnt/raid2tb/Backups/YYYY_MM_DD, and then restart the VM 3-Share.

Assuming that all works, how would I go about automatically checking for and removing folders more than ten days old?  Also happy to accept suggestions on what I already have above.

As always, thanks for the guidance.

---

### Post by TheFu on 2018-10-07
```
find /path/to/directories -mtime +10 -print 
```
If that does what you want, add the **-delete** option.

If you only want to delete directories, not files, use -type d.
If you only want to delete files, not directories, use -type f.

'find' is very powerful, but the options aren't clear without examples and practice.  if you google "find examples", there are top 10 lists and top 20 lists with lots of good examples.  And there is always the manpage.  The examples inside it really help.  It is worth scanning the manpage because find can do so many things.

I used to backup VMs from outside the VM on the host machine, but that became too cumbersome and was taking hours.  We just didn't have time to do it that way, plus using so much storage was unacceptable.  We started treating VMs just like physical machines and back them from in the same way using rdiff-backup.  Backups are versioned, we can keep 60-180 days of versions because it is very efficient and backups take between 10 seconds and 5 minutes per machine.  On high risk servers, I keep 180 days of versioned backups which uses less than 2x the total storage being backed up.  For 60 days it uses 1.2x the original storage.  Highly efficient both in storage and speed.  Just a thought for you to consider.

Also, we stopped using virtualbox for a number of reasons, but mainly because of performance and stability.  There are better options, if you are interested.

---

### Post by Robert_Boutin on 2018-10-07
TheFu, as always your advice is welcomed and much appreciated.  rdiff-backup definitely appears to be the more efficient way to go.  I'll try this tonight and tomorrow night and let you know how it shakes out, but from what you've told me and what I've since checked out online, it's what I need (as long as I get the syntax correct...).  You've suggested KVM to me in the past and I've checked it out, but I feel KVM is beyond my skill level at the moment.  At some point I may try to take it on, but I'm not an IT guy, just trying to learn as I go.  For now I think KVM may consume more time and ability than I have of either.

---

### Post by TheFu on 2018-10-08
```
$ sudo rdiff-backup --exclude-special-files  /  remote-server:/backups/local-server-name/
```
This would "push" the backup to a different server.
ssh authentication via keys is usually required to handle networked backups, so they can be run overnight, automatically.  If you have DBMSs running, those need to be quiesced before the backup to avoid data corruption.  Or use LVM snapshots.  
The source and the target for the backup can be local or remote. "Pulling" the backup is better for security almost always, but slightly more complicated.
```
$ sudo rdiff-backup --exclude-special-files  remote-server:/ /backups/remote-server/
```
My backups are a little more complex, since I don't backup the core OS. Saving storage space for backups matters to us. It also makes backups take less time.  And the first step we use for restoring is to install a fresh Ubuntu with an ssh-server active.  Doing it that way solves lots of grub setup problems, having to manually fix the fstab entries and lets us restore to very, very, different hardware. Backups that can't be quickly restored to different hardware AND work aren't very useful to us.

If vbox is meeting your needs, excellent.  It works great for many people.

KVM works with virt-manager, which is a GUI very much like virtualbox. Point-n-click for VM creation and running and changing settings.  NAT networking is setup automatically, but bridged networking has to be setup outside the VM/virt-manager. Standard Linux bridges with all the capabilities and complexity are used.

Do not install virtualbox and kvm hypervisors on the same hosts.  Only 1 hypervisor per physical machine.

---

### Post by Robert_Boutin on 2018-10-11
Thanks for your help as always.  So with your advice here is my solution to accomplish my original goal of shutting down my VirtualBox vm nightly, backing it up, restarting it, and then removing backups older than a year.  
**ls -l /etc/cron.daily**
*-rwxr-xr-x 1 root root  599 Oct 10 22:59 vmbackup*

**vmbackup**
[I]sudo su - vmuser -c "VBoxManage controlvm 3-Share acpipowerbutton"
sudo su - root -c "rdiff-backup /mnt/raid/LiveVMs/3-Share /mnt/raid2tb/Backups/3-Share/"
sudo su - vmuser -c "VBoxManage startvm 3-Share"
sudo su - root -c "rdiff-backup --remove-older-than 1Y /mnt/raid2tb/Backups/3-Share/"[/I]

[LIST]
[*]first line shuts down my vm "3-Share" as the vmuser
[*]second line uses rdiff-backup to perform an incremental backup of 3-Share to the folder /mnt/raid2tb/Backups/3-Share/
[*]third line brings 3-Share back online
[*]fourth line checks for backups older than 1 year and removes them
[/LIST]

---

### Post by TheFu on 2018-10-11
A few questions/comment.

Are you backing up the .vdi file(s)?  Probably not a good idea.

When using rdiff-backup, using the --exclude-special-files is pretty important.  It won't get FIFOs or named pipes or device files that go never end.

I'd validate that the backup partition is actually mounted. Been burned by that. A full / sucks.

BTW, is there a reason you don't just leave the VM running and backup using C/S ssh connection? No downtime.

Not all OSes honor the ACPI power commands. Be certain that is full validated periodically.  I've had it stop working after a kernel update and then start working a few weeks later.

I would just run the script from a root crontab, so none of the sudo/su stuff is needed. sudo  su - is the same as **sudo -i**. To run as a different userid, **sudo -l -U user**, fewer subshells. Probably not THAT important.  If it works, that's usually good enough.

cron.daily/ is an anacron location.  That means it runs at random times "sometime" in that 24 hr period.  With a specific crontab entry, we get control over the hour and minute that the backup begins. Subtle, but important difference.  Probably don't want a VM being taken down at 10:15am.  I've been burned.

---

### Post by Robert_Boutin on 2018-10-18
***Are you backing up the .vdi file(s)?  Probably not a good idea.***
I did set it up to do just that.  Maybe what I'll do is just copy the full vm folder, say monthly, and then do the daily backup of just the data directory and database since those would be the difficult/impossible to replace items.

 When using rdiff-backup, using the --exclude-special-files is pretty important.  It won't get FIFOs or named pipes or device files that go never end.

 ***I'd validate that the backup partition is actually mounted. Been burned by that. A full / sucks.***
The backup array is mounted at startup, so far seems not to have been an issue.  But I don't know what I don't know.

 [I][B]BTW, is there a reason you don't just leave the VM running and backup using C/S ssh connection? No downtime.
[/B][/I]I'd prefer to leave the VM running, I just thought it was bad juju to try to back up a machine that wasn't in a static state (not sure why I thout this).  But if I stick to backing up just the database and data directory, I guess my concern is unfounded regardless.

***Not all OSes honor the ACPI power commands. Be certain that is full validated periodically.  I've had it stop working after a kernel update and then start working a few weeks later***.
I noticed that with the Windows 7 VM.  The other 5 or 6 are all Ubuntu 18.04 Server, so far all have behaved.  But your observation is noted, I'll have to check periodically.

 I would just run the script from a root crontab, so none of the sudo/su stuff is needed. sudo  su - is the same as **sudo -i**. To run as a different userid, **sudo -l -U user**, fewer subshells. Probably not THAT important.  If it works, that's usually good enough.

 [I][B]cron.daily/ is an anacron location.  That means it runs at random times "sometime" in that 24 hr period.  With a specific crontab entry, we get control over the hour and minute that the backup begins. Subtle, but important difference.  Probably don't want a VM being taken down at 10:15am.  I've been burned.
[/B][/I]Yes, I saw this morning that my backups were starting around 7:30 a.m., 3:30 a.m. would be much better. 

I'll work now on modifying the script to run from a crontab that incorporates your suggestions.  Thanks!

---

### Post by TheFu on 2018-10-18
> **Robert_Boutin said:**
> ***Are you backing up the .vdi file(s)?  Probably not a good idea.***
I did set it up to do just that.  Maybe what I'll do is just copy the full vm folder, say monthly, and then do the daily backup of just the data directory and database since those would be the difficult/impossible to replace items.

Copying large files like VDI isn't a good idea, IME.  But everyone needs to learn things like this on their own.

> **Robert_Boutin said:**
> 
 ***I'd validate that the backup partition is actually mounted. Been burned by that. A full / sucks.***
The backup array is mounted at startup, so far seems not to have been an issue.  But I don't know what I don't know.

When it happens, and it will eventually, hopefully it doesn't take an OS that refuses to boot to learn this lesson.
> **Robert_Boutin said:**
> 
 [I][B]BTW, is there a reason you don't just leave the VM running and backup using C/S ssh connection? No downtime.
[/B][/I]I'd prefer to leave the VM running, I just thought it was bad juju to try to back up a machine that wasn't in a static state (not sure why I thout this).  But if I stick to backing up just the database and data directory, I guess my concern is unfounded regardless.

No.  Data corruption is a real concern, but there are techniques to prevent those things on running systems (LVM-snapshots and dumping the SQL DBs prior to any backups).  You cannot copy a VDI file while the system is running and NOT expect data corruption.  That is one more reason NOT to use VDI file copies as backups. There are others. 
> **Robert_Boutin said:**
> 
***Not all OSes honor the ACPI power commands. Be certain that is full validated periodically.  I've had it stop working after a kernel update and then start working a few weeks later***.
I noticed that with the Windows 7 VM.  The other 5 or 6 are all Ubuntu 18.04 Server, so far all have behaved.  But your observation is noted, I'll have to check periodically.

It is working on my Win7 VM, but I installed it with ACPI enabled. This was a specific choice in my setup.
> **Robert_Boutin said:**
> 
I'll work now on modifying the script to run from a crontab that incorporates your suggestions.  Thanks!

I learned all the things I'm suggesting by doing most of the things you are doing now, years ago. I was hoping to help you avoid the pain that I had, but perhaps that isn't possible or even needed. Maybe the methods are perfect for your needs.  IDK.

---

