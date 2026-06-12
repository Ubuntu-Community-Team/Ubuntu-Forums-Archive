---
title: "Am I over complicating this rsync script?"
date: 2012-12-09
forum: General Help
---

### Post by Roasted on 2012-12-09
I have two small file servers in my house. Once a day I want one to copy the other. The only curve ball is, I noticed I cannot successfully rsync all of the data that my wife has because some of her files (particularly random hidden files that come in 600 permissions) fail due to permissions issues. In order to keep things cleaner I decided to break things up a bit. The only catch is I'm using the --delete flag, which as a result might fumble things if I'm thinking correctly.

Here's my script:

```
#!/bin/bash
set -e
rsync -az --delete /media/storage/kristi/ kristi@192.168.1.150:/media/NAS/backup/kristi/
rsync -az --delete /media/storage/jason/ jason@192.168.1.150:/media/NAS/backup/jason/
rsync -az --delete /media/storage/public/ jason@192.168.1.150:/media/NAS/backup/public/
rsync -az --delete /media/storage/backup_logs/ jason@192.168.1.150:/media/NAS/backup/backup_logs/
date >> /media/storage/backup_logs/Server_Backup.txt
ssh jason@192.168.1.150 'sudo /sbin/shutdown -h now'
exit

```

Basically I set up ssh key pairs with both myself and my wife. I have the first entry as my wife rsyncing her own data from server A to server B. That way there's no permissions headaches and I can avoid running rsync as root. Beyond that, jason is doing each additional folder that needs backed up individually. Reason being, if I used the --delete flag on say /media/storage/jason, then it would wipe out Kristi's stuff since its destination is within the same basic path, /media/NAS/backup/, am I right? Originally I thought I could do something like:

rsync -az --delete /media/storage/one /media/storage/two /media/storage/three /media/destination/... but if I want "kristi" to reside in "destination", then I need to either A) Do each line individually to avoid the --delete parameter from affecting anybody else besides its targeted directory, or B) run rsync as root when the script flies.

Is it acceptable to be doing multiple ssh-esque connections like this? (i.e. kristi and jason, for example) Am I over complicating this? Or is this making logical sense and the way I'm doing it is the way to go?

