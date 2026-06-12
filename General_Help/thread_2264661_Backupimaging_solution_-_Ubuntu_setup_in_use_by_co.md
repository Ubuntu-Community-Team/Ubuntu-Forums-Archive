---
title: "Backup/imaging solution - Ubuntu setup in use by computer non-freaks"
date: 2015-02-09
forum: General Help
---

### Post by kaweka on 2015-02-09
Hi, As for 14.04 LTE and later is there any chance to have a backup / system disk imaging solution as 
simple in use and productive as for instance Acronis True Image, Symantec Ghost, Apple True Image.....?

The concern is there is a Ubuntu based PC used mainly by PC-non-freaks with rare assistance of administrator, nor a PC-freak local assistance,
despite the fact of rare presence of a Linux (Ubuntu) experts.

The backup solution needs to support
- make the backup while the user regular work in progress (means plenty of files are open by system or application)
- support recovery from backup in short time without hacking here and there,
  means the backup must include practically every bit of Ubuntu installation and all data produced by Ubuntu usage.
  Of course all entries in system file tree produced dynamically at run-time must not be in backup.
- incremental backups
- backup scheduling
- scheduling with postpone to nearest possible point of time in case of system is powered down at backup schedule
- stable and bug-free - not worser than mentioned state-of-the-art solutions for other platforms.


Secondarily a backup solution for use-case as below is needed.
Ubuntu setup as mentioned above is in progress. Several points are still to be carried out
before the handover to user. For instance other Ubuntu flavours are going to be tried out
if they meet user needs closer as the Ubuntu native does it. It means a roll-back from 
other flavour tial-out to native Ubuntu in short time and without extensive study of documentations here and there must be possible.

---

### Post by HermanAB on 2015-02-09
Yup.  It is called CloneZilla.

---

### Post by slickymaster on 2015-02-09
> **HermanAB said:**
> Yup.  It is called CloneZilla.
+1 to Clonezilla.

It's similar to True Image or Norton Ghost. In your case opt for [Clonezilla live]("http://clonezilla.org/clonezilla-live.php"), which is the one suitable for a single machine backup and restore.

---

### Post by kaweka on 2015-02-09
Thanks for all the feedback from you.
In Clonezilla wiki a read a statement neither incrementals nor differential are supported.
It would mean each and every backup process is whole backup which takes long time.

There are more point where Clonezilla does not meet the set requirements:
Backup destination container must not be smaller than the stuff being backed up.
The reference solutions produce images which are several factors smaller than backup source.
Backup process while in a regular work is not possible.
No, Clonzilla definitely does not meet these requirements. I am sorry.


Me seems to have found the solution for use case #2.
Just start that computer from Live Ubuntu - use its deju dup to backup the mounted partitions
with Ubuntu installation on it to be backed up. 
Any stuff created dynamically at run-time should not be existing because that Ubuntu system not alive.
Any caveats regarding this choice?

---

### Post by dragonfly41 on 2015-02-09
I'm going to suggest that you at least try Webmin .. 
and Usermin which comes with it .. for custom server administration.

Webmin is in Ubuntu Software Centre.

In the scenario you describe Webmin/Usermin seems a good fit.

It is definitely not Clonezilla.

You need to define your users into ..
those who have the full use of Webmin (superusers)
those who have access to a reduced subset of Webmin features.

So your Webmin superuser(s) can setup the backup commands 
and profiles and then go to Webmin > Usermin configuration
to define the reduced set of modules open to your 
usermin community

For example you may want to open up ..

System > Bootup and Shutdown
System > Filesystem Backup
etc.

In other words Usermin (which runs on port 5000) 
can be a much leaner GUI than Webmin (which runs on port 10000).

To explore your requirements ...

For differential backup you can specify 
Custom Commands to run rsync (or other) on selected files.

For backup while regular work is underway you might be able to run
cron jobs on dormant assets (run a test to see if asset is in use before backing up).

So really you can customise your backup workflow.

---

### Post by kaweka on 2015-02-09
@dragonfly41
Thanks for your help. Please allow me to come to your input as next.

In the meantime it turned out that my backup concept for use-cas #2 failed.
Had started from Live Ubuntu 14.04, then mounted root and home partitions of Ubuntu installation to be backed up under /media.
Actually no files should be open nor locked nor any items in file system tree generated dynamically at run-time  (processes, devices, drivers,...)
should be present on the mounted partitions.

Deja dup was not able to open several files in home directories and outside of it. So the backup is not complete and unreliable.
It was not possible to save the produced logs nor to find its log file on file system tree in a short time.
Hence, it is not possible to present you the details here.

