---
title: "Apache on Ubuntu - Help with simple settings please"
date: 2013-12-06
forum: General Help
---

### Post by p.callan on 2013-12-06
I have switched from WAMP on WinXP to LAMP on ubuntu 12.04 LTS but can't get it to work properly. I have an external hdd connected to my server (Lenovo S10e) with all my media on, and these mediafiles are linked from my website which is hosted on weebly.com. I have no html, php or other files on the server. I need to set it up as it was on WinXP so that I don't have to edit thousands of links on my website. I need to know:

- Which file do I edit to specify the ext hdd as the root of the server (instead of the www dir) (Using Apache 2.2.22).
- How do I denote this path? The name of the hdd is simply M for media. Is the path then /media/M/ ?
- Do I need to configure a firewall on the server? How?

I have only been using ubuntu two days so I'd rather stay away from the terminal and unnecessary complications that I don't understand. I am learning through the Getting started with ubuntu manual, but I need the server up and running ASAP.

Thanks for helping a noob out.

---

### Post by Iowan on 2013-12-06
Thread began [here]("http://ubuntuforums.org/showthread.php?t=2179905").
Additional information available there.

---

### Post by p.callan on 2013-12-07
Ok, I have now figured out and done the following:

- The httpd.conf is not used at all on Ubuntu. It's there, as someone put it, "for historical reasons" (to confuse newbies). Anyway it is blank.
- I have set the apache2.conf file to /etc/apache2 which is the install path.
- I have edited the root directory in the default-file in /sites-available/ and set it to "/media/M" without a slash at the end.
- When testing a link from my site to a pdf-document on the server, I get a 403:Forbidden error. Guessing I need to open port 80, 8080 and 21 on the server...
- Downloaded and added the ports in the app "Firewall configuration", but this still gets me a 403:Forbidden error.
- Oh, and I haven't changed anything in the router (i.e port forwarding) since this should stay the same.
- Tried to find help from the apache community but they use IRC that I have never used and is another nightmare to setup on an OS I hardly know.

This is now the third day of pulling my hair out over this, so I tried to revert back to WinXP, but for some reason WAMP doesn't work anymore. So now the site is offline and I don't know what to do...

---

### Post by Lars Noodén on 2013-12-07
If you're getting a "403" error then you are getting through to the server but maybe index.html is missing or the directory+file is not readable by the web server.

By the way:

The default for Apache2 on Ubuntu is to come with one pre-configured virtual host.  You can find the settings for that virtual host in [s]/etc/apache2/sites-enabled/000-default.conf[/s] /etc/apache2/sites-enabled/000-default  If you have to make any changes do it to that file only, also you need to restart the web server (not your whole box) like this for the changes to take effect:

```

sudo service apache2 restart

```

The default place for your web pages in that first vhost is /var/www  You'll need to have index.html there, if nothing else.  If you're the only user on that machine then you can get write access by taking ownership of the web directory.

```

sudo chown -R p.callan /var/www

```

If you are sharing with other users on the same machine who need access, then you can use group permissions instead.  

If you want to check the configuration file for correct syntax, then you can do it this way:

```

apache2ctl configtest

```

---

### Post by steeldriver on 2013-12-07
This is NOT my area of expertise but I set up a 'play' server some time ago with default document root /data/mysite. As far as I recall the steps were


[LIST=1]
[*]edit the /etc/apache2/**sites-available**/default file (NOT the sites-enabled file), changing the path in TWO places 
[/LIST]
[INDENT]```

$ head -15 /etc/apache2/sites-available/default
<VirtualHost *:80>
    ServerAdmin webmaster@localhost

    **DocumentRoot /data/mysite**
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    **<Directory /data/mysite>**
        Options Indexes FollowSymLinks MultiViews
        AllowOverride None
        Order allow,deny
        allow from all
    </Directory>

```
2. run **a2ensite **(*a*vailable-to-*en*abled) to create the appropriate symlink in /etc/apache2/sites-enabled
[/INDENT]

I don't recall having to do anything with the apache2.conf file. Once you restart the apache2 service, test it on the localhost interface to rule out any issues about ports / firewalls - if you don't have a browser on the localhost (e.g. if it is a non-GUI server) you can use wget

