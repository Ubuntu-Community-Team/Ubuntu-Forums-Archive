---
title: "File ownership on a Network USB drive through Netgear router"
date: 2018-05-01
forum: General Help
---

### Post by b3nst3r on 2018-05-01
Ubuntu 16.04.4 LTS (GNU/Linux 4.4.0-119-generic x86_64)

I have an 8 TB WesternDigital USB drive connected through my Netgear wireless router, and I use the following command to mount it:

```
 mount -t cifs //10.0.0.1/USB_Storage /media/readyshare
```

Ubuntu prompts me for the password, but I've tried it with the router password and with a blank, and it seems to work either way.  I never formatted this drive, it's exactly as I purchased it.  Any windows user or Ubuntu server user can create folders, and write files.

One day this USB drive was not responding correctly, so I put it on my windows machine, and ran CHKDSK to fix corrupted files.  Put the drive back on the router, and then mounted with the above command, and everything appeared to be working correctly.  The problem though is root:root owns every folder, and every file.  Ubuntu users can not create directories, nor write to root:root folders.  I then would run the commands:

```
cd /media/readyshare/
sudo mkdir directory_newname
sudo chown -R user1:user1 directory_newname
ls -al
```

and I can see that user1 is now the owner of the directory, and user1 can write new files to this folder.  If user1 creates any new directories, they are owned by root:root and I'm right back to where I started.

I've been googling a bit, get close to answers, but I just haven't found a solution to this.  Am I mounting it incorrectly?  Do I need to change ownership of the entire hard drive? (obviously I let windows have it's way and it's causing me a bit of grief now.)  What is the traditional way to work with a drive like this?

Thanks for any links, help or insight you can provide me.

---

### Post by TheFu on 2018-05-02
Insight ... 

a) be very, very careful attaching storage to routers.  This has commonly been a way to share those files over the internet thanks to bugs.  [https://securityaffairs.co/wordpress/63724/hacking/netgear-security-advisories.html](https://securityaffairs.co/wordpress/63724/hacking/netgear-security-advisories.html)  There are usually hundreds of bugs in non-trivial software.  Netgear has a $15000 bug bounty, which is enough to make security researchers responsibly disclose issues, if they find them.  That is good.

b) for NTFS partitions, permissions are controlled at mount time.  You'll have to research the netgear site to learn how they allow control of owners, groups and permissions, if at all.  chmod doesn't work on cifs mounts. Perhaps [https://kb.netgear.com/en_US/20129/](https://kb.netgear.com/en_US/20129/) is helpful?  I find it scary that an internet website is used to control internal storage.

c) CIFS permissions are controlled on the CIFS server-side, which also points back to netgear.

If you disconnect the drive and physically connect it to an Ubuntu machine, then it would be an Ubuntu question, IMHO. We can help with mount options to control the owner, group and permissions.  Of course, I think it would be smart to format the disk into 2-4TB partitions with ext4, mount each on the Ubuntu machine and have it share via NFS and/or samba to other systems on the subnet as needed. NFS is much preferred over CIFS for sharing between Unix systems.  Linux file systems are better for Posix permissions and can be shared using a full Samba, not a stripped down version. I don't know which version of Samba netgear uses, but it is extremely common for these devices not to provide the full version as provided by samba.org.

Don't know if any of this helps, just some random guy over the internet sharing opinions.   Hopefully that netgear link is useful.

---

