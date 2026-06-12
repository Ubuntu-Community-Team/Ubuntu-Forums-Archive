---
title: "Using Ubuntu as a NAS"
date: 2016-12-04
forum: General Help
---

### Post by freddy58 on 2016-12-04
I am going to take an older computer a friend gave to me, and install two or three 2 TB drives in it, then install Ubuntu.  Now question, can Ubuntu set up a raid array ?  Then I am going to hook the computer to the router, where a Windows 10 and a Laptop running Windows and Linux Sarah Cinnamon are also hooked to.  I want to use this extra computer as a NAS server, not running web pages and such, but so it can be accessed from the INTERNET with a smart phone from anywhere.  Is that possible to set up a raid 1 array and partition off a 2GB area to install Ubuntu  in it, then set up folders that can be viewed from anywhere?

---

### Post by TheFu on 2016-12-04
RAID is 1000x less important than having good backups.  Get backups working first.  RAID solves 3 problems.  Versioned backups solve 1,000 problems, including certain failed RAID issues.  RAID adds complexity that just isn't necessary for 99.999% of home users.

Yes, you can use ubuntu as a NAS, if you like, but over the internet it is probably easiest (and definitely MORE secure than HTTPS) to use an ssh-based access method like sftp, scp, sshfs, or ... ssh-tunnel.  All networked OSes have sftp clients. If the client is Linux/Unix, there is always sshfs too.

Inside your network, the machine can be an NFS server.  All Unix-based OSes speak NFS natively, it is faster than other network file sharing methods AND the mounted storage uses the same permissions as local storage.  Just ensure all the userids and groupids match across all systems on the network (the **id** cmd shows the numbers that need to match).  There is an NFS client for Windows in Ent/Ult versions, but I've never gotten it working. Need to try harder at that. WinSCP is an easy solution or you can setup samba, but know samba/CIFS doesn't really honor Unix file/directory permissions without effort to match MSFT-UUIDs to Unix userid/groupid.

Do not allow NFS, CIFS, Samba to be available over the internet without a full, complete, secured, VPN.  I would also say that if you are thinking about using owncloud or nextcloud for access, be certain to use a full VPN too.  

Other people will have different opinions about this stuff, so read some other info and you can decide what level of security is your target.  Folks think I'm too paranoid. Of course, I think I'm not. ;)

BTW, older computers aren't always a good thing.  For $100, you would be amazed at the motherboard+CPU you can get that only uses 35W. Reusing old HDDs, RAM, etc ... you can get a system that is really quite fast and would easily handle being a NAS, media server, ebook server, and still have 80% CPU for other things.  My NAS, built from spare parts and $100 MB+CPU, has over 16TB connected and does all those things.  I don't use RAID (on that machine), but have 60 days of versioned backups. It could also be used as a remote desktop from anywhere in the world using a very low-power, $99,  laptop too.  Just sayin'.

---

### Post by mastablasta on 2016-12-05
mdadm will provide RAID of your choice. however, you should think if you really need it. RAID guards against disk failure an dit is not a backup solution. it is mean for servers to have high uptime.

---

### Post by gordintoronto on 2016-12-05
You could install Ubuntu Server if you are handy at the command line, or Xubuntu if you are not. Give either one 10 GB or more for the root; 2 GB won't work.

I also agree with the comments about RAID. It requires a fairly high level of technical proficiency, for starters.

Many ISPs block any attempt to run a server, so you might wish to check this before you buy a lot of hardware.

---

### Post by DuckHook on 2016-12-05
+1 to all advice above.

@OP

When three *very* seasoned power-users all say "avoid RAID"...     I leave you to draw your own conclusions.

In my opinion, you are focusing rather too much attention on the wrong subject. Given your usage intentions, your primary issue is security, not HW configuration. In this day and age, anything open to the big, bad internet had better be hardened ten ways to Sunday. In this respect, I second all of TheFu's security comments wholeheartedly. He is not being overly paranoid and is, in fact, being very realistic. Speaking only for myself, I judge the risks to be so high that I refuse to open my intranet to the internet and try to achieve what you are planning with third-party alternatives that are already outside of my private network. Let *them* deal with the security threats. I don't store anything of importance or sensitivity with them anyway.

I understand how the lure of having all your info at your fingertips is a strong one. But such convenience is the enemy of security, and one always has to carefully weigh whether the convenience really is so great as to outweigh the very real risks. Usually, when examined dispassionately, it is not. The convenience is overrated and the risks underestimated. But only you can decide in your own case.