```

$ sudo service apache2 restart
 ... waiting  * Restarting web server apache2                           [ OK ] 
$ 
$ wget -O- http://localhost | html2text

```

---

### Post by p.callan on 2013-12-07
Ok, thanks for the reply.
I did the following

[I]sudo -s
nano /etc/apache2/sites-enabled/000-default.conf[/I]

But the file is blank. I'm very shaky on using the terminal, I don't speak the language so to speak =)
Also, I have no html-files on the server. It is only used for media files. But there are 2 autogenerated files in /var/www/, index.html and testphp.php.
Are the other paths that I mentioned above correct now? I should have written them down on paper before I changed them...

*"If you're the only user on that machine then you can get write access by taking ownership of the web directory."*
I am the only user, but I don't understand what you mean by ownership or syntax. I just need to change the /var/www/ to my hdd path... At least that's what I did on the Windows version.

Thanks for helping me!

---

### Post by Lars Noodén on 2013-12-07
That configuration file should not be empty.  Something is not quite right.  Can you check the contents of the sites-enabled directory?

```

$ ls -lh /etc/apache2/sites-enabled/
total 0
lrwxrwxrwx 1 root root 26 Dec  7 16:39 000-default -> ../sites-available/default

```

It should look like the above with the symlink that steeldriver mentioned.  If the directory is empty or the file 000-default does not exist, then enable the site:

```

sudo a2ensite default

```

If the file exists but is not a symlink, then it has to be moved out of the way before enabling the site.  The -> indicates that it is a symlink or not.

---

### Post by p.callan on 2013-12-07
Steeldriver: Thanks so much for your reply.