---

### Post by kaweka on 2015-02-09
"WebMin was in Ubuntu until 5.10 Breezy Badger, and was then dropped because it is not compatible with the way that Ubuntu packages handle configuration files, and caused unexpected issues with people's systems..."
Source: [https://help.ubuntu.com/community/WebMin](https://help.ubuntu.com/community/WebMin)
That's the reason why my Ubuntu Software Center does not offer Webmin nor Usermin at all.

The searched solution has to produce minimal overhead on user and administrator side. It must be also of high reliability.
Therefore I avoid solutions generally not compatible with concepts used in Ubuntu.
Anyhow was a good hint.... The Ubuntu Software Center and the original installation offers some Ubuntu dedicated administration environments like Landscape.
Maybe I will find something which is satisfying.

---

### Post by dragonfly41 on 2015-02-09
> 14.04 LTE and later ..

I don't understand why you can't find webmin (search lowercase!) in your Ubuntu Software Centre. It is in mine (14.04).
And usermin is bundled within webmin.

Your other reasons don't stack up .. but its your call.

---

### Post by slickymaster on 2015-02-09
> **dragonfly41 said:**
> I don't understand why you can't find webmin (search lowercase!) in your Ubuntu Software Centre. It is in mine (14.04).
And usermin is bundled within webmin.

Your other reasons don't stack up .. but its your call.

webmin package doesn't exist in the Ubuntu repositories, as you can confirm [here]("http://packages.ubuntu.com/").

In order to install it in Ubuntu one has to add the webmin official repository to the **/etc/apt/sources.list** file or download it from their  downloads page and then install it through **dpkg --install** and deal with all the missing dependencies.

---

### Post by dragonfly41 on 2015-02-09
My mistake .. I remember now that I added webmin to /etc/apt/sources.list

I do think that kaweka jumped to the wrong conclusion too soon ... before trying ...

From the link provided .. read post #6 .. and then further ...

[https://www.virtualmin.com/node/21110](https://www.virtualmin.com/node/21110)

> 
That information was misleading back then, and it's ridiculously incorrect today. 
...
There are thousands of Debian/Ubuntu servers running Virtualmin (and uncountable numbers running Webmin). Our ticket tracker and forums are searchable. If there were compatibility issues with any OS, you'd be able to figure that out really quickly. But, it's free software. Try it and judge for yourself. In a world with free virtualization tools, there's no reason not to play with it in a sandbox environment and see how things work for you.

---

### Post by kaweka on 2015-02-10
Good to know. Thanks. However if I look at the straightening discussion behind provided link it is dated to '12.
For my decisions I need more actual statements, or at least be able to see that the vintage one ('12) is still valid.
Unfortunately no free resources to make this search. Unfortunately no free resources to deal with missing dependencies, with steady hacking here-and-there.
I looks to be great tool, however not possible for me to invest big extent of efforts. A drop for whole hosting project if no solution can be found in reasonable time.
That (question of backup solution) is one of plenty points in whole big project. I am not able to invest efforts of such extents in every second projects element. Up to now it runs like every
second/third project's element would consume more than reasonable amount of work resources.

---

### Post by Mark Phelps on 2015-02-10
I've used two Linux backup solutions -- Clonezilla and RedoBackup, but each requires booting from a CD or USB to run the backup.  Sorry, don't know of any backup solution that allows you to use the system while the backup is being done.  Windows does this because their backup apps use VSS; I'm not aware of any VSS solution in Linux.

---

### Post by cl-netbox on 2015-02-10
The best way to do a system backup is to create it when the system is not running.
Clonezilla has not the nicest UI but - what is most important : RELIABILITY=100% !
For backing up files and folders Deja-Dup is a conveniant and easy to use solution.

---

### Post by kaweka on 2015-02-10
Me won't dare to ask the user to boot his computer and let it run unused and out of any log-on for the duration of the backup.
It is just a theft of his valuable time and his other resources.
Me won't dare to ask our lovely natural environment to accept the burdens coming from all the machines running only for backup.
Hmm, you are right, it is not such critical when the used solution supports incrementals or differential backups, and the user does not produce big increments/differentials.
**_what is most important : RELIABILITY=100% !_** I can only double it. Reliability and productivity!
Productivity while in backing up, productivity while on recovering.

> The best way to do a system backup is to create it when the system is not running.
Even that was tried as well. It was tried by booting the computer with Ubuntu Live USB. Then read-only mounting the root and home 
partitions to be backed up under /media. Then starting the backup using deja dup. It simply did not work. More details here in thread.
Actually why, the Ubuntu under backup was sleeping, no files should be open nor locked, no entries in file system tree coming from 
process or device drivers in operation.....

Curiously deja dup first makes a big a long in time scan of changes. Following that it attempts to write to destination
storage. If it does not get sufficient access rights it aborts the job. Why not to carry out this check at the beginning?
The big scan for changes does not need to be made if no access rights to destination handover.

---

### Post by dragonfly41 on 2015-02-11
> Productivity while in backing up, productivity while on recovering.

I've been pondering on your requirement to have backups underway while user(s) continue working.
As stated by other writers here that seems to be a tall order. Perhaps even undesirable.
On some sites this "productivity" requirement is referred to as "concurrent backup" .. particularly in the context of concurrent users database backups.

In searching through Ubuntu forum and further afield I found little on "concurrent backups", the usual advice being to shutdown your server and use .. say .. clonezilla.   This is safe.

If this truly is a necessary requirement .. i.e. as you say sustaining (24/7 ?) productivity while backing up concurrently .. then one thought is to have "micro backup sessions" which take place at natural breaks in user sessions.

Incidentally clarify how many users to consider per server?

Natural breaks .. (where productivity = 0) .. can be at these points

startup
user login
user logout
shutdown

and these can be used to trigger backup scripts.   
But there will probably be other concurrent users and this approach will only work for backing up user profiles.

e.g. at user login the bash script calls can be placed in

 ~./profile

...

Now as to the tool to use .. [COLOR=#696969]**rsnapshot**[/COLOR] in Ubuntu Software Centre seems to be a good candidate. 
This can be setup in config files ...

I found some writeups here ...

[http://www.rsnapshot.org/howto/1.2/rsnapshot-HOWTO.en.html](http://www.rsnapshot.org/howto/1.2/rsnapshot-HOWTO.en.html)

[https://kamaradski.com/1245/how-to-install-and-setup-rsnapshot-incremental-remote-backup](https://kamaradski.com/1245/how-to-install-and-setup-rsnapshot-incremental-remote-backup)

[http://jeffskinnerbox.me/posts/2014/Feb/08/network-backups-via-rsync-and-rsnapshot/](http://jeffskinnerbox.me/posts/2014/Feb/08/network-backups-via-rsync-and-rsnapshot/)

and this article discusses how to rollback if rsnapshot process has been interrupted ... so this is one risk to consider ..

[http://blog.philippheckel.com/2013/06/28/script-run-rsnapshot-backups-only-once-and-rollback-failed-backups-using-rsnapshot-once/](http://blog.philippheckel.com/2013/06/28/script-run-rsnapshot-backups-only-once-and-rollback-failed-backups-using-rsnapshot-once/)

...

There is this feature in rsnapshot ...

>  If you want to run anything before or after rsnapshot finishes take a look at the cmd_preexec and cmd_postexec lines.

So you could shut down processes before running rsnapshot job and open processes again after completing rsnapshot job.

...

The conclusion is that it seems that concurrent backup jobs *might* be possible but the natural break points in user sessions need to be defined carefully.

...

In searching around I found an Rsnapshot module to add into webmin.

rsnapshot + webmin

[http://tbanelwebmin.free.fr/](http://tbanelwebmin.free.fr/)

and this similar tool which does not require webmin ...

[http://dobrev.ws/projects/webrsnapshot](http://dobrev.ws/projects/webrsnapshot)
[https://github.com/dobrevg/webrsnapshot](https://github.com/dobrevg/webrsnapshot)

...

I'm going to try out rsnapshot (if only to save backup space).

---

### Post by redcom on 2015-09-23
Maybe now it is not necessary, but someone else might need it.

My suggestion for you is "Back in time" ([http://backintime.le-web.org/](http://backintime.le-web.org/)). This tool is visual and allows you to easily select which folders to backup and where (external HD is allowed), can create incremental backups. The problem is that it doesnt allow backup scheluding (or I don't know how)

If you don't mind using console, you could try Bera Backup ([http://www.portalprogramas.com/en/bera-backup.php](http://www.portalprogramas.com/en/bera-backup.php)). It also allows incremental backups, a recovery tool and can schelude it using crontab.

You could find more tools here 
[http://www.techrepublic.com/blog/10-things/10-outstanding-linux-backup-utilities/](http://www.techrepublic.com/blog/10-things/10-outstanding-linux-backup-utilities/)
but most of them are too complex por a "non-freak" guy

---