EDIT - New thoughts on the table on top of what's above. So I'm finding out that when my wife's stuff rsync's over, a lot of it I don't have access to. It's mostly hidden files for gimp and whatnot that are 600 permissions, so only she has access to them, but it results in errors in the rsync script. My intention is to have an error-less setup so that way the script completes, and therefore puts the date stamp in the text file like what I have above. (I understand that set -e implies that if a single thing in the script fails, the entire thing fails, i.e. then it won't put the date stamp in).

So my options are this. Either run rsync as root, or run rsync as her. I like the running it as her idea, so I may do that and just cron it to run under her username. Simple enough. The only catch is I'd like to also flirt with the run as root idea. Problem with that is this. What if server B's HDD fails? Server B's HDD is mounted at /media/storage, but if the HDD fails, /media/storage would simply be another directory running on the OS drive, which is an 80GB drive with only root on it. Running rsync as root would fill up /media/storage since, as root, you can do anything.

Is there a way to run it so it checks for the disk to be mounted prior to running as root? Or are there other issues with running rsync as root that would make me think otherwise?

---

### Post by SeijiSensei on 2012-12-09
Just run rsync as root, and you'll be fine.

If the number of directories you want to back up increases, you might consider using the "--include-from" directive to rsync and putting the list of directories into a text file.  If you need to exclude certain files and directories, you can put them in a file and use --exclude-from.  That's especially useful if you start a backup from the filesystem root and need to exclude pseudo-directories like /proc.

---

### Post by Roasted on 2012-12-09
> **SeijiSensei said:**
> Just run rsync as root, and you'll be fine.

If the number of directories you want to back up increases, you might consider using the "--include-from" directive to rsync and putting the list of directories into a text file.  If you need to exclude certain files and directories, you can put them in a file and use --exclude-from.  That's especially useful if you start a backup from the filesystem root and need to exclude pseudo-directories like /proc.

Sounds good. Do you understand what my concerns are, though? I'm not sure if my words are explaining my concerns accurately. Just to highlight it a bit more, here's my thought process. On Server B, there's /media/NAS. NAS is the mount point for a 500GB array. The internal drive is 80GB. If the 500GB fails to mount, /media/NAS still exists, even though it's an empty drive. As a result, the rsyncing as root (which is now possible thanks to using sudo/root) would be writing all of the data to the 80GB drive as opposed to the 500GB drive that has essentially failed to mount. Know what I mean? When the drive is mounted, I have permissions to it as a normal user. When it's not mounted, it's a root:root 755 directory, so the rsync fails, thereby saving me from writing to the wrong drive inadvertently. 

I just want to make sure that using root won't have any monumental issues. Sure, using root is the sure-fire easy way to do this in one inclusive command, but if there's consequences I want to make sure I'm well aware. In my testing here, it looks like I can easily write separate rsync scripts and have each one launch for the corresponding user via cron. But then I think, what if I had 500 users? How would this be done on a much larger scale?

I had ran into this issue a while back when my array failed to mount. As a result, my system was not bootable when it was rebooted because the entire hard drive was 100% full. The fix? I had to boot to a LiveCD, mount the internal drive, go to /media/NAS and thereby delete the contents. After all, the 80GB drive is not where I want /media/NAS to be, so deleting those contents were fine. The contents belong on the actual 500GB drive in question.

Thanks for the insight!

---

### Post by SeijiSensei on 2012-12-09
Well, I can see a couple of options.  One is to run the backup from server B and have it pull the files from server A.  Then the script could check to see if the NAS is mounted like this:

```

if [ "$(mount | grep /media/NAS)" != "" ] 
then
   do the backup
else
   mail -s "NAS not mounted" you@example.com
fi

```

If you need to run the job from server A, then you could run the command above on the remote via SSH and check the result.  I assume you are using shared-keys for SSH to avoid needing to enter the password. Something like:

```

TEST=$(ssh root@serverB 'mount | grep /media/NAS')
if [ "$TEST" != "" ]
etc.

```

---

### Post by Roasted on 2012-12-09
I like the thought of pulling the files over. Would that ensure that server b handles more of the processing? Server b has more processing power so if server b would inadvertently take on more of the cpu workload that would be better yet. Server a is a raspberry pi, hence the added benefit in the quad core box pulling vs the pi pushing. But that command seems easy enough. I'll give it a shot. Thanks!

---

### Post by thnewguy on 2012-12-09
The rsync command uses so little CPU time I don't think it really matters which one is pulling and which is pushing. The bottle neck is going to be the network connection.

I also agree about using root to sync files your user can't acess. That will make things a good deal easier. Regarding permissions, using rsync with the "-a" flag, as you have, is supposed to maintain the original permissions and file ownership.

One note thing: consider using the "-u" flag as well. It makes sure you're not copying files that are already newer on the receiving end. This avoids copying over files you have already updated on the destination host.

---

### Post by SeijiSensei on 2012-12-09
In all my years of using rsync I've never used the "-u" switch.  By default rsync transfers any file on the source that is not identical to the file on the target.  I'm not sure I see the reason for -u at all.  Can you give us an example where it's better than the default?

If you add "z" to the list of switches, rsync will use gzip to compress the files on the fly at the source and uncompress them on the target.  That can help with slower connections if the files largely contain text.  Files like images and multimedia that are already compressed will not compress further, so using "z" in this case will actually slow things down.  However, it sounds like both of your servers are on the same LAN, so you don't need to use compression.

---

### Post by Roasted on 2012-12-09
> **thnewguy said:**
> The rsync command uses so little CPU time I don't think it really matters which one is pulling and which is pushing. The bottle neck is going to be the network connection.

In my case, I'm using a Raspberry Pi. I'm running it slightly overclocked at 800MHz, but I'm watching top right now and rsync is taking upwards of 25% CPU. Granted I'm running some other things on it, but nothing that wouldn't already be running on it full time (samba, motion, etc). It's enough of a hit that if the other server can handle the load, I'd be happy with that.


> 
I also agree about using root to sync files your user can't acess. That will make things a good deal easier. Regarding permissions, using rsync with the "-a" flag, as you have, is supposed to maintain the original permissions and file ownership.


I'm trying to run as root now, but I seem to be hitting another road block. I'm logged in as root via sudo su at the terminal. I think the issue I'm running into is the user I'm utilizing for the ssh portion of the command.

For example, if I run:

> rsync -az --delete --progress jason@192.168.1.160:/media/storage/ /media/NAS/backup/

I get errors citing that I cannot access certain hidden files in Kristi's home directory.

If I run:

> rsync -az --delete --progress kristi@192.168.1.160:/media/storage/ /media/NAS/backup/

I get errors citing that I cannot access certain hidden files in Jason's home directory.

Problem is, I'm logged in as root in the actual terminal I'm executing this command from. I tried pushing from server A to B and also (in the above examples) tried pulling from server B to A. In both cases we have no winning cigar.

I'm almost certain (because of the cross referencing example above) that it's due to the user I'm utilizing for the initial SSH connection. How can I alter this?

EDIT - Got it working. Turns out because there's no actual "root" login, you cannot utilize the ssh-copy-id command (since you have to effectively log in as the user in question to utilize the ssh-copy-id script), so I was missing the point entirely. The fix? Create a file called "authorized_keys" (I gave it 600 perms, rw-------) within the .ssh folder in /root. aka, /root/.ssh/authorized_keys. Then add the public key from the Raspberry Pi server to the authorized_keys file of server B. Now instead of jason@192.168.1.150 I use root@192.168.1.150. Working great so far.

---

