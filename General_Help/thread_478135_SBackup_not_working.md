---
title: "SBackup not working"
date: 2007-06-19
forum: General Help
---

### Post by dennus on 2007-06-19
I have gone over this forum to see if my question was already answered, but couldn't find it, so here goes...

I start Simple Backup, select the directory to backup to (/home/dennus/test).
I press BACKUP NOW and get a message with an ID number. Other than that it does't do anything.

When I open up SYSTEM MONITOR and select ALL PROCESSES I see that it's sleeping. When I select MY PROCESSES I don't even see it. So, I guess it's there but just doesn't want to work for me.

Does anyone know what the problem could be here?

---

### Post by rbmorse on 2007-06-19
It looks to me like you are trying to store the backup in one of the directories (/home/dennus/test)  that gets backed up (home/dennus). 

This sets up a recursion and is an error that results from Sbackup trying to backup the backup as new files are added to the backup being backed up.   

I don't know if sbackup checks for this condition (it should). You might try locating the backup store somewhere outside of the set of directories that sbackup processes (/home, /etc, /opt by default as I recall)  or you can add the location of the backup store to sbackups exclusion list and see if it works then.  Of the two options I prefer using a directory outside of sbackups source set since I don't trust myself to get the exclusion syntax correct (is it /home/dennus/test, home/dennus/test/ or home/dennus/test/*)?

Ron Morse

---

### Post by dannyboy79 on 2007-06-19
> **rbmorse said:**
> It looks to me like you are trying to store the backup in one of the directories (/home/dennus/test)  that gets backed up (home/dennus). 

This sets up a recursion and is an error that results from Sbackup trying to backup the backup as new files are added to the backup being backed up.   

I don't know if sbackup checks for this condition (it should). You might try locating the backup store somewhere outside of the set of directories that sbackup processes (/home, /etc, /opt by default as I recall)  or you can add the location of the backup store to sbackups exclusion list and see if it works then.  Of the two options I prefer using a directory outside of sbackups source set since I don't trust myself to get the exclusion syntax correct (is it /home/dennus/test, home/dennus/test/ or home/dennus/test/*)?

Ron Morse

here's my sbackup.conf file located within /etc/. The gui will sometimes put the slash on the end and sometimes not, BUT if you look in your sbackup.conf, you'll see anything with a ZERO (0) will NOT be backed up. and as you can see /home/dennus/test
will WORK as I have already verified that my backup's are successful using this program. Here's the link of the instructions I put together for actually verifing your sbackup tar gz actually works. [http://ubuntuforums.org/showthread.php?t=401425](http://ubuntuforums.org/showthread.php?t=401425)

[exclude]
regex = \.mp3,\.avi,\.mpeg,\.mpg,\.mkv,\.ogg,\.ogm,\.tmp,/home/[^/]+?/\.thumbnails/,/home/[^/]+?/\.Trash,/home/.mozilla/.+/Cache/
maxsize = -1

[places]
prefix = /usr

[dirconfig]
/proc = 0
/sbin = 1
/home/daniel/ntfs = 0
/media = 0
/vmlinuz = 1
/bin = 1
/usr = 1
/initrd = 1
/boot = 1
/home = 1
/opt = 1
/lib = 1
/root = 1
/home/daniel/400gb-ext3 = 0
/etc = 1
/var = 1
/var/cache = 0
/home/daniel/400gb-ext3/backups = 0
/home/lost+found = 0
/home/daniel/300gb-ext3/torrents = 0
/mnt = 0
/home/daniel/400gb-ext3/laptop-backups = 0
/home/daniel/300gb-ext3/lost+found = 0
/tmp = 0
/dev = 1
/initrd.img = 1
/home/ftp = 0
/home/daniel/fat32 = 0
/home/daniel/500gb-ext3 = 0
/sys = 0
/var/tmp = 0
/cdrom = 0

[general]
purge = log
maxincrement = 7
lockfile = /var/lock/sbackup.lock
target = /home/daniel/500gb-ext3/backup
format = 1

---

### Post by rbmorse on 2007-06-19
Ah...thanks.

---

### Post by dennus on 2007-06-19
Guys, thank you for the replies. I just think it is more a problem of user-rights. The CONFIG doesn't ask me for a password and I don't see it running in System Monitor.

Dennis

---

### Post by dannyboy79 on 2007-06-19
try to remove and purge it, then reinstall it and that should fix it.

---

### Post by dennus on 2007-06-19
Remove I understand... but PURGE?  How does that work?

---

### Post by dannyboy79 on 2007-06-19
man apt-get

OR

man aptitude

then read what purge does. Just as an FYI, linux has way better support built into it than winbloz ever will, for almost every single program, there's what is called the man pages (manual) for commands. So if someone suggests you do something, you can always find out what it means yourself (that is most of the time) So if you review the man pages for either apt-get or aptitude, this will tell you how to purge and what it does.

If you're using synaptic, this option is merely renamed in there, it's name in there is called, completely remove, versus, just Uninstall, I believe.

---

### Post by dennus on 2007-06-19
-purge
          Use purge instead of remove for anything that would be removed. An
          asterisk ("*") will be displayed next to packages which are
          scheduled to be purged. Configuration Item: APT::Get::Purge.

Then why REMOVE first and Purge later on?

I've REMOVED it in Synaptic, MARK for COMPLETE REMOVAL. Does this include PURGing? I don't know how to enter the purge command in terminal. Sorry, I'm a NOOB!!!

---

### Post by dannyboy79 on 2007-06-19
sudo aptitude --purge sbackup

---

### Post by dennus on 2007-06-19
sudo aptitude remove sbackup
sudo aptitude purge sbackup
then

sudo aptitude install sbackup
sudo simple-backup-config

destination /var/backup
press BACKUP NOW
get a message with an ID number
then... nothing.
In System Monitor the process sbackup is only listed in ALL PROCESSES not in MY PROCESSES. So, nothing more happens...  :-(

Dennis

---

### Post by hummingbird59 on 2007-06-19
Have you seen this:  [http://ubuntuforums.org/showthread.php?t=332426&highlight=sbackup](http://ubuntuforums.org/showthread.php?t=332426&highlight=sbackup).  I was having the same problem(s) and reading through this fixed it.  I can't remember what I did but this thread helped.

---

### Post by dannyboy79 on 2007-06-19
the problem is because /var/backups does exist in feisty, you need to chose a directory that exists and that root can write to. I have it backed up to a directory within /media which is owned by me, NOT ROOT, just make sure the directory is writable and you'll be fine. good luck

---

### Post by dannyboy79 on 2007-06-19
> **dennus said:**
> 
In System Monitor the process sbackup is only listed in ALL PROCESSES not in MY PROCESSES. So, nothing more happens...  :-(

Dennis

it won't be in YOUR PROCESSES as you're not running it, sudo should be running it. Are you starting the program from the System, Admin, Simple Backup Config choice within the drop down, or are you entering simple-backup-config from the command line? if you're doing the second, then this is also your problem, as YOUR user can't access some of the directories that are backed up by default, you ened to run it as root.

also, you'll need to killall simple-backup-config's which are running so they don't conflict if you choose to run it again. (at least I think, it's better safe to kill the ones that aren't working then not to)

---

### Post by dennus on 2007-06-19
Thank for your help DannyBoy
---

I have tried running it as

sudo simple-backup-config
then made a new directory in /root/backup_test
and set destination to that directory

started BACKUP NOW
it says "backup initiated...."
and then nothing.
in System Monitor is just says SBACKUP  SLEEPING

I am about to give up.

---

### Post by dannyboy79 on 2007-06-20
may I ask why your running it from the command line? If you have a desktop manager installed, chose it thru that. For example, I have Gnome (Ubuntu Feisty), and I chose it thru System, Admin, simple-backup-config
then from the gui, make sure the directory you chose is there and that its writable. that's it, I can't understand why you're having so much problems with this????? also, what are your backup options? are you chosing timed backup? are you choseing manual backup? what folders do you have chosen to backup? what folders have you chosen to exclude?

---

### Post by dennus on 2007-06-20
I have tried both, the command line and simple-backup-config. Believe me, I too don't know why it is soo hard to backup. 

Included
/var
/etc
/home
/urs/local

exclude
/proc
/tmp
/dev
/var/cache
/var/tmp
/sys

I think this is standard.
Destination /var/backup
time; do backups never .... so I select BACKUP NOW!

How can I see the backups is placed in /var/backup?
I can not enter this directory, permission denied.

I think the problem lies here somewhere... Last night it did a backup-thing, but I can not see if it went well. I don't know how to open this directory. I have tried it both in Nautilus and via the command-line. In both cases... DENIED!!!

How can I make a new directory with write-permissions, while not being root???

Dennis

---

### Post by dannyboy79 on 2007-06-20
ok, we're back to the same thing all over again. You can't use a directory to backup to that is being backed up!!!! THis will cause a loop and basically make the sbackup not work. Not to mention that /var/backup doesn't even exist in Ubuntu unless you created it, which is another thing we have all said repeatedly!!!!! You either need to chose another directory that is NOT being backed up or add /var/backups OR /var/backup to your exclude list.

If you want to view th contents of the folder owned by root, then you simply switch to the root user, I use this command
sudo -i
then enter your sudo password, then you can go to that directory all you want. I really think you should read all the posts again and make sure you stop asking the same questions or making the same mistakes over and over, it really will make people now want to help you.

---

### Post by dennus on 2007-06-20
I really appreciate you helping me out. But why is it that SBACKUP will do a backup to /var/backup OUT OF THE BOX?  When this is not a good choice?  This I don't understand. I understand you'll get in a loop.

Now when you tell me SUDO -i I'm getting somewhere... can you believe I have asked this several times (also in Dutch forums) and noone tells me this ?!?!?  

root@dennis-desktop:~/backup_test# ls
2007-06-19_22.33.11.026312.dennis-desktop.ful

I see it has made a backup!  This was when I had set the destination to /root/backup_test.

One other thing, what is the point of making a backup on the same disk that Linux is on?  I prefer making a backup to my network-drive or something. This drive is mounted via smb://opslag/Dennis but I get a message saying I don't have permission to write. 

Before this, I have just started using Linux for a week or two, I was using Windows XP. The Network HDD was formatted in Windows. 

Anyway, I want to thank you for your patience!!!!

---

### Post by dannyboy79 on 2007-06-20
sbackup is used in more distributions than just Ubuntu, meaning just because /var/backup doesn't exist doesn't mean that it does exist in Debian or any other distro. Ubuntu by default makes a directory callled /var/backups and I am not sure why.

Also, many people have seperate partitions for each of their top level folders, they would have 1 for /etc, for /home, for /var, for /boot and any one you can think of, so that could be why the default backup is put on /var/backup. I am sure you got it working but to point out to everyone else, SUDO -i will not work, it's sudo -i. Linux IS case sensitive. I am glad you hung around and finally got it based on what we were trying to tell you. good luck

---

### Post by rbmorse on 2007-06-21
> **dennus said:**
> But why is it that SBACKUP will do a backup to /var/backup OUT OF THE BOX?  When this is not a good choice?  This I don't understand. I understand you'll get in a loop.

when I set up sbackup, I found the directory /var/backup was already set for exclusion, out of the box if you will, thereby avoiding the recursion that would otherwise occur. .Look at /etc/sbackup.conf

RBM

---

### Post by dannyboy79 on 2007-06-21
> **rbmorse said:**
> when I set up sbackup, I found the directory /var/backup was already set for exclusion, out of the box if you will, thereby avoiding the recursion that would otherwise occur. .Look at /etc/sbackup.conf

RBM


well as I have already said more then twice now, /var/backup does NOT exist in Ubuntu. Not to mention, post #17 shows what's in sbackup.conf and there is no /var/backup shown there and the author stated that this is what the defaults are.

---

### Post by rbmorse on 2007-06-21
OK...it's /var/backups not /var/backup (my mistake) 

And it most certainly exists in Feisty (and Gutsy, too). Here's what's in mine:

```

dpkg.status.0
dpkg.status.1.gz
dpkg.status.2.gz
dpkg.status.3.gz
dpkg.status.4.gz
dpkg.status.5.gz
dpkg.status.6.gz
group.bak
gshadow.bak
infodir.bak
passwd.bak
shadow.bak

```

---

### Post by dannyboy79 on 2007-06-21
> **rbmorse said:**
> OK...it's /var/backups not /var/backup (my mistake) 

And it most certainly exists in Feisty (and Gutsy, too). Here's what's in mine:

```

dpkg.status.0
dpkg.status.1.gz
dpkg.status.2.gz
dpkg.status.3.gz
dpkg.status.4.gz
dpkg.status.5.gz
dpkg.status.6.gz
group.bak
gshadow.bak
infodir.bak
passwd.bak
shadow.bak

```
I agree! I never said that /var/backups doesn't exist in Ubuntu. My point now for the umptenth time is that sbackup by default will backup to /var/backup, which for 1 doesn't exist in Ubuntu, and for 2 isn't in the exclude list so you can't use that location to backup too even if Ubuntu did have that directory because it would cause a loop and your backup would never finish and this would actually cause your machine to most likely lockup due to getting 100% full, unless that is if the developer of sbackup programmed in for sbackup to quit if the backup location is a folder that is trying to be backed up. I am done trying to help anymore, I can't make it any easier to understand as I have stated the same thing more than 3 times now.

---

### Post by rbmorse on 2007-06-21
> **dannyboy79 said:**
> I agree! I never said that /var/backups doesn't exist in Ubuntu. 

See post #13 this thread.

Now,  you're all huffy and in a bad mood but I think I understand what you are trying to say;

1. sbackup defaults to placing the backup store in /var/backup
2. this is a bug in sbackup because the directory name is incorrect, it should be /var/backups   < ---- note the "s"
3. Even if that is fixed, there is still a bug in sbackup because it is set to backup /var by default, and if the backup is in /var/backups that creates a recursion (unless there is internal checking for recursion that isn't immediately apparent) and that is a bad thing. This condition should be avoided by manually setting the backup location to somewhere outside of sbackup's list of directories to be included in its back up. 

Is that what you're trying to say? 

One other thing: I'll cop to an error about /var/backups being excluded by default.  Mine is, don't know how it got there, but I must have done it. But, a subsequent reinstall to a clean installation didn't have it so I must be mistaken.

---

### Post by dannyboy79 on 2007-06-22
> **rbmorse said:**
> 2. this is a bug in sbackup because the directory name is incorrect, it should be /var/backups   < ---- note the "s"
 

Everything you stated above is correct except for what I have quoted. I tried to previously explain that just because Ubuntu doesn't have a /var/backup folder doesn't mean that other Linux Distributions don't. Which means that this could be their intention to have it backup to /var/backup instead of /var/backups. I don't believe sbackup was created solely for Ubuntu. It was created during the Google Summer of Code is all I know. If it is in fact a bug, and ALL other Linux Distro's have /var/backups and NOT /var/backup, than we should definitely inform the developer.

---

### Post by gcclinux on 2007-06-22
Also having problems, any help would be great!

This is the command line output.

ricardo@ibm-laptop:~$ gksudo simple-restore-gnome
  File "/usr/sbin/simple-restore-gnome", line 442, in <module>
    SRestoreGTK()
  File "/usr/sbin/simple-restore-gnome", line 107, in __init__
    self.load_tree(self.default_target)
  File "/usr/sbin/simple-restore-gnome", line 198, in load_tree
    if str(gnomevfs.read_entire_file( self.target+"/"+adir+"/ver"))[:3] != "1.3":
gnomevfs.NotFoundError: File not found
ricardo@ibm-laptop:~$

---

### Post by dannyboy79 on 2007-06-22
may I ask why you're issueing the command from the terminal when the developers spent a whole summer of coding to get this to be a gui????? Please try to go to System, Admin, Simple-Backup-Restore or whatever it is and see if it works that way please.

Otherwise I can't help ya. I have never EVER had any problems with sbackup. I always use it thru the pull down menu within System, Admin.

---

### Post by gcclinux on 2007-06-22
well Dannyboy thx for your help, the reason I issued it via command line is to show what the error is, because I can't even launch it from the GUI System --> Administration

So I thought I'll be pro-active in post a error out before someone ask me what the error is.

Now that DannyBoy can't help me, is there anyone else that can?

Rico

---

### Post by dannyboy79 on 2007-06-22
do you have python and python-gnome2 libraries installed? you could always use the command line restore python script that comes along with sbackup, it's 

sudo srestore.py

---

