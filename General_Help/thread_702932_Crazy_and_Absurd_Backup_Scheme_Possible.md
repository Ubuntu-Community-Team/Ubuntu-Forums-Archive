---
title: "Crazy and Absurd Backup Scheme: Possible?"
date: 2008-02-20
forum: General Help
---

### Post by xelapond on 2008-02-20
I just lost a ton of data because my 4 gig flash drive died, so then I started thinking about how insecure my data is, with no backup.  I designed a crazy backup scheme that seems foolproof, and I was wondering if it would be possible.  Here it goes:

All computers and servers are running Ubuntu GNU/Linux.

<hypothetical and not real(yet)>
I have my main desktop computer, which is mirrored exactly with version control with my main server.  My laptop is also synced in this manner, so any changes to files on my main computer also change on my laptop and the server.  My main server is also mirrored with my other server, that is not local, so If the house burns down and the three computers are lost with it my data is not lost.  Also, because I like to have a copy of my data with me I keep it on my flash drive(I may have to get a pocket hard drive, 'cause this will be big).  Every 24 hours or so(once a day) I will plug my flash drive into a computer, and diff/merge all of the files them between the drive and the server.  Any errors will be solved by hand.
</hypothetical and not real(yet)>

Could this be doable?  I would be very happy to research this more and write a lot of code myself, also publishing a how to and all of the code if its possible.  Also, I would like it to have minimal human intervention(except solving diff errrors) and would like it to be pretty fast(maybe backing up files as they change, rather then on a time base) so I can save a file and have it change very quickly on my laptop as well.

Just want to know your opinion on its feasibility, and when/if I do it I will post all code so the community can benefit.

---

### Post by Littleweseth on 2008-02-20
rdiff-backup. :) No need to reinvent the wheel yourself - some kind folks already came up against your problem and wrote this rather elegant tool to solve it.

rdiff-backup does time-versioned backups so you can do things like 'I want the directory /home/lws/DoomsdayPlans as it was on the 20th of February... stupid evil monkeys, GET OFF THE KEYBOARDS!' rdiff-backup also works quite fast (if i remember correctly, it figures out what to diff based on timestamp/size differences), though i'm not sure how it resolves diff conflicts.

