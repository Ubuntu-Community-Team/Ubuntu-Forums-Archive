---
title: "chown -R hasn't worked!?"
date: 2018-02-08
forum: General Help
---

### Post by MibunoOokami on 2018-02-08
Using rsync to back up my computer, there were a couple of files came up with this error 
```
rsync: send_files failed to open "/home/username/directoryname/filename" : Permission denied (13)
```

I thought the easiest solution which has worked in the past would be to run ```
sudo chown -R username /home/username/*
``` to cover all my bases by changing owner of everything, rather than typing each filename individually, There were no error messages so I figured it worked properly, but I'm still getting the same permission message... There's no reason I can see as to why chown -R didn't work, AFAIK I own the files. Have I missed something, or is it possible to end up with a file which has unchangeable permissions?

Thanks in advance

---

### Post by TheFu on 2018-02-08
They could be hardlnks or symlinks or pointing to file systems that do not support Unix permissions?
Can you post the **ls -al "/home/username/directoryname/filename"**?

---

### Post by HermanAB on 2018-02-09
You forgot the colon:
> 
sudo chown -R username: /home/username/*


As mentioned above, some things cannot be changed.  For example, Gnome has one or two config files that are not really files.  I don't know the details, since I don't use Gnome.

---

### Post by Impavidus on 2018-02-09
Whether you own the files isn't really relevant, it's about having read permission (and in case of directories, execute permission). The owner usually has read permission, but you could check that.

---

### Post by TheFu on 2018-02-09
I don't think the : is needed.  I've never used it unless a group change is included. The examples section of the manpage shows chown use without a : or . BTW.

To me, the most likely issue is that a directory in the way down to the file had the eXecute permissions removed.

---

### Post by leunam12 on 2018-02-09
Are you rsyncing to an NTFS drive? I used to get errors with rsync when doing home backups until I formatted the backup drive to EXT4. Also I use sudo. Like this```
sudo rsync -aAXv /source/ /destination/
```

---

### Post by sisco311 on 2018-02-10
[~/.gvfs]("https://en.wikipedia.org/wiki/GVfs") can also cause some troubles.

---

### Post by haplorrhine on 2018-02-10
Maybe a ***chattr*** flag is stopping ***chown.***
[http://manpages.ubuntu.com/manpages/trusty/man1/chattr.1.html](http://manpages.ubuntu.com/manpages/trusty/man1/chattr.1.html)

For example,
chattr -i
removes the "immutable" flag.

---

### Post by TheFu on 2018-02-10
> **haplorrhine said:**
> Maybe a ***chattr*** flag is stopping ***chown.***
[http://manpages.ubuntu.com/manpages/trusty/man1/chattr.1.html](http://manpages.ubuntu.com/manpages/trusty/man1/chattr.1.html)

For example,
chattr -i
removes the "immutable" flag.

ACLs can also do it.  get/setfacl.

---

### Post by MibunoOokami on 2018-02-21
Hi everyone, thanks for your replies. Sorry for the very slow response it’s been a busy week. Here are some outputs, I’ve changed the actual username to “username”, I hope this helps. Basically a lot of hidden directories (.mozilla, .thunderbird, .adobe etc) have permissions that I can’t even view using the ```
ls -al
``` command. 

All other files have the same output as seen in the detailed examplea few lines down ```
-rwxr----- 1
``` 
 
 
 ```
ls -al "/home/username/.mozilla"
 ls: cannot open directory '/home/username/.mozilla': Permission denied
```
 
 
 ```
ls -al "/home/username/Pictures-2/2018/01/16/20180116_145931.jpg"
 -rwxr----- 1 username username 3983879 Jan 16 14:59 /home/username/Pictures-2/2018/01/16/20180116_145931.jpg
```
 
 
 @leunam12 You know now that you mention it, it is a new HDD and I don’t think I formatted it before I started using it. #-o

---

### Post by vanadium on 2018-02-22
Do a```
ls -ld "/home/username/.mozilla"
``` to check the permissions of the .mozilla folder itself. It is absolutely not normal that you would not have permissions to that folder. It would let me suspect that you have run firefox as root at one time. Then again, however, your chown command should have changed it back to normal, but the ls -ld command will tell what the permissions and who the owners are.

---

### Post by TheFu on 2018-02-22
> **MibunoOokami said:**
> 
 
 @leunam12 You know now that you mention it, it is a new HDD and I don’t think I formatted it before I started using it. #-o

You can't just start using a HDD without formatting.  If it was new and you installed Ubuntu onto it, that process would format it.

Sometimes new users screw up permissions so badly that starting over is the best action. I'd wipe everything and reinstall, being careful NOT to use sudo/root next time.  My rule is NEVER use sudo with any GUI programs.  NEVER.

We've assumed the disk isn't bad.  It could be, even if it is new.  We've made 1,000s of assumptions. If any aren't correct and we don't know that, well ... garbage in = garbage out.  These assumptions are true for normal Ubuntu installs, so it isn't usually an issue.

---

### Post by MibunoOokami on 2018-02-23
@[COLOR=#000000]vanadium[/COLOR] Here’s the output. I can’t think of an occasion where I would have run a program as root, or even using sudo. Could I have done so without knowing?
 
 
 ```
ls -ld "/home/username/.mozilla"
 drwx------ 5 username username 4096 Dec 24 09:46 /home/username/.mozilla
```
 
 
 @TheFu: I didn’t format the destination external HDD that I’m backing up on which is quite new. Old one ran out of space.

---

### Post by vanadium on 2018-02-23
There is nothing strange to be seen in your output. Permissions appear to be correct. If you username is indeed "username" and if you are logged in as "username" or as "root", you should be able to list the contents of that folder. 

instead of ls -al "/home/username/.mozilla", try the commands
```

cd
ls -al .mozilla

```
My guess is that you also turned off execute permissions of /home and home/username for yourself, so you cannot access these folders with an absolute path.
The best advise indeed might be a reinstall, but you could try if following command still saves you:
```

sudo chmod 755 /home home/username

```

---

### Post by Impavidus on 2018-02-23
There's one strange thing:
> **MibunoOokami said:**
> Hi everyone, thanks for your replies. Sorry for the very slow response it’s been a busy week. Here are some outputs, I’ve changed the actual username to “username”, I hope this helps.
...
 ```
ls -al "/home/username/Pictures-2/2018/01/16/20180116_145931.jpg"
 -rwxr----- 1 username username 3983879 Jan 16 14:59 /home/username/Pictures-2/2018/01/16/20180116_145931.jpg
```
A jpeg file with execute permission? That doesn't make sense. Altough it doesn't harm your system in any way, this indicates some blanket chmod commands were used, which could very well have messed things up.

Although it sounds implausible, I cannot think of anything more plausible than vanadium's guess.

---

### Post by TheFu on 2018-02-23
I'm guessing that an NTFS file system has been connected to the HOME somehow and that mount permissions are stuck.  HOME directories need to use a Linux file system, never NTFS or FAT-whatever.  Extra storage **can** be added below HOME with NTFS, but not the ~/.config/ directory or the ~/.  Linux cares about file systems.

The output from **df -hT** will help us.  For example, here's mine (with odd file systems remove):
```
$ df -hT
Filesystem                        Type      Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--mate--vg-root ext4       55G   38G   14G  74% /
/dev/sda2                         ext2      473M   69M  380M  16% /boot
/dev/sda1                         vfat      511M  3.6M  508M   1% /boot/efi
/dev/sda4                         ext4       40G   20G   19G  51% /misc/Stuff
```
Please use "code tags", like I did so things line up nicely.

---

### Post by MibunoOokami on 2018-02-24
[COLOR=#000000]> **TheFu said:**
> I'm guessing that an NTFS file system has been connected to the HOME somehow and that mount permissions are stuck. [/COLOR]

[COLOR=#000000]Hazarding a guess, I would say my new (6mths or less) external HDD is the guilty NTFS file system. So somehow I will have to find space for everything that’s on there and format that to ext4. What a rookie mistake that was.
[/COLOR]
> **TheFu said:**
>  
[COLOR=#000000]
The output from [/COLOR]**[COLOR=#000000]df -hT[/COLOR]**[COLOR=#000000] will help us. For example, here's mine (with odd file systems remove):
[/COLOR]

[COLOR=#000000]Here’s the output. What are all those tmpfs outputs? Shouldn’t my swap partition be showing?[/COLOR]

```
df -hT
 [COLOR=#000000]Filesystem     Type      Size  Used Avail Use% Mounted on[/COLOR]
 [COLOR=#000000]udev           devtmpfs  1.9G     0  1.9G   0% /dev[/COLOR]
 [COLOR=#000000]tmpfs          tmpfs     384M  6.3M  378M   2% /run[/COLOR]
 [COLOR=#000000]/dev/sda1      ext4       92G   81G  6.5G  93% /[/COLOR]
 [COLOR=#000000]tmpfs          tmpfs     1.9G  233M  1.7G  13% /dev/shm[/COLOR]
 [COLOR=#000000]tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock[/COLOR]
 [COLOR=#000000]tmpfs          tmpfs     1.9G     0  1.9G   0% /sys/fs/cgroup[/COLOR]
 [COLOR=#000000]/dev/sda3      vfat      976M  3.5M  972M   1% /boot/efi[/COLOR]
 [COLOR=#000000]/dev/sda5      ext4      819G  147G  631G  19% /home[/COLOR]
 [COLOR=#000000]tmpfs          tmpfs     384M   64K  384M   1% /run/user/1000[/COLOR]
```

[COLOR=#000000]The lack of capacity in the / partition is quite concerning. Is it possible somewhere along the line the machine has started using / instead of /home and somehow messed up permissions that were previously working fine?[/COLOR]

[COLOR=#000000]I get the feeling you’re right TheFu and I should do a fresh install. There are two new but pertinent questions I have. [/COLOR]
[COLOR=#000000]#1 How do I make sure I get all directories and files that have associated permissions backed up?[/COLOR]
[COLOR=#000000]#2 Once backed up, how do I copy the backed up directories and files back to the fresh system without potentially running into the same type of permission issue at a later date again? I imagine the permissions will all be backed up too.[/COLOR]

---

### Post by TheFu on 2018-02-24
/ gets full if you load every GUI application you want and don't clean them up.  Normally, 25G is more than enough for the OS and applications.

Looks like /home/ is mounted on the old disk still and is still using ext4.
I can't tell what is going on.
I suspect you've been changing things along the way.  To solve this forever, learn Unix permissions well. This stuff is easy and makes perfect sense, once you spend the time to play with 3 user accounts, in 3 different terminals, with 3 different groups that are mixed and matched with different userids in each.  Go into a temporary directory structure and play around with owners, groups, permissions. See what works, what doesn't, and HOW the permissions and groups allow or prevent access.  Make a directory 711 ... what does that do?

I don't see sdb (a new disk).  If you use a GUI to mount it, just know that those are often "fake mounts" and don't show up in the OS AND have poor performance.  I only use REAL mounts for permanent storage ... that's either /etc/fstab or using autofs.  I've been burned by point-n-click mounts too many times to bother with it anymore.

As for what is using all the space on / ... I don't know. I'm cautious to keep media files on network storage (I use NFS), never local, except for during travel.  That's my method to keep huge files out of my systems.  So I can look for any files over 500MB in size and know those aren't anything I need on a system.  Usually, those are left over from the last trip (and I didn't watch anything) just waiting to be deleted.

My "hogs" script:
```
$ more bin/hogs 
#!/bin/sh

find . -type f -size +500M -exec ls -lh {} \;
```
Actually just ran it ... and found an old recording of Raw Travel (a TV show) in my HOME. ;)
Ran it on a temp partition, mounted just for temp stuff and found an Ubuntu ISO and OpenSense ISO. ;)  It is good to clean things up.  Beware that the size specifier has some unexpected behaviors based on the K/M/G/T suffix. Best to read the manpage on that. It is weird.

As for using a /home on sda ... Linux is very flexible. You can make your HOME anywhere you like.  It doesn't **have** to be in /home/{userid}.  That is just commonly used for small sites or people in their houses/apartments.  In a work environment, let's just say that things are VERY different.

---

### Post by MibunoOokami on 2018-02-25
[COLOR=#000000]> **TheFu said:**
> / gets full if you load every GUI application you want and don't clean them up. Normally, 25G is more than enough for the OS and applications.[/COLOR]
 
 [COLOR=#000000]How does one usually clean them up? I take it ```
sudo apt-get clean
``` ```
sudo apt-get autoclean
``` doesn’t take care of that.

> **TheFu said:**
> Looks like /home/ is mounted on the old disk still and is still using ext4.
I can't tell what is going on.[/COLOR]
 
 [COLOR=#000000]I wonder if my partition setup coupled with my explanation might be causing some confusion as I don’t quite understand what you’re trying to say here. Or I’m tired and not reading it properly. Either way I’ll try to clarify it.[/COLOR]
 
 [COLOR=#000000]Years ago now I was told it’s best to manually specify partitions. [/COLOR] 
 [COLOR=#000000]#1 The / partition should be at least 30GB, check to put grub onto sda, format as ext4 and set as logical partition. (since I have more space to spare, I made it bigger, 100GB)[/COLOR]
 [COLOR=#000000]#2  Swap partition, slightly bigger than RAM, specify as Linux Swap and set as logical partition.[/COLOR]
 [COLOR=#000000]#3 The remaining space specified to mount as /home formatted as ext4 and presumably as a primary partition.[/COLOR]
 [COLOR=#000000]#4 My machine also demanded a separate partition for efi.[/COLOR]
 
 [COLOR=#000000]During a recent backup of this machine to a new external drive I came across some files/directories that didn’t copy due to permission error 13. I tried to chown all files which didn't seem to work or possible made matters worse. I don’t recall formatting the new external backup drive as ext4 so is probably still ntfs.

> **TheFu said:**
> I don't see sdb (a new disk).[/COLOR]
 
 [COLOR=#000000]I didn’t have it plugged in at the time. New output below.[/COLOR]
 
 [COLOR=#000000]```
 df -hT
```[/COLOR]```

 [COLOR=#000000]Filesystem     Type      Size  Used Avail Use% Mounted on[/COLOR]
 [COLOR=#000000]udev           devtmpfs  1.9G     0  1.9G   0% /dev[/COLOR]
 [COLOR=#000000]tmpfs          tmpfs     384M  6.3M  377M   2% /run[/COLOR]
 [COLOR=#000000]/dev/sda1      ext4       92G   81G  6.5G  93% /[/COLOR]
 [COLOR=#000000]tmpfs          tmpfs     1.9G  212M  1.7G  12% /dev/shm[/COLOR]
 [COLOR=#000000]tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock[/COLOR]
 [COLOR=#000000]tmpfs          tmpfs     1.9G     0  1.9G   0% /sys/fs/cgroup[/COLOR]
 [COLOR=#000000]/dev/sda3      vfat      976M  3.5M  972M   1% /boot/efi[/COLOR]
 [COLOR=#000000]/dev/sda5      ext4      819G  147G  630G  19% /home[/COLOR]
 [COLOR=#000000]tmpfs          tmpfs     384M   76K  384M   1% /run/user/1000[/COLOR]
 [COLOR=#000000]/dev/sdc2      fuseblk   2.8T  334G  2.5T  12% /media/username/TOSHIBA EXT[/COLOR]
```[COLOR=#000000]
[/COLOR]
 [COLOR=#000000]> **TheFu said:**
> 
My "hogs" script:
```
$ more bin/hogs 
#!/bin/sh

find . -type f -size +500M -exec ls -lh {} \;
```[/COLOR]
 [COLOR=#000000]
[/COLOR][COLOR=#000000]I’m not sure how to set that script up. I copied and pasted it to a gedit file, set it as executable, placed it in my bin folder but when I tried to run it, nothing seems to have happened… [/COLOR][COLOR=#000000]

> **TheFu said:**
> As for using a /home on sda ... Linux is very flexible. You can make your HOME anywhere you like. It doesn't **have** to be in /home/{userid}.

Is my HOME in  /home/{userid}? [/COLOR][COLOR=#000000]I’m beginning to feel I know significantly less about Ubuntu than I had previously thought.[/COLOR]

---

### Post by TheFu on 2018-02-26
Lots of opinions follow. Other people will/could have VERY different ideas.  Get some inputs from others and consider what everyone says, then decide what is best for your needs.

If it isn't clear, using chown without understanding is VERY dangerous.  chown on your HOME shouldn't cause many issues provided it is converting all ownership to the userid for that HOME.  Doing chown outside of a HOME is extremely dangerous.  File ownership and permissions are the core for all system security on Linux/Unix systems. There are many, many, subtle considerations that aren't always clear.  Unix is multi-user, even if you aren't.

You can't put your HOME on a disk that isn't always connected. PERIOD.  USB for HOME is a bad idea.  I suspect you really don't want to use the external disk for HOME, just to add some extra storage for big files.

HOME is an environment variable set at login for each userid.  It is a special place.  /home is a directory and can be different from HOME, since it lacks the userid.  At least that is how I use those terms.

Make / larger than 25G is a bad idea, IMHO.  It makes backing up the OS harder.  Whereas backing up 25G or less is pretty easy, backing up 100G is much harder.  When I lay out storage, I see 4 places that need to be setup.
[LIST=1]
[*]/ - for the OS and applications
[*]/boot - for the boot setup - LVM and full disk encryption require a separate boot 
[*]/home - for personal files
[*]swap - 4.1G in size.  The old rules-of-thumb don't apply anymore. Do not use hibernation.
[/LIST]

You need to figure out what is eating all the storage in /.  If it is applications, then you need to remove some. But considering the entire OS mirrors are only 20G in size, I don't see how there can be more than that in /.  Amazing.

To get the script working, you'll need to gain a better understanding of the shell environment. I'm not a good teacher in this environment.  Search for "beginning bash scripting" for a guide hosted on TLDP site.  There's also a good, free, PDF book that you can read to fill in some of the missing parts in skills.  Everyone has missing knowledge. I'm weak on GUI methods, for example.   [http://blog.jdpfu.com/2017/03/31/learning-linux-condensed](http://blog.jdpfu.com/2017/03/31/learning-linux-condensed) has the book link. The book is published and available at all book stores if you prefer paper.

Using fuse to mount file systems is slow for disk performance, BTW.  So, if you want to move the external disk between systems, then ext4 might not be the best choice, unless those systems are all Unix-based.   If you need to share it with Windows, then only use it for data files, not programs and not for /home.

---

### Post by #&amp;thj^% on 2018-02-26
I agree with TheFu in regards to You need to figure out what is eating all the storage in /
And if your unsure about what's in that location:
```
cd /
```
And 
```
ls
```
Will give you the Listed Folders/Files that reside there. And a more detailed view would be of course:
```
ls -la
```
My system is rather basic and looks like:
```
cd / && ls
bin   dev  home  lib64       media  opt   root  sbin  sys  usr
boot  etc  lib   lost+found  mnt    proc  run   srv   tmp  var

```
With a little more detail:
```
cd / && ls -la
total 64
drwxr-xr-x  18 root root  4096 Feb  1 11:08 .
drwxr-xr-x  18 root root  4096 Feb  1 11:08 ..
lrwxrwxrwx   1 root root     7 Oct 17 01:32 bin -> usr/bin
drwxr-xr-x   6 root root  4096 Feb 24 11:06 boot
drwxr-xr-x  21 root root  3560 Feb 26 04:05 dev
drwxr-xr-x  85 root root  4096 Feb 26 07:00 etc
drwxr-xr-x   3 root root  4096 Feb 12 13:17 home
lrwxrwxrwx   1 root root     7 Oct 17 01:32 lib -> usr/lib
lrwxrwxrwx   1 root root     7 Oct 17 01:32 lib64 -> usr/lib
drwx------   2 root root 16384 Feb 12 13:15 lost+found
drwxr-xr-x  28 root root  4096 Feb 26 01:45 media
drwxr-xr-x   2 root root  4096 Oct 17 01:32 mnt
drwxr-xr-x   4 root root  4096 Feb 12 18:51 opt
dr-xr-xr-x 198 root root     0 Feb 26 04:05 proc
drwx------  12 me   me    4096 Feb 12 14:28 root
drwxr-xr-x  26 root root   680 Feb 26 06:07 run
lrwxrwxrwx   1 root root     7 Oct 17 01:32 sbin -> usr/bin
drwxr-xr-x   4 root root  4096 Feb  1 10:55 srv
dr-xr-xr-x  13 root root     0 Feb 26 04:05 sys
drwxrwxrwt  11 root root   260 Feb 26 06:57 tmp
drwxr-xr-x   9 root root  4096 Feb 26 07:00 usr
drwxr-xr-x  12 root root  4096 Feb 26 04:05 var

```
NOTE: My Partition Scheme is different than yours. (But that dose not matter here)
I have used this way for many years now and it just fits my needs.
```
df -hT
Filesystem     Type      Size  Used Avail Use% Mounted on
dev            devtmpfs  5.9G     0  5.9G   0% /dev
run            tmpfs     5.9G  9.2M  5.9G   1% /run
/dev/sda3      ext4      455G   37G  395G   9% /
tmpfs          tmpfs     5.9G     0  5.9G   0% /dev/shm
tmpfs          tmpfs     5.9G     0  5.9G   0% /sys/fs/cgroup
tmpfs          tmpfs     5.9G   16K  5.9G   1% /tmp
tmpfs          tmpfs     1.2G   28K  1.2G   1% /run/user/1001

```
Others may have more thoughts or suggestions also. (We have some very talented folks here in UF)

---

### Post by TheFu on 2018-02-26
du, ncdu, my 'hogs' script and there are 50,000 other ways to find where storage is being used.

---

### Post by MibunoOokami on 2018-02-26
@1fallen: below are the outputs from those commands.
 
 
 @TheFu: out of the 50,000 other ways, I did it the old fashioned way of clicking on the properties of each directory in root. ](*,)

 I didn’t realise there is a HOME and a /home…  
 
 
 ```
/$ ls
 bin    dev   initrd.img      lib64       mnt   root  snap  tmp  vmlinuz
 boot   etc   initrd.img.old  lost+found  opt   run   srv   usr  vmlinuz.old
 cdrom  home  lib             media       proc  sbin  sys   var
```
 
 
 ```
/$ ls -la
 total 108
 drwxr-xr-x  24 root root  4096 Feb 23 12:41 .
 drwxr-xr-x  24 root root  4096 Feb 23 12:41 ..
 drwxr-xr-x   2 root root  4096 Feb 17 06:24 bin
 drwxr-xr-x   4 root root  4096 Feb 24 20:00 boot
 drwxr-xr-x   2 root root  4096 Dec 24 08:25 cdrom
 drwxr-xr-x  20 root root  4280 Feb 27 06:49 dev
 drwxr-xr-x 137 root root 12288 Feb 26 16:22 etc
 drwxr-xr-x   6 root root  4096 Dec 24 16:56 home
 lrwxrwxrwx   1 root root    33 Feb 23 12:41 initrd.img -> boot/initrd.img-4.13.0-36-generic
 lrwxrwxrwx   1 root root    33 Jan 27 08:13 initrd.img.old -> boot/initrd.img-4.13.0-32-generic
 drwxr-xr-x  23 root root  4096 Jan 18 06:52 lib
 drwxr-xr-x   2 root root  4096 Jan 18 06:52 lib64
 drwx------   2 root root 16384 Dec 24 08:18 lost+found
 drwxr-xr-x   7 root root  4096 Feb 26 17:11 media
 drwxr-xr-x   2 root root  4096 Aug  1  2017 mnt
 drwxr-xr-x   3 root root  4096 Dec 24 09:50 opt
 dr-xr-xr-x 210 root root     0 Feb 27 06:49 proc
 drwx------  12 root root  4096 Feb 22 15:21 root
 drwxr-xr-x  27 root root   840 Feb 27 06:54 run
 drwxr-xr-x   2 root root 12288 Feb 24 20:00 sbin
 drwxr-xr-x   2 root root  4096 Apr 29  2017 snap
 drwxr-xr-x   2 root root  4096 Aug  1  2017 srv
 dr-xr-xr-x  13 root root     0 Feb 27 06:49 sys
 drwxrwxrwt  15 root root  4096 Feb 27 06:58 tmp
 drwxr-xr-x  11 root root  4096 Aug  1  2017 usr
 drwxr-xr-x  14 root root  4096 Aug  1  2017 var
 lrwxrwxrwx   1 root root    30 Feb 23 12:41 vmlinuz -> boot/vmlinuz-4.13.0-36-generic
 lrwxrwxrwx   1 root root    30 Jan 27 08:13 vmlinuz.old -> boot/vmlinuz-4.13.0-32-generic
```

---

### Post by MibunoOokami on 2018-02-26
When my wife was logged on to the computer today, I noticed a little icon on the desktop which I haven’t paid attention to before until I saw an interesting figure of 92%. 
Please see the screenshot. I believe this icon belongs to Cairo-dock, but can’t tell you why it’s on my wife’s desktop.

 Could this be related to, or the root of my full / problem? (pun intended)

[ATTACH=CONFIG]278679[/ATTACH]

---

### Post by TheFu on 2018-02-28
Use ncdu to find the largest files.
Decide what you want to do with each - delete or move somewhere else.
Being aware of the issue AND proving what is causing it are important.

---

### Post by MibunoOokami on 2018-03-01
> **TheFu said:**
> Use ncdu to find the largest files.
Decide what you want to do with each - delete or move somewhere else.
Being aware of the issue AND proving what is causing it are important.

Below is the output of ncdu, am I to understand these directories are somehow being stored in /? It doesn't look out of the ordinary to me is why I'm asking. Thanks

```
   14.8 GiB [######    ] /Desktop
    8.5 GiB [###       ] /Downloads
    3.3 GiB [#         ] /.thunderbird
    2.7 GiB [#         ] /Music
    1.6 GiB [          ] /Documents
    1.5 GiB [          ] /.cache
And pictures at 25GiB (won't let me cut and paste)

```

---

### Post by #&amp;thj^% on 2018-03-01
Did you try to use the arrow key to navigate to any shown directory or file?
```
--- /home/me/Pictures ----------------------------------------------------------
                         /..                                                    
   85.5 MiB [##########] /Walls
   29.0 MiB [###       ] /Screenshots
    2.3 MiB [          ]  déconnexion-cables-ante...wifi-wlan-wii-u-gamepad.jpg
  964.0 KiB [          ]  bluedandelion.jpg
  272.0 KiB [          ]  fs1.png
   64.0 KiB [          ]  Help Avatar.png
   56.0 KiB [          ]  pv.png
   16.0 KiB [          ]  face.jpg
   12.0 KiB [          ]  fallen.png
   12.0 KiB [          ]  face.svg
    4.0 KiB [          ]  fs2.png

```
And I see where "/dev/sda1 ext4  92G   81G  6.5G  93% /" >>>not enough headroom to operate.

**TheFu's way is more suited (easier) for users to understand visually. **
So as not to add more confusion **_(purely informational only)_**, Here is another of the 50,000 ways. (Just another option)
I just use a combination of du and sort.

With this example the "2>/dev/null" will remove errors that show:
```
sudo du -sx /* 2>/dev/null | sort -n
```
This will show any error messages,  and this dose not bother me.
```
sudo du -sx /* | sort -n
```
To show you the difference between the two:
```
sudo du -sx /* 2>/dev/null | sort -n
[sudo] password for me: 
0	/bin
0	/dev
0	/lib
0	/lib64
0	/proc
0	/sbin
0	/sys
4	/mnt
4	/tmp
12	/srv
16	/lost+found
116	/media
1264	/root
22484	/etc
42124	/run
81820	/opt
118576	/boot
2018800	/var
9782548	/usr
26026564	/home

```
No shown errors.
Now:
```
sudo du -sx /* | sort -n
[sudo] password for me: 
du: cannot access '/proc/8745/task/8745/fd/4': No such file or directory
du: cannot access '/proc/8745/task/8745/fdinfo/4': No such file or directory
du: cannot access '/proc/8745/fd/4': No such file or directory
du: cannot access '/proc/8745/fdinfo/4': No such file or directory
0	/bin
0	/dev
0	/lib
0	/lib64
0	/proc
0	/sbin
0	/sys
4	/mnt
4	/tmp
12	/srv
16	/lost+found
116	/media
1264	/root
22484	/etc
42116	/run
81820	/opt
118576	/boot
2018800	/var
9782548	/usr
26025980	/home

```
And I see in my case that my /usr and /home is the bigger or larger directories in this example.

Target the subdirectories you think are too big, run the command for them and you'll find out what's in them the problem. (Rinse and repeat as needed)

Note Here: I use **"du's -x flag"** to keep things limited to one filesystem (I have quite a complicated arrangement of cross-mounted things between SSD and other Drives).

Note 2: **"2>/dev/null"** redirects any error messages into oblivion. If they don't bother you, it's not obligatory. (As I have shown in my examples above)

---

### Post by MibunoOokami on 2018-03-01
> **1fallen said:**
> Did you try to use the arrow key to navigate to any shown directory or file?

I hadn't at the time but have just now. I can't really afford to get rid of any of the files of any decent size. That is unless of course ncdu is showing the contents of / then I should be able to copy everything to /~ (IIRC this is home) and isolate/eliminate any further unnecessary space being used on /.

Forgive me if I have overlooked an answer already provided, if my /~ directory is 600GB or so with about 450GB free, why would my machine be chewing through the / directory? Is it just using space for the sake of it since it's there? That's kind of what I was picking up from TheFu. Thanks.

This is probably waaaaay over my head but it's good learning

---

### Post by TheFu on 2018-03-01
```
cd /
sudo ncdu
```
sudo is needed for ncdu to read files and directories not owned, readable, by your userid. When running in your HOME directory, no sudo should be needed.  ncdu is an information program.  
To move things, you'll need to use something else and then I suspect you are still back at the permissions issue.  We never learned here if you solved the HOME directory permissions problem. Is that solved or not?

It shows the storage used by each directory from that point down. Sorry, I thought that was clear. I'm bad at assuming things are clear.

/~ isn't HOME. ~/ is HOME.  Details matter, greatly.  Every login/userid probably has a different HOME ... that is usually ~username/ or /home/username/ or ~/ for the currently logged in username/userid.  To see the current HOME, open a terminal and type **env |grep HOME**.  You can also use **getent passwd {userid}** to see what HOME will be set for any other {userid} on the system.  BTW, it is best if userids are all lower-case for a number of reasons.  So, to be EXTREMELY clear, **getent passwd root** will show that /root is the HOME directory for the root, userid.  It is the 2nd to last field, : separated.

But ... we found that your HOME isn't on the external disk already, correct?
We found that you don't always connect the external disk, so really can't use that for HOME for any userid.  Sometimes connected disks can only be used for data.

I suspect you are getting tripped up on relative and absolute directory paths.  Windows-centric people often do in the beginning.  The link provided has a link in it to a free, no-hassle, PDF file which explains directories structures.  I can't tell if you are stuck on that skill or not.  Cannot tell if you are stuck on finding the huge files on the system or not.  It appears you've been reading and gaining some knowledge.

---

### Post by MibunoOokami on 2018-03-01
> **TheFu said:**
> ```
cd /
sudo ncdu
```
sudo is needed for ncdu to read files and directories not owned, readable, by your userid. When running in your HOME directory, no sudo should be needed. ncdu is an information program. 

That makes sense, I didn’t even think about it. Running that, I found the offender in /, it’s a virtualbox which I could swear I removed and/or purged when I couldn’t get it to work. I’ll Google a way to permanently remove all traces of that because I don’t need it. Thanks.

> **TheFu said:**
> To move things, you'll need to use something else and then I suspect you are still back at the permissions issue. We never learned here if you solved the HOME directory permissions problem. Is that solved or not?

Moving is no longer an issue based on the above explanation. Permission issues are still persisting.

> **TheFu said:**
> It shows the storage used by each directory from that point down. Sorry, I thought that was clear. I'm bad at assuming things are clear.

To be honest, it’s probably just my lack of understanding rather than you not making things clear. I have a hands on type learning style. As in let me see you doing something as you’re explaining, then let me give it a go and correct me if I screw up. So I’m really slow at learning from reading and often Youtubers just don’t have the knack for keeping the attention of their audiences.

> **TheFu said:**
> /~ isn't HOME. ~/ is HOME. Details matter, greatly. Every login/userid probably has a different HOME ... that is usually ~username/ or /home/username/ or ~/ for the currently logged in username/userid. 

That’s my bad, I was going off the top of my head when I inverted ~/ with /~

> **TheFu said:**
> But ... we found that your HOME isn't on the external disk already, correct?
We found that you don't always connect the external disk, so really can't use that for HOME for any userid.

That is correct. I only connect the external disk once a week or so to back things up.

> **TheFu said:**
> I suspect you are getting tripped up on relative and absolute directory paths. Windows-centric people often do in the beginning. The link provided has a link in it to a free, no-hassle, PDF file which explains directories structures. I can't tell if you are stuck on that skill or not. Cannot tell if you are stuck on finding the huge files on the system or not. It appears you've been reading and gaining some knowledge.

Is that the link you posted in post #20? That page won’t load for me, keeps timing out. 

Apologies for the dozens of quotes, I like to answer each thing separately to keep things simple. 

Thanks.

---

### Post by MibunoOokami on 2018-03-02
See [this thread]("https://ubuntuforums.org/showthread.php?t=2386194&p=13744711#post13744711") re my Virtualbox

ETA: df -hT looks significantly better now.

```
 df -hT
Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  1.9G     0  1.9G   0% /dev
tmpfs          tmpfs     384M  6.3M  377M   2% /run
/dev/sda1      ext4       92G  5.4G   82G   7% /
tmpfs          tmpfs     1.9G  252M  1.7G  14% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs     1.9G     0  1.9G   0% /sys/fs/cgroup
/dev/sda3      vfat      976M  3.5M  972M   1% /boot/efi
/dev/sda5      ext4      819G  149G  628G  20% /home
tmpfs          tmpfs     384M   72K  384M   1% /run/user/1000


```

---

### Post by TheFu on 2018-03-02
```
/dev/sda1      ext4       92G  5.4G   82G   7% /
```
Yep, much better.  So it was something YOU did, not the system.  That is usually the situation with things like this, BTW.  We are our own worst enemy.  BTW, you are not alone on this.  I've done some foolish things over the year on my knowledge quest. ;)

Depending on what and how you backup, using an NTFS file system might be a bad idea.  For most end-users, something like **aptik** is a tool for backups. I think it requires a Linux file system to retain ownership, users, and permissions, but the manpage will be clear on that.  I use something different.

I like to learn by seeing/doing too.  But many short things that are considered basic knowledge will only be well-learned by reading.  The basic use to too simple to be in a video, but it is the non-basic use that has all the power.  I fear permissions are like that.

If the link is timing out, ... there are probably 1 of 2 problems.
[LIST=1]
[*]The system is down for backups - at most 2 minutes every 24 hours. Try again.
[*]Your source IP is from a part of the world that has attempted to hack the server, so it is on a block list.
[/LIST]
Backups for that machine last night were quick:
```
=== Time for Backups to blog.jdpfu.com === 
StartTime 1519973711.00 (Fri Mar  2 01:55:11 2018)
EndTime 1519973754.27 (Fri Mar  2 01:55:54 2018)
ElapsedTime 43.27 (43.27 seconds)
TotalDestinationSizeChange 691515 (675 KB)
```

Both can be solved by using google-cache or by using the Wayback machine. Webpages disappear all the time, but those two tools keep a copy around much longer. [https://web.archive.org/web/20180302111809/http://blog.jdpfu.com/2017/03/31/learning-linux-condensed](https://web.archive.org/web/20180302111809/http://blog.jdpfu.com/2017/03/31/learning-linux-condensed) has it.

You'll really want to fix the HOME permissions issues ASAP.

---

### Post by MibunoOokami on 2018-03-03
> **leunam12 said:**
> Are you rsyncing to an NTFS drive? I used to get errors with rsync when doing home backups until I formatted the backup drive to EXT4. Also I use sudo. Like this```
sudo rsync -aAXv /source/ /destination/
```

 Going back through all the responses to see if I missed anything really paid off with the above response. I tried using sudo a number of times but it would throw up a message telling me the command is not found. That’s because I had been using sudo with my script command. Upon opening my script and adding sudo before rsync as stated above, all permission messages have vanished.   
 
 I’m a bit disappointed with myself because I had even replied to Leunam12’s question about rsyncing to an NTFS drive.
 
 @Leunam12 Thanks for the tip, it’s a shame I didn’t pay close enough attention.
 
 @TheFu, I’ll look into aptik. NZ must be blacklisted because the site is still timing out. The archive link you provided throws out ```
Got an HTTP 302 response at crawl time
``` but it does give a download button for The Linux Command Line PDF which I’ve clicked about a dozen times and nothing happens. I did manage to download a copy (of The Linux Command Line) to my cellphone from elsewhere though. So I'll definitely give that a read.
 
 Thank you everyone

---