### Post by SeijiSensei on 2018-05-02
You can set mount options for CIFS shares in the options list for the entry in /etc/fstab or using "mount -o options_list".  The available options include ownerships and permissions:  [https://www.samba.org/samba/docs/3.5/man-html/mount.cifs.8.html](https://www.samba.org/samba/docs/3.5/man-html/mount.cifs.8.html)

---

### Post by b3nst3r on 2018-05-06
I'll take a look at the links.  I've googled USB mounting before, and it worked great until I rebooted the server, then it was looking in the wrong place for the boot partition.  I have to unplug my 4TB USB drive before I can reboot my Ubuntu server.

I logged into the router readyshare area and Write-All-No Password & Read-All_No Password.

I'll have to read the CIFS guide  that was posted.

---

### Post by b3nst3r on 2018-05-06
> **TheFu said:**
> 
Of course, I think it would be smart to format the disk into 2-4TB partitions with ext4, mount each on the Ubuntu machine and have it share via NFS and/or samba to other systems on the subnet as needed. NFS is much preferred over CIFS for sharing between Unix systems.

I am already over 50% on this drive.  What is the purpose  of using smaller partitions?  If I choose to run this drive directly on the Ubuntu Box, I may just Shuck the drive and start using UnRaid.  I wanted to wait until I had an actual server machine before going down this path.

---

### Post by TheFu on 2018-05-07
> **b3nst3r said:**
> I am already over 50% on this drive.  What is the purpose  of using smaller partitions?  If I choose to run this drive directly on the Ubuntu Box, I may just Shuck the drive and start using UnRaid.  I wanted to wait until I had an actual server machine before going down this path.

Whenever I purchase and deploy storage, I consider backups. If I can't easily backup a partition, then I won't deploy it.  4TB disks can be found fairly cheap and they are large enough to still be convenient.  Media centers definitely understand having multiple partitions for "movies" or any other media. They merge them into a single flat view in their interfaces.  I have 4 separate partitions for recorded TV shows, but inside Kodi or Plex, they appear as coming from the same place, sorted by the media tool.

I do have an 8TB disk which I use for backups.  When I bought it, there wasn't sufficient failure history on the brand/model to make me comfortable. My primary disks were 4TB, so it was natural to split it to that size.  Every few months, I see 8TB disks for just under $150 but I can find 4TB disks daily for highly competitive pricing.  It used to be that way for 2TB disks, so I have a few of those on other systems still.

Huge partitions for anything besides data is a storage design failure.  Never put a HOME or OS or application into a partition much over 25G.  Many reasons for this.

I do not use any software that merges partitions or logical volumes across different physical disks. Learned the hard way that wasn't a smart idea.  Lost 80% of my data.  Never again.

If I was going to do any multidisk merging, it would be using 64-bit ZFS and I'd have 100%-know-I-can-restore backups that were fully, periodically, tested first.

Anyways, those are my thoughts.

---

### Post by HermanAB on 2018-05-07
Note that you can easily make your own NAS thingummajig using a Raspberry Pi and USB storage:
[https://www.aeronetworks.ca/2017/12/raspberrypi-3-headless-with-ssh.html](https://www.aeronetworks.ca/2017/12/raspberrypi-3-headless-with-ssh.html)

---

### Post by TheFu on 2018-05-07
> **HermanAB said:**
> Note that you can easily make your own NAS thingummajig using a Raspberry Pi and USB storage:
[https://www.aeronetworks.ca/2017/12/raspberrypi-3-headless-with-ssh.html](https://www.aeronetworks.ca/2017/12/raspberrypi-3-headless-with-ssh.html)

Another option with better performance and a higher price ODROID XU4 8-core ARM 
[https://category5.tv/shows/extras/episode/525-odroid-cloudshell-2-xu4/](https://category5.tv/shows/extras/episode/525-odroid-cloudshell-2-xu4/)  It has USB3-to-SATA ports.

The new Raspberry Pi v3+ addresses some (older models are v3, v2 and v1- the '+' matters), but not all of the issues. It definitely **is** better than using a WAN facing router for storage. But for $48 (Pi, Case, PSU), what do you want?

If you have spare parts lying around (old PC with case, PSU, HDD), are willing to use a 10W-35W CPU and $100, you can build a cheap Intel-based system that will make a great NAS for most people and has 4 or 6 or 8 SATA and a number of USB3 ports for nearly unlimited storage.

There are other, low-power, AMD/Intel CPUs that do SATA, USB3, and use 12W at full speed.  My only caution about these devices is to be certain to get 64-bit CPUs since many distros are dropping 32-bit support soon if they haven't already.

---

### Post by b3nst3r on 2018-05-14
Music is the only thing I'm concerned about backing up.  3 desktops computers, and one 4TB USB are backup.  This 8 TB I'm using so everything is available to every one in the house.  My Ubuntu machine is running Plex server, TS3 defer, ioquake3 server, and rtorrent\rutorrent.  I have a 512 SSD for the OS, and a 4TB for storage.

I've been instructed to run openNAS or unraid in the box, and run Ubuntu as a virtual machine.   Sounds neat, but complicated.  I did condense 3 boxes to this one Ubuntu machines, saving myself electricity, and requiring only one machine to keep up with.

Trying to keep up with where I store things is starting to be a headache, I'm trying to avoid starting from scratch to organize everything.

---

### Post by TheFu on 2018-05-14
> **b3nst3r said:**
> 
Trying to keep up with where I store things is starting to be a headache, I'm trying to avoid starting from scratch to organize everything.

I would use NFS to mount all the storage onto the Plex Server, something like this:
```
/D/M1
/D/M2
/D/M3
/D/M4
```

And let Plex merge the storage into organized views.  It wouldn't matter if the storage was local or remote. To plex, it all appears like local storage.  Music is so small, it just doesn't matter on any modern wired network.

When/if you need to know where an actual file is on disk, I'd use **locate**.  Locate pre-builds a DB of files periodically, usually daily, using the updatedb tool. Setup a script that searches my different storage servers for a file by ssh'ing into each system.  

But there are many different ways to solve something like this. Probably a few that are better too!

---