Set that up as a cron job on all the relevant computers (you'll have to work out the exact details as per your computer setups) and you're set.

There also exists a KDE frontend for rdiff-backup called 'keep'. I've never used it, but you might want to give it a whirl. keep and rdiff-backup are both available from the repos.

--

We had this going at college, three of our computers syncing to a bittybox in someone's room running three 80gb hard drives in software RAID. :) Saved my *** at least once.

-lws

---

### Post by SpaceTeddy on 2008-02-21
i would have suggested rsnapshot over ssh, but your solution seems to work quite nice too...

if you want to find out more about rsnapshot here are the links to the howto...

the Howto
[http://www.rsnapshot.org/howto/1.2/rsnapshot-HOWTO.en.html]("http://www.rsnapshot.org/howto/1.2/rsnapshot-HOWTO.en.html")
and the howto for getting it work over ssh to manage remote machines
[http://troy.jdmz.net/rsnapshot]("http://troy.jdmz.net/rsnapshot")

rsnapshot only copies those files you changed, and will only store those which are changed. Only problem is, that it can only do a pull (i.e. copy from a computer) and not a push (i.e. copy to a computer)...

we have this baby running at work and with a few tricks you can even get it to work on almost any filesystem and server you like.

hope this helps your helps your backup scheme :)

---

### Post by xelapond on 2008-02-21
Cool.  Thanks guys!

Does rdiff really do anything with diff?

Would rsnapshot allow me to backup a snapshot to the server and then pull that over to my macbook pro?  So both the desktop and the laptop are the same?

Thanks, 

Alex

---

### Post by xelapond on 2008-02-21
Also, do I have to use a passwordless ssh server?  That seems kind of open to me.

Thanks, 
Alex

---

### Post by Littleweseth on 2008-02-21
if i remember correctly, rdiff can be made to both push or pull (you just need to have rdiff-backup installed on both computers.) I'm not actually sure on the technical details of how rdiff-backup operates, but the blurb from the rdiff-backup project page reads thusly :

---
[http://www.nongnu.org/rdiff-backup/](http://www.nongnu.org/rdiff-backup/)

rdiff-backup

A remote incremental backup of all your files could be as easy as
"rdiff-backup / host.net::/target-dir"[disclaimer]
What is it?

rdiff-backup backs up one directory to another, possibly over a network. The target directory ends up a copy of the source directory, but extra reverse diffs are stored in a special subdirectory of that target directory, so you can still recover files lost some time ago. The idea is to combine the best features of a mirror and an incremental backup. rdiff-backup also preserves subdirectories, hard links, dev files, permissions, uid/gid ownership, modification times, extended attributes, acls, and resource forks. Also, rdiff-backup can operate in a bandwidth efficient manner over a pipe, like rsync. Thus you can use rdiff-backup and ssh to securely back a hard drive up to a remote location, and only the differences will be transmitted. Finally, rdiff-backup is easy to use and settings have sensical defaults.

---

---

### Post by SpaceTeddy on 2008-02-21
> **xelapond said:**
> Also, do I have to use a passwordless ssh server?  That seems kind of open to me.


no, you are not using a passwordless ssh-server, you would be using public/private key authentification. i.e. you have a keyfile that authorizes you automaticially to the server. 

more to be found [here]("http://sial.org/howto/openssh/publickey-auth/")

but if rdiff can do push and pull, you might want to stick with that...

---

### Post by Spitphire on 2008-02-21
what would be a proper command to backup an entire system with rsync over a network to a remote location?

Is it possible with rsync?

what happens to all those /dev and sym links?? 

do /dev and sym links restore from backup as well?

---

### Post by SpaceTeddy on 2008-02-21
for me, i only backup /etc and the data folder... so anything that is NON-Standard. If you system really crashes, that is where the work goes... and if you have all the config files at hand, there is no reason not to reinstall.

as for backing up / - i don't know, i have NEVER done nor tried it... sorry

---

### Post by Littleweseth on 2008-02-22
> do /dev and sym links restore from backup as well?

IANAE, but backing up the entirety of / using a file-based backup seems like a really bad idea - consider that some toplevel directories (consider /proc, /dev) aren't really directories containing FILES, but dynamically updated system resources. I'm not sure how well defined the actions of rsync/rdiff-backup are on such directories, but you sure don't wanna find out. (it's likely to be ugly.)

For what it's worth : /dev isn't a directory proper, but the kernel's way of exposing devices to the OS - nothing in /dev is really a file, so it doesn't make sense to back them up. Every time you boot your computer, udev takes care of mapping your I/O hardware to /dev/[...] links and udev continues to play magic as you hotplug things like USB devices during use.

--

If you want a Full System Backup, you're better off using some kind of whole-disk/whole-partition imaging (see 'dd') - but note that doing this on mounted partitions is also a Really Bad Idea. Doing a really proper entire disk backup would involve having to boot from a livecd or network every time you wanted to do it.

You're really much better off just backing up /var, /home and /etc - these are the places where the 'soul' of your computer lives, and if you're worried about restoring the programs on your computer, you should be able to reconstruct the software installation on your computer by inspecting the files/logs within /var/apt.

--

> what would be a proper command to backup an entire system with rsync over a network to a remote location?
> Is it possible with rsync?

If i remember correctly, both the rsync and rdiff-backup FAQ's on the internet cover common usage cases with full examples. I don't have time to chase them up for you (have to wake up for work in 6 hours), but you should be able to find them by googling 'rsync FAQ' and 'rdiff-backup FAQ' respectively. Look these up for full details of usage.

And yes, it's possible to do backups with rsync - but rsync was designed more for keeping file mirrors up to date (i.e. making exact copies of ubuntu package repositories), not for personal file backups, so it doesn't do anything fancy like versioned backups or such. rsync will simply clobber old versions of files with new versions of files, which isn't terribly helpful when you discover you overwrote your Doomsday Device plans with your mother's recipe for baked chicken. (Unless your plan for world domination involves mass quantities of KFC, in which case i raise my hat to you.) :D rdiff-backup, however, DOES keep versioned backups and will save you from such embarrassment.

HTH;
-lws

---

### Post by dark_phantom on 2008-02-22
> **Spitphire said:**
> what would be a proper command to backup an entire system with rsync over a network to a remote location?

Is it possible with rsync?

what happens to all those /dev and sym links?? 

do /dev and sym links restore from backup as well?
I have not used rsync yet but I did this recently and this is what worked for me.  I backed my whole system to a USB drive with this command.

sudo tar cvpzf /media/MONSTOR/backup_`date +%m_%d_%y_%H_%M`.tgz --exclude=/etc/fstab --exclude=/boot --exclude=/proc --exclude=/lost+found --exclude=/mnt --exclude=/sys --exclude=/media /

Re-install Ubuntu and restore my system with sudo tar xvpfz backup.tgz -C / and had my old system back with no problems..

---