---

### Post by kevdog on 2016-12-06
To add fuel to the fire...

If setting up Ubuntu as a NAS and you have the time if you want the features of a RAID array -- I would definitely thing about using ZOL rather than RAID.  ZOL -- ZFS on Linux -- is a type of filesystem very similar to RAID, however it also able to create snapshots which you could send to another computer -- which is one means of making a backup. You can make numerous snapshots as well and revert back to the snapshot if corruption is a widespread problem -- or simply recover individual files if you want a partial restore through the use of mounting the snapshot as a clone. ZOL is now contained by default within the Ubuntu distribution, however it's not the default filesystem, so setting up ZFS with Ubuntu -- you'll have to do some reading.

In terms of file sharing from your phone or computer outside the intranet -- that's a very wide topic.  Sure you can do it through many different ways -- some more secure than others.  The easiest is ftp -- which isn't very secure.  SSH which offers sftp and also sshfs (a way to mount a remote filesystem similar to NFS) is more secure and I would venture to guess at least bare minimum for what you want to do.  It's pretty easy to set up an SSH server and it's very well documented.  Improving security would be to add a firewall for the NAS, however the subject of iptables or ufw is a little bit more complicated and would usually require a little bit more research.  I'm not sure what tools you would be using from your phone or programs that would be available on your phone, so you may need to match programs available on your phone to programs that will act as a server on your computer.

More complex solutions would be running your own cloud server such as owncloud or nextcloud.  These packages are freely available within linux.  If you want to run these through a VPN, then your possibly looking at running an OpenVPN server either on your router or on your computer -- which is actually kind a pain to setup depending on your type of VPN -- bridged or NAT.  I've had far more success with bridged VPNs than NAT VPN's however I'm sure there are different opinions on the subject.  Unfortunately if working with VPNs you are going to have to have some knowledge of iptables and network routing.  

Another possibility would be to run your server within a jail or virtualize your server such as with a program like virtualbox.  The use of containers such as docker could be another options to separate the server from the main OS on the computer, however I don't have a lot of luck or skill with running things from containers since they are new to me. 

There are specialized NAS distributions, such as FreeNAS (BSD Based), Nas4Free (BSD Based), and OpenMediaVault (Debian Based).  Here's a link: [http://www.mondaiji.com/blog/other/it/10210-the-hunt-for-the-ultimate-free-open-source-nas-distro](http://www.mondaiji.com/blog/other/it/10210-the-hunt-for-the-ultimate-free-open-source-nas-distro).  

I'd start simple however in your case. Possibly with an ssh server.  As you get more comfortable with things you can add complexity and possibly new hardware. 

Always have a backup strategy in place however.  Whether this be through rsync, rsnapshot, duplicity, obnam, borg, simple cp or tar archives -- whatever -- just have a basic system in place.  Probably the easiest would be to use rsync which can run on top of your ssh setup.

---

### Post by HermanAB on 2016-12-06
RAID: Not much use - if you accidentally delete a file on one disk, it is immediately erased from the other one too.  Rather set up an automated backup system to make versioned backups from the first disk to the second disk.
WAN access: You need encrypted secure access.  SSH SFTP is one way to do it and there are client apps for smart phones.

Maybe look into Retroshare for sharing files, texts, voice and video calls, securely with multiple users and machines.

---

### Post by kpatz on 2016-12-06
RAID provides protection against disk failure but that's about it.  If you want RAID I'd go with a simple RAID1 setup - 2 mirrored disks.  This is the simplest way to do it and your NAS will stay up even if a drive fails.  You'll need backups in any case, multiple generations ideally, since if a file gets corrupted or overwritten you don't want to overwrite your only backup of it with the corrupted version.

Another option for using 2 drives is to have one as the primary and one as your backup.  You'd use cp, tar, or rsync to copy files from one drive to the other periodically.  If you copy to a new directory each time, you'll have versioned backups.  Even better is to get an external USB drive or two, and back up to that, and keep one off site.

ZOL (ZFS on Linux) is great.  I have it on my new server.  With ZFS you can create snapshots which are instant images of your file system at that point in time.  If you need to go back to that point in time due to a file getting deleted or corrupted you can either roll back the filesystem to that snapshot or copy the file(s) you need from the snapshot.  You can also clone snapshots, and send them to another ZFS pool on another disk/set of disks to make backing up quick.  But if you're new to Linux ZFS may be a bit advanced.

---