*"edit the /etc/apache2/**sites-available**/default file (NOT the sites-enabled file), changing the path in TWO places"*
Ok, they are now set to /media/M
(The drive letter in WinXP is D, does this matter in ubuntu? The name I've given it is M, however)

*"2. run **a2ensite **(available-to-enabled) to create the appropriate symlink in /etc/apache2/sites-enabled"*
Ok, but how do I do that exactly? Just type a2ensite in the terminal?

Localhost in the browser gives the same 403:Forbidden message...

---

### Post by Lars Noodén on 2013-12-07
If /etc/apache2/sites-available/default is set up correctly, then you would just run a2ensite in the terminal.  If you specify a site (e.g. default) then it will load that one.  If not you get to choose from the ones available.  

What do you have for DocumentRoot in the /etc/apache2/sites-available/default file?

---

### Post by p.callan on 2013-12-07
Ok this is confusing. The 000-default.conf is blank when I open it in nano through the terminal but not when I doubleclick on the icon. 

DocumentRoot in **sites-available** is /media/M as well as <Directory /media/M>
DocumentRoot in **sites-enabled** is /media/M as well as <Directory /media/M>

When I type 
$ ls -lh /etc/apache2/sites-enabled/

it says command not found.
edit: sorry, I wrote the dollarsign too. It says:
total 0
lrwxrwrwx 1 root root 26 dec 6 00:24 <cyan>000-default</cyan> -> --/sites-available/default

(tags added)

---

### Post by Lars Noodén on 2013-12-07
The above was both what I typed and the output from the machine so I included the system prompt.  The $ is a convention to indicate the prompt for a regular user  account.  Try the same line without the $ and it will work.  You'll see the $ a lot in tutorials as well as # which, depending on context, means the root account or a comment.

---

### Post by Lars Noodén on 2013-12-07
> **p.callan said:**
> Ok this is confusing. The 000-default.conf is blank when I open it in nano through the terminal but not when I doubleclick on the icon. 

DocumentRoot in **sites-available** is /media/M as well as <Directory /media/M>
DocumentRoot in **sites-enabled** is /media/M as well as <Directory /media/M>


Steeldriver caught the typo I made  in the filename and I've corrected it above.  The file name should be without the .conf:

/etc/apache2/sites-enabled/000-default

in the one directory and in the other it should be 

/etc/apache2/sites-available/default

---

### Post by Lars Noodén on 2013-12-07
> **p.callan said:**
> 
DocumentRoot in **sites-available** is /media/M as well as <Directory /media/M>
DocumentRoot in **sites-enabled** is /media/M as well as <Directory /media/M>

Ok.  This helps.  We should check permissions for /media and /media/M and, if it exists, for /media/M/index.html

The following will print out the permissions, it's more concise than using ls and sorting through the extra output.  

```

stat -c "%A" /media
stat -c "%A" /media/M
stat -c "%A" /media/M/index.html

```

---

### Post by p.callan on 2013-12-07
Yes, I'm sorry for the confusion. The following is it:


DocumentRoot in **sites-available** (filename: **default**) is **/media/M** as well as **<Directory /media/M>**
DocumentRoot in **sites-enabled** (filename: **000-default**) is **/media/M** as well as **<Directory /media/M>**

Also, when I open these  (or any other files) through the terminal and nano, I do it as root because otherwise I cannot save changes.

stat -c "%A" /media
drwxr-xr-x

stat -c "%A" /media/M
drwx------

stat -c "%A" /media/M/index.html
stat: cannot stat '/media/M/index.html': No such file or directory.

**Added known-to-exist file:**
stat -c "%A" /media/M/index.php
-rw-----

---

### Post by Lars Noodén on 2013-12-07
Ok.  That looks like the source of the problem.  The web server needs read [permissions](https://help.ubuntu.com/community/FilePermissions) to everything you are going to publish.  You can set them with chmod

```

sudo chmod 755 /media/M
sudo chmod 644 /media/M/*

```

I'm rusty on PHP, we might have to add [DirectoryIndex](http://httpd.apache.org/docs/2.4/mod/mod_dir.html#directoryindex) to the configuration.  But try setting the permissions first.

---

### Post by p.callan on 2013-12-07
Ok did that. Terminal did not return any reply.

I don't use php so that's fine. It's some file I don't know (Probably added by WAMP when I had it on WinXP. The language used in the file is french for some reason. I'm Swedish, so...)

---

### Post by Lars Noodén on 2013-12-07
The traditional UNIX utilities don't say anything when they work.  It's expected that they work and would only say something if they fail in some way. 

Can you reload the web page now in the web browser and see the directory, since the index.html file is missing?  

As an afterthought, is /media/M formatted as EXT or NTFS?  The latter will give problems and requires special handling.

---

### Post by p.callan on 2013-12-07
*Can you reload the web page now in the web browser and see the directory, since the index.html file is missing?*
Still 403.

*As an afterthought, is /media/M formatted as EXT or NTFS?  The latter will give problems and requires special handling.*
Hmm I don't know, it doesn't say in properties or on the sticker... How do I find out?

---

### Post by Lars Noodén on 2013-12-07
You can see what file systems you have with [mount](http://manpages.ubuntu.com/manpages/saucy/en/man8/mount.8.html)

```

mount

```

or the short output version:

```

mount | grep /media/M

```

It will tell you something like this, if it is a normal format:

/dev/sda2 on / type ext4 (rw,errors=remount-ro)

If it says NTFS then there are some changes that have to be made to the fstab entry.

---

### Post by p.callan on 2013-12-07
[FONT=verdana][I]mount
...
/dev/sdb1 on /media/M type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)

mount | grep /media/M
/dev/sdb1 on [COLOR=#FF0000]/media/M [/COLOR]type fuseblk[/I] *(rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)*[/FONT]

---

### Post by Lars Noodén on 2013-12-07
I've not seen that kind of mount before, maybe it is a Windows-formatted drive?

What does /etc/fstab have to say?

```

grep /media/M /etc/fstab

```

That should show the mount options, too.

---

### Post by p.callan on 2013-12-07
$ grep /media/M /etc/fstab
$

(i.e no reply)...

---

### Post by Lars Noodén on 2013-12-07
The lack of an fstab entry is normal for removable drives.   I know that you need to somehow mount it with the options dmask=022 and fmask=033 but not how to get there from here.  I haven't used fuse much or ntfs at all.  All my external drives have been EXT, HFS+ or FFS. 

What's happening is that the drive is getting mounted with permissions that are fine for personal use, but additional read permissions are needed for web use.  Since chmod did not work, and the drive works with XP, it is probably in NTFS format.  

Maybe someone who has used NTFS will spot this thread.

---

### Post by p.callan on 2013-12-07
Ok, maybe I can format it... I'll have to dig up some temporary storage space somewhere and hope there are no files >4gb.

I found something when running apache2ctl configtest and it returned an error: 

*87: ulimit: error setting limit (Operation not permitted) apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName.*

This means that in some file 127.0.1.1 should be 127.0.0.1 instead, right??


Note:
I haven't a clue what you're talking about when it comes to
"dmask=022 and fmask=033". Won't "try this at home" =)

---

### Post by steeldriver on 2013-12-07
I think the 'fuseblk' type is what you see when the drive is auto mounted as "removable media" via udisks - you probably don't want to do that (unless you want a removable website ;) )

OTOH if you permanently mount the drive via /etc/fstab you should probably choose a mountpoint somewhere other than /media - since udisks can get confused if it finds devices there that it's *not* managing. Probably the 'right' mountpoint would be somewhere like /srv

---

### Post by Lars Noodén on 2013-12-07
Reformatting is probably not necessary.  It just needs the "right" mount options.  You can list the partitions on /dev/sdb with parted 

```

sudo parted -l /dev/sdb

```

That might give more data.

---

### Post by p.callan on 2013-12-07
kay... That was mostly greek to me...
Maybe I should just try to get it to work on windows again.
Ubuntu was recommended to me by loads of people but it's just too complicated for me... If I wasn't under the pressure of time, then it'd be a different story.

---

### Post by Lars Noodén on 2013-12-07
Sorry.  I've made it complicated.  I saw Apache in the heading and it turns out to be a question of mount options for an external drive.  If you ask in another thread about setting the permissions for an external drive, you might get easier help.

---

### Post by p.callan on 2013-12-07
user@computer:~$ sudo parted -l /dev/sdb
Model: ATA HITACHI HTS54321 (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  77.4GB  77.4GB  primary   ntfs         boot
 2      77.4GB  147GB   70.0GB  extended
 6      77.4GB  145GB   67.9GB  logical   ext4
 7      145GB   146GB   1054MB  logical
 5      146GB   147GB   1063MB  logical
 4      147GB   155GB   7881MB  primary
 3      155GB   160GB   4719MB  primary   ntfs         diag


Model: WDC WD10 EADS-00M2B0 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  1000GB  1000GB  primary  ntfs         boot


Model: Linux device-mapper (crypt) (dm)
Disk /dev/mapper/cryptswap1: 1054MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0.00B  1054MB  1054MB  linux-swap(v1)

---

### Post by Lars Noodén on 2013-12-07
Ok.  The output from parted shows that it is an ntfs drive.  

Here is one guess, I don't have an ntfs drive to  work with.  First we unmount the drive.  Then make sure the mount point (/media/M) is still there.  Then is a guess at mount options.

```

sudo umount /media/M
sudo mkdir /media/M
sudo mount -t ntfs-3g /dev/sdb1 /media/M -o uid=1000,gid=1000,utf8,dmask=022,fmask=133

```

---

### Post by p.callan on 2013-12-07
I'm doing something similar... [http://ubuntuforums.org/showthread.php?t=2192241](http://ubuntuforums.org/showthread.php?t=2192241)
As far as I can tell my ext hdd is always mounted as /media/M
but how do I set permissions to this NTFS drive to use it with Apache server, and _without losing the HotSwap_ functionality?

Please speak to me as if I had only used ubuntu for 3 days (which is literally true) and please, let's stay away from the terminal as I don't know what I am doing there.

If OP would like me to start my own T, then let me know.
Thanks.

---

### Post by howefield on 2013-12-07
Post merged into thread, please stop tacking you queries on to other posters threads. It really isn't the best way to get help.

Start a new thread in the appropriate forum if your query not suitable for this thread.

---

### Post by p.callan on 2013-12-07
@howefield:
Yeah, I was trying to avoid "Stop posting new threads, use the search function"-type of answers. + I don't even know what I need to do. It's like saying "you need to fix this flux capacitor thingamatron, but your questions must be asked in martian".
You know, my Ubuntu experience so far reminds me of a movie quote from Jurassic park: "Yeah... Oooh! Aaah! That's how it always starts. Then, later, there's running. And screaming."  :)


@Lars:
I got it working again on WinXP. So now, at least I have a fallback option. Phew.

[I]user@computer:~$ sudo umount /media/M
user@computer:~$ sudo mkdir /media/M
user@computer:~$ sudo mount -t ntfs-3g /dev/sdb1 /media/M -o uid=1000,utf8,dmask=022,fmask=133
ntfs-3g: Failed to access volume '/dev/sdb1': No such file or directory

ntfs-3g 2012.1.15AR.1 external FUSE 28 - Third Generation NTFS Driver
        Configuration type 7, XATTRS are on, POSIX ACLS are on

Copyright (C) 2005-2007 Yura Pakhuchiy
Copyright (C) 2006-2009 Szabolcs Szakacsits
Copyright (C) 2007-2011 Jean-Pierre Andre
Copyright (C) 2009 Erik Larsson

Usage:    ntfs-3g [-o option[,...]] <device|image_file> <mount_point>

Options:  ro (read-only mount), remove_hiberfile, uid=, gid=,
          umask=, fmask=, dmask=, streams_interface=.
          Please see the details in the manual (type: man ntfs-3g).

Example: ntfs-3g /dev/sda1 /mnt/windows

News, support and information:  [http://tuxera.com](http://tuxera.com)[/I]

Good news!  localhost now gives "index of /" on both the server and via another machine.
However when trying to access some of the files I have linked from the website, this gives a 404.
In /media/ there is now both an "M" folder (empty) and an "M_" folder which is the ext hdd.
Tried to change the /etc/apache2/sites-available/default to "DocumentRoot /media/M_" and <Directory /media/M_>  and restarted apache. But this did nothing, still 404.

---

### Post by Lars Noodén on 2013-12-07
I've used Gparted and made an NTFS partition on a spare drive and checked that the options "dmask=022,fmask=133" are what you need.  The 404 error probably is due to linking to files that the web server still cannot access.

---

### Post by p.callan on 2013-12-07
Lars, thank you SO much for taking the time with this. I really appreciate it. I'd be lost without you.

---

### Post by Lars Noodén on 2013-12-07
You're welcome.  It's kind of a puzzle.  For the time being, since we added /media/M manually it can be removed with rmdir if it's not being used.  That will allow Ubuntu to make it's own /media/M when you add the drive.  The question remains how to get the hotplug drive partition to pick up the two mount options automatically.

---

### Post by p.callan on 2013-12-08
Ok, I'll do whatever you say.
It's back running on Windows now, so no rush. I have Ubuntu on my main machine now also, so that lets me explore the fun stuff in the meantime.

---

### Post by Lars Noodén on 2013-12-08
I've formatted a thumb drive with NTFS and am able to duplicate the permissions with the hotplugged USB drive.  

The permissions problem doesn't / won't happen with normal file systems like EXT4.  However, if the external drive is reformatted to EXT4 (backing up and restoring the data from elsewhere in the process), then XP won't be able to read it.  If  that is not an issue, then EXT4 is an option.   

If XP is required, then NTFS is the only way.  Maybe there is a way to fix the hotplug permissions but not knowing how, the main option is to mount manually.  Unfortunately, NTFS bites again and requires root for mounting.  The other bad news is that  means the terminal again, the good news is that it is only one line each in two files.

---

### Post by bab1 on 2013-12-08
> **Lars Noodén said:**
> If XP is required, then NTFS is the only way.  Maybe there is a way to fix the hotplug permissions but not knowing how, the main option is to mount manually.  Unfortunately, NTFS bites again and requires root for mounting.  The other bad news is that  means the terminal again, the good news is that it is only one line each in two files.

There is a way of auto mounting an NTFS partition using the users defined permissions.  You have to make a udev rule that specifies the permissions.  First you should to develop the *mount* command in the terminal with the permissions you want.  Then you incorporate that with the *RUN+ *parameter in the udev rule.  See [here]("http://askubuntu.com/questions/54321/how-do-i-give-multiple-users-access-to-a-windows-ntfs-partition") for an example.

---

