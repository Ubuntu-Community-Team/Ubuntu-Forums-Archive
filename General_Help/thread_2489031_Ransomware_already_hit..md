---
title: "Ransomware already hit."
date: 2023-07-15
forum: General Help
---

### Post by josephchrzempiec on 2023-07-15
Hello, My ubuntu desktop server got hit by a Ransomware. I was using a desktop system as a nas. With no backup and back then no money for a second server. I know I know. It has the most hard drive space and was the only system I didn't use much. So I turned it into a desktop server in a way. Not knowing what I was doing back then I setup SMB share on my network. I never had security or protection on it. I never port forward to the ouside world And I'm always careful what I download, Somehow they got in. 

I didn't lose much. I can get 95% of it back and the rest is okay. Now I learned my lession I'm building a second system with the same hardware specs. So my question is what would be the best way to protect these system so Ransomware won't happen again and able to backup from one server to the other as it will be offsite? Thank you for any help.
 
Joseph

---

### Post by dragonfly41 on 2023-07-16
I now use Tresorit.com as a ZeroTrust data vault. But not ZeroCost.
There are other ways you will get from other contributors.

---

### Post by Rubi1200 on 2023-07-16
I recommend reading through the Ubuntu Security sticky page, lots of good information about security in general as well as about servers:
[https://ubuntuforums.org/showthread.php?t=510812](https://ubuntuforums.org/showthread.php?t=510812)

---

### Post by josephchrzempiec on 2023-07-17
> **Rubi1200 said:**
> I recommend reading through the Ubuntu Security sticky page, lots of good information about security in general as well as about servers:
[https://ubuntuforums.org/showthread.php?t=510812](https://ubuntuforums.org/showthread.php?t=510812)


Thank you I will do that. Lately it has been one problem after another with my health. Now this happen it's been crazy.

---

### Post by josephchrzempiec on 2023-07-17
> **dragonfly41 said:**
> I now use Tresorit.com as a ZeroTrust data vault. But not ZeroCost.
There are other ways you will get from other contributors.


I will look into them as well. Thank you.

---

### Post by MAFoElffen on 2023-07-17
I, well that was part of my job to protect against...

And it was your server...

Linux Servers are considered less vulnerable of other types of Operating System's servers. But things has changed a but in what that risk is. last year saw a 75% increase in ransomware attacks that targeted Linux-based systems compared to 2021. 

You probably didn't know that ZFS has internal protections against a ransomware attack... Just the checks/balances in how irt does COW and some internal properties within the pools. This is why a lot of companies trying to sell Ransomware Protection products, are running on top of ZFS... RE:  [https://klarasystems.com/articles/openzfs-openzfs-your-data-and-the-challenge-of-ransomware/](https://klarasystems.com/articles/openzfs-openzfs-your-data-and-the-challenge-of-ransomware/)

This is a peek at my Server:
```

mafoelffen@Mikes-B460M:~$ lsblk -e7 -o name,label,size,fstype,mountpoint
NAME        LABEL      SIZE FSTYPE     MOUNTPOINT
sda                    1.8T            
&#9492;&#9472;sda1      datapool   1.8T zfs_member 
sdb                    1.8T            
&#9492;&#9472;sdb1      datapool   1.8T zfs_member 
sdc                    1.8T            
&#9492;&#9472;sdc1      datapool   1.8T zfs_member 
sdd                  476.9G            
&#9500;&#9472;sdd1                  16M ext4       
&#9500;&#9472;sdd2               476.3G ntfs       
&#9492;&#9472;sdd3                 607M ntfs       
sde                    1.8T            
&#9492;&#9472;sde1      datapool   1.8T zfs_member 
sdf                    1.8T            
&#9492;&#9472;sdf1      datapool   1.8T zfs_member 
nvme0n1                1.8T            
&#9492;&#9472;nvme0n1p1 kpool      1.8T zfs_member 
nvme1n1                1.8T            
&#9492;&#9472;nvme1n1p1 kpool      1.8T zfs_member 
nvme2n1                1.8T            
&#9492;&#9472;nvme2n1p1 kpool      1.8T zfs_member 
nvme3n1                1.8T            
&#9492;&#9472;nvme3n1p1 kpool      1.8T zfs_member 
nvme4n1              931.5G            
&#9500;&#9472;nvme4n1p1            512M vfat       /boot/efi
&#9500;&#9472;nvme4n1p2              2G swap       [SWAP]
&#9500;&#9472;nvme4n1p3 bpool        2G zfs_member 
&#9492;&#9472;nvme4n1p4 rpool      927G zfs_member 
nvme6n1                1.8T            
&#9492;&#9472;nvme6n1p1 datapool  1000G zfs_member 
nvme5n1     datapool   1.8T zfs_member 
&#9500;&#9472;nvme5n1p1            1.3T zfs_member 
&#9492;&#9472;nvme5n1p2 datapool    10G zfs_member 

mafoelffen@Mikes-B460M:~$ sudo zfs list -o name,used,avail,userused@mafoelffen,mountpoint
NAME                                               USED  AVAIL  USERUSED@MAFOELFFEN  MOUNTPOINT
bpool                                              293M  1.46G                   0B  /boot
bpool/BOOT                                         291M  1.46G                   0B  none
bpool/BOOT/ubuntu_2cwpns                           291M  1.46G                   0B  /boot
datapool                                           907G  3.84T                   0B  /data
datapool/DATA                                      906G  3.84T                   0B  none
datapool/DATA/ubuntu_2cwpns                        906G  3.84T                10.0G  /data
datapool/DATA/ubuntu_2cwpns/ISO                    398G  3.84T                34.7G  /data/ISO
datapool/DATA/ubuntu_2cwpns/KVM-VM                 498G  3.84T                   0B  /data/KVM-VM
kpool                                             1.56T  1.85T                   0B  /KVM_Pool
kpool/KVM                                         1.56T  1.85T                   0B  none
kpool/KVM/ubuntu_2cwpns                           1.56T  1.85T                36.1G  /KVM_Pool
rpool                                             16.1G   875G                   0B  /
rpool/ROOT                                        14.1G   875G                   0B  none
rpool/ROOT/ubuntu_2cwpns                          14.1G   875G                2.00G  /
rpool/ROOT/ubuntu_2cwpns/srv                        96K   875G                   0B  /srv
rpool/ROOT/ubuntu_2cwpns/usr                       224K   875G                   0B  /usr
rpool/ROOT/ubuntu_2cwpns/usr/local                 128K   875G                   0B  /usr/local
rpool/ROOT/ubuntu_2cwpns/var                      6.97G   875G                   0B  /var
rpool/ROOT/ubuntu_2cwpns/var/games                  96K   875G                   0B  /var/games
rpool/ROOT/ubuntu_2cwpns/var/lib                  6.73G   875G                 512B  /var/lib
rpool/ROOT/ubuntu_2cwpns/var/lib/AccountsService   108K   875G                   0B  /var/lib/AccountsService
rpool/ROOT/ubuntu_2cwpns/var/lib/NetworkManager    180K   875G                   0B  /var/lib/NetworkManager
rpool/ROOT/ubuntu_2cwpns/var/lib/apt               109M   875G                   0B  /var/lib/apt
rpool/ROOT/ubuntu_2cwpns/var/lib/dpkg             46.1M   875G                   0B  /var/lib/dpkg
rpool/ROOT/ubuntu_2cwpns/var/log                   240M   875G                   0B  /var/log
rpool/ROOT/ubuntu_2cwpns/var/mail                   96K   875G                   0B  /var/mail
rpool/ROOT/ubuntu_2cwpns/var/snap                 1.48M   875G                   0B  /var/snap
rpool/ROOT/ubuntu_2cwpns/var/spool                 120K   875G                   0B  /var/spool
rpool/ROOT/ubuntu_2cwpns/var/www                    96K   875G                   0B  /var/www
rpool/USERDATA                                    1.93G   875G                   0B  /
rpool/USERDATA/mafoelffen_gtg9x1                  1.93G   875G                1.91G  /home/mafoelffen
rpool/USERDATA/root_gtg9x1                        2.49M   875G                   0B  /root

mafoelffen@Mikes-B460M:~$ sudo zpool status -v
  pool: bpool
 state: ONLINE
  scan: scrub repaired 0B in 00:00:00 with 0 errors on Sun Jul  9 00:24:01 2023
config:

    NAME                                    STATE     READ WRITE CKSUM
    bpool                                   ONLINE       0     0     0
      0196ab45-3ee2-894e-b725-39560409109f  ONLINE       0     0     0

errors: No known data errors

  pool: datapool
 state: ONLINE
  scan: scrub repaired 0B in 00:15:22 with 0 errors on Sun Jul  9 00:39:23 2023
config:

    NAME                                                   STATE     READ WRITE CKSUM
    datapool                                               ONLINE       0     0     0
      raidz2-0                                             ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_2TB_S6PNNM0TA09560A-part1  ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_2TB_S6PNNM0TA11601H-part1  ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_2TB_S6PNNM0TA47393M-part1  ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_2TB_S6PNNS0W330507J-part1  ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_2TB_S6PNNM0TB08933B-part1  ONLINE       0     0     0
    logs    
      nvme-Samsung_SSD_970_EVO_2TB_S464NB0KB10521K-part2   ONLINE       0     0     0
    cache
      nvme-Samsung_SSD_970_EVO_2TB_S464NB0KB10521K-part1   ONLINE       0     0     0

errors: No known data errors

  pool: kpool
 state: ONLINE
  scan: scrub repaired 0B in 00:07:16 with 0 errors on Sun Jul  9 00:31:18 2023
config:

    NAME                                 STATE     READ WRITE CKSUM
    kpool                                ONLINE       0     0     0
      raidz2-0                           ONLINE       0     0     0
        nvme-eui.0025385a2140bd61-part1  ONLINE       0     0     0
        nvme-eui.0025385a21418769-part1  ONLINE       0     0     0
        nvme-eui.0025385a2141f4fc-part1  ONLINE       0     0     0
        nvme-eui.0025385b21407ef0-part1  ONLINE       0     0     0

errors: No known data errors

  pool: rpool
 state: ONLINE
  scan: scrub repaired 0B in 00:00:14 with 0 errors on Sun Jul  9 00:24:17 2023
config:

    NAME                                    STATE     READ WRITE CKSUM
    rpool                                   ONLINE       0     0     0
      ae13efaa-d1cf-ec40-86a6-2883f0e07102  ONLINE       0     0     0

errors: No known data errors

```
Always good to have a good foundation that allows for hardening, adaptabilty, flexibility, and easy backup, that also just happens to be immune from a Ransomware attack.

And yes... Plus one on the Server Security Hardening Guide.

---

### Post by josephchrzempiec on 2023-07-18
Hello, Just a follow update. I did manage to recover 98% of what happen. The only things I couldn't recover was from almost 17 years ago. I'm looking at all the Suggestions everyone has offer for to help me. the fail2ban as well as the the ssh. It seems like the ssh is what they got through. I had ports open for that. 

What I have done so far is added fail2ban and I'm not using a VPN from my laptop to my network. No other ports are open. Also I'm working on a offsite backup server that backs up the files as well as snapshots just incase. I have learned a lot and read a lot. If there is anything else that is needed for me to look at please let me know. 

Edit: I also put stronger passwords on my network then before just incase. 

Joseph

---

### Post by dragonfly41 on 2023-07-18
A few tips I have found to be useful to add to the many others available.

Here is a link to another point of knowledge to probe your security measures..

[https://www.grc.com/shieldsup](https://www.grc.com/shieldsup)

Also explore app lynis as audit tool in Ubuntu repo.   $man lynis

And recently I added Google Titan Key for 2FA. I purchased a pair. One for backup.

---

### Post by ActionParsnip on 2023-07-18
USB drive that you connect for the night then disconnect during the day. If you get hit then you don't care. Run your backup to the external disk to protect your data

---

### Post by TheFu on 2023-07-18
**Never use passwords with server connections over the internet. Always use ssh-keys. Always.**

Daily, automatic, "pulled", versioned, backups are the only real protection against malware/cryptoware.  The client system cannot push the backups or have direct access to the storage used by the backup server.
On the backup server, you need to have sufficient storage to support enough versions of the backups so that ransomware people can't out-wait you and corrupt files.  For low risk systems, I keep 90-120 days of daily backup versions.  For high risk systems, I keep over a year.  Fortunately, my high risk systems don't really store data.

BTW, I get multiple emails every week with claims that my accounts have all been cracked and that I need to pay them 0.x bitcoins. It is never true.  I don't even read those messages anymore.

For backups, I use rdiff-backup at the core of my solution. I've posted 50+ times in these thread about it, including basic scripts.  These don't really show how to use "pulled" backups, since that requires some non-obvious ssh setup, but start with getting rdiff-backup being used in a client/server mode, then you can swap from "push" to "pull" backups once you master rdiff-backup versioning.

If you have an active malware issue, don't use local storage for backups. Backup storage areas need to be unavailable to the clients. Definitely don't use CIFS or NFS or sshfs or any sort of network mounted storage for backup storage.

As for server security, there's no "best way", since of the 500 things you can do, an attacker just needs to find one thing you didn't do to get in.  Network security is the first step. I missed any information about the network for these systems.  

You can setup an overlay network that encrypts all traffic between approved systems and blocks all other traffic, so if you don't need to allow outsiders any access, then you don't need to, even for servers located in public cloudy data centers.  Some people setup an overlay network and only allow ssh into their systems from authenticated peer computers on the same overlay network.  There are a few of these types of networks. They sound really easy to use, but some network devices might prevent them from working.

---

### Post by josephchrzempiec on 2023-07-18
I have no external drives on my server. Back up is a server I'm working on to build. All storage is internal. The server will be offsite. That is what I'm working on. I can't back up my server with usb drives not enogh space. I have a total of 80TB worth of storage All being used.

---

### Post by josephchrzempiec on 2023-07-18
Thank you for the reply back. A lot of this is over my head. As I'm learning so much more it is blowing my mine for what can be done to get into someones network. My router is a sonicwall firewall router with all the updates and security on it. I thought that was enough protection. It looks like it was not. I did find out how this all started. My wife downloaded a game that she always wanted to play and that is what started its attack. most of the time I'm very cautious of what I download or view. I thought her a lot of this stuff and she has been careful as well.  Lession learned I need to learn more about protection and I'm.

---

### Post by TheFu on 2023-07-18
> **josephchrzempiec said:**
> I have no external drives on my server. Back up is a server I'm working on to build. All storage is internal. The server will be offsite. That is what I'm working on. I can't back up my server with usb drives not enogh space. I have a total of 80TB worth of storage All being used.

You need local and remote backups for anything you deem important.
If you don't have backups, expect to lose that data.  It is a law of nature.  If you have 80TB of storage, at least 40TB should be reserved for backups.  If you can't afford to backup that data, then it isn't important.

About 20 yrs ago, I had a disk failure that caused me to lose 80% of my data.  I didn't have backups, but to be fair, the "popular" disks of the time were 100x smaller and 2x more expensive.  Even after losing all that data, I didn't get backup religion.  Took a few more years and a hacking attempt over the internet to finally teach me that lesson.  I happened to make an rsync mirror of a disk 1 week before it was hacked. They got in over a service that hadn't been updated in 3 months - it was a different time.  Anyway, thanks to the mirror, I was able to compare all the files between the 2 disks to see what had been touched.  I could also see what they were doing, since they were using the named userid, which had very few privileges .... basically, it could only create files under /tmp/ ... and the attackers had pulled some scripts to a 5-level deep set of hidden directories there to try and get root access.  They never go root and each attempt caused an alert email.  They were using a timing attack, trying to get root, but I'd patched against that, so it was never going to work.  Anyway, I killed all named processes and cleaned up their stuff buried in /tmp/ ... and didn't even reboot the system. All thanks to backups and 100% "knowing" they hadn't touched any other files on the system.

I'd been lucky and that experience got me to automate my backups, such as they were at the time.  Weekly, I'd mount the backup storage, run an rsync, umount the backup storage and be done.  While I don't recall any more issues for many years that the backups solve/prevented, I'm convinced that doing backups helps HDDs know about, and self-correct, sectors that are just starting to fail.  It prevents bit-rot too.
Around 2007, my backups became better. I switched from just plain rsync to using rsync + hardlinks to have versioned backups. This is when I got "backup religion".  I used that until about 2011, when the backups were taking so long that they couldn't finish in the 8 hr *backup window*.  I needed a new solution.  Enter rdiff-backup.  rsync is fast, but if you do backups of huge files, it spends lots of time validating that each sector is unchanged.  If any sector is changed, for local rsyncs, then the entire file gets copied over.  This can take a very long time.  rdiff-backup is smarter.  It stores the checksums for each sector in the last backup, so validating changes is much quicker and efficient.  I'm backing up about the same amount of data today as I did in 2011, but instead of taking 10 hrs, it is under 1 hour.  Most system backups take less than 3 minutes.  

Seems like a bargain to me.

Now, if you have 80TB, most of that is probably media files and media files should not be versioned, so rsync should be used with some options to prevent block-by-block validations.  I have about 40TB of storage on 1 system, 20TB is usable.  The rsync for those media files takes about 5 minutes to validate/run with only new stuff being mirrored to other storage.  I'm not made of money, so this is my compromise.

OTOH, non-media files get 120-366 days of automatic, daily, versioned, backups - with almost all of it pulled by the backup server from clients both on the same LAN and from VPS systems in different countries.  I just setup a new VPS this morning for a specific need for the next week or so.  After it was brought up, I setup the "pull" backups and ran a backup.  Because it is a VPN and I have the backup script 99% created, just needed to change the remote server name/IP and user for the pull backups, it took about 15 seconds to setup and less than 1 minute for the first backup to complete.

```
$ time sudo ./pull-backup-gw.example.com.sh 

=================
INFO: Backing up gw.example.com ...
================= 
INFO: Backing up gw.example.com ...
INFO: Removing backups older than 280D
No increments older than Tue Oct 11 18:43:17 2022 found, exiting.
INFO: Post-Backup-Cleanup() 

INFO: Backup Start:     2023-07-18-18:43:08
INFO:   Backup End:     2023-07-18-22:43:18

=================
Done.
================= 

real    0m9.846s
user    0m0.420s
sys     0m0.032s

```
Just for fun, I'll run a backup.  Less than 10 seconds, over the internet, to pull everything I need to recreate that system in less than 15 minutes.  And if it is cracked, there are multiple versions of the backups so I can compare differences from day to day to figure out what changed, when.

BTW, I've disabled all ssh access, except for ssh-keys.  No passwords will work.  If I lose the key, I get to rebuild the system.
Also, I've added the system to my weekly systems to patch script, so that will happen automatically going forward too.

---

### Post by DuckHook on 2023-07-18
I feel your pain. It seems that you got off lucky. Being able to recover 98% is *very* good.

Moreover, being able to trace this to wife's download is also noteworthy. You have good detective skills.

Not that you need my advice on personal matters, but FWIW, please be understanding of your wife. Mrs DH has made similar mistakes. We power users forget that, for general users, security is an obscure and arcane form of dark magic. Social engineering is very hard to guard against and I know that a cunningly enough crafted scam would get through my defences too.

There's not much I can add to the excellent technical advice that you've already received from our forum gurus.

I can only suggest one thing that isn't technical: do a rough inventory of your files. You may find, as I did, that most don't require backups. They are either stuff that you have original BDs/CDs for, or not really that important, or obsolete, or redundant. I do true backups on only a small subset of my files. The rest is handled by mirroring. If I get malwared, I'm willing to wave bye&#8209;bye to most of it, preserving only what I deem critical. This might whack your 80 TB down to a far more manageable amount.

---

### Post by josephchrzempiec on 2023-07-19
[LIST=1]
[*]> **DuckHook said:**
> I feel your pain. It seems that you got off lucky. Being able to recover 98% is *very* good.
[/LIST]

Moreover, being able to trace this to wife's download is also noteworthy. You have good detective skills.

Not that you need my advice on personal matters, but FWIW, please be understanding of your wife. Mrs DH has made similar mistakes. We power users forget that, for general users, security is an obscure and arcane form of dark magic. Social engineering is very hard to guard against and I know that a cunningly enough crafted scam would get through my defences too.

There's not much I can add to the excellent technical advice that you've already received from our forum gurus.

I can only suggest one thing that isn't technical: do a rough inventory of your files. You may find, as I did, that most don't require backups. They are either stuff that you have original BDs/CDs for, or not really that important, or obsolete, or redundant. I do true backups on only a small subset of my files. The rest is handled by mirroring. If I get malwared, I'm willing to wave bye&#8209;bye to most of it, preserving only what I deem critical. This might whack your 80 TB down to a far more manageable amount.


I worked for a R&D company many years ago for 5 years finding a lot of things I never know what was out there. One thing my old boss told me was I was very good at finding things and very good at eye to detail. I wasn't much good at programming but hardware I love and to figure things out even to the point where it drives me a little crazy if I can't figure it out. Plus my wife confuess to downloading some games. I can't blame her really.  But still it messed me with me big time for a few days even my health is not all that good. I'm glade i can recover mostly all of it.

I'm still tying to figure things out even if I don't understand it but trying. a lot of this is way over my head to be honest in programming as well as software.

---

### Post by TheFu on 2023-07-19
> **josephchrzempiec said:**
>   I did find out how this all started. My wife downloaded a game that she always wanted to play and that is what started its attack. most of the time I'm very cautious of what I download or view. I thought her a lot of this stuff and she has been careful as well.  Lession learned I need to learn more about protection and I'm.

My mother received an email from her granddaughter with the subject "New Baby Pictures!"  Kacie had just had a new baby, so I'd say there isn't a grandmother in the world who could have resisted that tease.  She downloaded the files and it was all over.  Immediately, her computer was taken over. Adds, spam, all the evils of the internet started and she knew it was a problem.  She was running MS-Windows.  I told her not to use any online banking or purchasing stuff until I could get there in a few months.  I'd switch her to Linux.

She was really afraid of the OS change, but I'd had her running F/LOSS programs for years already, so when I loaded up Lubuntu onto her system and she saw the icons she already knew, much of her fear was gone.  Further, I setup a local versioned backup solution AND week pulled backups of her most critical stuff to my home.  She lost some capabilities for her stock market stuff, but I did create an MS-Windows Virtual Machine with the 2 programs she needed inside with a fresh install.  No browser. No email inside that VM, just financial and stock tools.

She ran that OS until her natural death a few years later.  I provided remote administration from 4 states away.  She was 82 yrs old and her mind was sharp, like always. We even pulled the HDD out of a Pentium4 computer and replaced it with a Core i7.  Afterwards, I asked if it was "better".  Mom said it seemed a bit faster, but not really noticeable.  ;)

For any malware, there's only one method to mitigate the risks for all of us.  Daily, automatic, versioned, "pulled", backups.  Every day, we make hundreds of choices on our computers. And most days we get them all correct enough not to matter, but over years of use, we will all make a mistake.  You, me, our better halves.  We will all make a mistake, eventually.

I use the same methods day after day, year after year, to avoid issues. They've become habits.  But knowing there's a version of the system backed up last night that can be restored is a huge relief.  When I first got backups working, I started sleeping better, the sleep of someone without a huge worry on their mind.

---

### Post by MAFoElffen on 2023-07-19
Remember the 3-2-1 backup strategy? Three copies of data: the original data and 2 copies. Two forms of backup media. One copy stored offsite.

I only used that much for companies for their production data. It all depends on your acceptance of risk, and what your RPO's & RTO's are.

---

### Post by TheFu on 2023-07-20
Rep. I do this for everything, except media.  

I take it further.  The "remote" copy is not in the same region, so if a region-wide disaster hits, the data isn't impacted.  My location doesn't really have most large natural disasters. We do have tornadoes, but in looking at tornado tracks the last 50 yrs, ZERO have been closer than a mile to here. The location is on the lea side of a hill.  Flooding happens, but not here. We have underground utilities, so the most common issues are when road work snags a utility cable. That happened 25 yrs ago, but in the last 20 yrs, there's very little large scale building locally, so utilities are all working.  Fiber doesn't care about water, unlike the old copper DSL lines.

I've felt 1 earthquake, about 15 yrs ago here. It was tiny and rolling, so most people didn't feel it.  

Used to live in a very active earthquake region, just a few miles from the fault line that shifted the Mississippi river path. We had hundreds of quakes there each year. It wasn't strange to find things on the floor after the quakes. [https://earthquaketrack.com/us-mo-new-madrid/recent](https://earthquaketrack.com/us-mo-new-madrid/recent)

For example, where I live, we don't get hurricanes, but my backup data is 4 states away were they do get hurricanes.  The type storms that wipe cities off maps completely, but they don't have problems with flooding or earthquakes or snow there.  The location for my backups survived, untouched after 2 recent category 4+ hurricanes, so there's something about where it is placed that protects it. They are literally on the right side of the railroad tracks that split the peninsula.

I can't imagine keeping data where there are earthquakes.  Sure, they build buildings on springs and try to make them "earthquake proof", but who needs the hassles? 
At 1 location, someone placed their data center at the end of  a busy international runway, prone to floods, with annual hurricanes likely.  When I learned about this location, I couldn't think of anything dumber. Fortunately, only the locals though of it as a DC. We considered it a "resource room" and treated it that way with non-critical systems only housed there. It has been flooded about every 5 yrs, so the building is a bad place for backups. 

Our default RTO and RPO were 24 hrs for most applications.  We had some systems that had 15 minutes for both RTO and RPO. For those, we'd write the data to active systems with only a slight delay and we'd test failovers every weekend, run for a week, then fail back.  15 minute RPO isn't hard and barely impacts performance. Anything shorter and modifying applications to write to redundant DBs is needed.  We used delayed transaction replays to get the data to the secondary location.
One system had a 4 hr RPO and didn't just have a database for data. For that one, we deployed EMC BCVs that took clones every 4 hrs, then transmitted those to the DR location another state away.  If a complete DC had to be taken down due to a disaster, then the DR DC would be switched over to act like the failed DB 100%. We're talking many, many, many, thousands of servers being moved.  Individually, each system tested their DR plans annually, but I have some doubts that the full DC-migration would have worked.  To my knowledge, they never tested it.  In a prior job, we did pay to rent a DR site and stream data there all the time.  Annually, we'd test the DR plans, but only had 3 days budgeted.  Those DR efforts never completed in the 3 day period.  Each year, notes for improvement would be taken and the following year, we'd get just a little farther.  In the 8 yrs I was in the environment (I wasn't responsible), they never completely a successful DR test.

DR planning needs to be integral to the total system design at the start. Tacking it on later seldom works for anything except the most trivial business needs. Inside a business, systems don't exist alone.  Getting data feed from other systems and sending output to the correct downstream systems can be very difficult in a DR situation.

Nobody starts out knowing these things. I didn't learn how to handle DR stuff until I'd been working 10 yrs already.

---

### Post by MAFoElffen on 2023-07-20
> **TheFu said:**
> 
Nobody starts out knowing these things. I didn't learn how to handle DR stuff until I'd been working 10 yrs already.

Very true.

I took this a lot more seriously when I was brought to help my company recovery from a ransomware attack, that was caused by one of their remote nodes being breached... And had encrypted not only their infrastructure, but also the last 9 months of their backups.

I was brought in to recovery their infrastructure, up to current... Patch that infrastructure so it could exist until something else was put into place... Come up with a new infrastructure architecture, and a new disaster recovery plan. They still had all their paper receipts and invoices. I worked with two accountants who recreated 9 months of records, to get it current, in 1 month's time, when the taxes were due for their fiscal year. That was a nightmare.

I learned a lot of things quickly, on what happened, how it happened, and how to prevent it. I did this alone, and was also responsible for implementing the new infrastructure from the ground up, while the patched old infrastructure was maxed out, but chugging along.

The way it worked, was that it encrypted 'everything' and it existed that way for 9 months... Until one day, when it deleted or lost access to the encryption key. Then the systems were locked up. The breach was through some remote access software product that had been compromised. We didn't hear from the vendor, that that product was compromised, until after I found out that was where their problem originated, and I reported that to that Vendor. 'Then' they told us that they were aware of the problem!!!

Yes. Being a victim of a Ransomware Attack is not something I would wish on anyone.

---

### Post by josephchrzempiec on 2023-07-22
> **MAFoElffen said:**
> Remember the 3-2-1 backup strategy? Three copies of data: the original data and 2 copies. Two forms of backup media. One copy stored offsite.

I only used that much for companies for their production data. It all depends on your acceptance of risk, and what your RPO's & RTO's are.


I know the 3-2-1 problem was back then I didn't have the money to buy more drives or build a second system even from use parts. Drives back then was way to costly for me back then. Over time I forgot all about it.I wasn't even thinking about it until when this happens.

---

### Post by josephchrzempiec on 2023-07-22
> **TheFu said:**
> 
Nobody starts out knowing these things. I didn't learn how to handle DR stuff until I'd been working 10 yrs already.



Same Here. Took me many years to figure things out myself. Until I can get my handle into it

---

### Post by TheFu on 2023-07-22
> **josephchrzempiec said:**
> Same Here. Took me many years to figure things out myself. Until I can get my handle into it

If you don't have backups, I'd say you didn't learn what was important.  I suppose, that's a matter of opinion.
For me, computers aren't important.  It is 100% about the data and being able to have the data survive any issues.  Without the data, businesses are dead and will never come back.  If you lose the wedding pictures and video, you may not wake up tomorrow either.

---

