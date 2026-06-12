---
title: "Assorted questions: hard-drive, partition management, ftp related"
date: 2007-02-23
forum: General Help
---

### Post by Chake99 on 2007-02-23
Running Kubuntu Dapper Drake

I'm considering buying a new hard drive as I only have a single 30 GB one. Is there any way to check from KDE if my motherboard supports SATA hard drives, or what does the connector look like? 

I also want to create multiple partitions for different operating systems including linuxes/*bsds but I would want my central files on a partition accessible to all of them. How would I do this? 

How would I rig my computer so I can FTP into my home folder and download and upload files with a static IP? VNC?

Answers to any questions appreciated, links to howtos or even names of software would be nice. 

Thanks in advance.

---

### Post by Chake99 on 2007-02-23
*bump*

---

### Post by Chake99 on 2007-02-24
*bump*

---

### Post by JohnPhys on 2007-02-24
I'm not sure on checking to see if your mb supports sata from KDE, but the connectors on the motherboard are about 1.5 cm long, and look mostly like this

[Some Gigabyte mobo with SATA]("http://www.newegg.com/Product/ShowImage.asp?Image=13%2D128%2D011%2D02%2Ejpg%2C13%2D128%2D011%2D03%2Ejpg%2C13%2D128%2D011%2D04%2Ejpg%2C13%2D128%2D011%2D05%2Ejpg%2C13%2D128%2D011%2D06%2Ejpg&CurImage=13%2D128%2D011%2D03%2Ejpg&Description=GIGABYTE+GA%2DM59SLI%2DS5+Socket+AM2+NVIDIA+nForce+590+SLI+MCP+ATX+AMD+Motherboard+%2D+Retail")

As for sharing data, if you need to access files from windows you'd need to create a partition with the vfat file system, or use 

[Read ext2,ext3 from Windows]("http://easylinux.info/wiki/Ubuntu_dapper#How_to_read_Linux_partitions_.28ext2.2C_ext3.29_in_Windows_machine")

to get windows to read ext2/3 file systems.

You just need to create a partition that you don't install any OS to, and have each of your OS's mount it at boot.  This can be done by editing the fstab, and if you need further help I can certainly elaborate.

As for being able to ftp in to your machine from the outside, if you get a dynamic IP address from your ISP, you can use 

[Get Hostname from DynDNS]("http://easylinux.info/wiki/Ubuntu_dapper#How_to_assign_Hostname_to_local_machine_with_dynamic_IP_using_free_DynDNS_service")

to make it easy to always access your machine.  That page is *full* of useful info by the way, if you haven't already come across it.

Hope this helps!

---

### Post by undecidable on 2007-02-24
I use 3 logical partitions:

one for Windows partition, labelled "data", as drive D:
   and not mounted in Lx
one ext3 for Linux data, labelled "Lxdata", mounted to /docs,
  and invisible to Windows. 
and one fat32, labelled "xfr" for transferring files between them.
On Windows "xfr" is mounted a drive X:
On Lx "xfr" is mounted to /xfr.

I can mount "data" from Lx if necessary, 
and can read the Lx partition from Winzzz,
but generally prefer to use the "xfr" partition
to reduce interaction between the systems.  

Note:
they need to be logical partitions as if you have only 1 hdd, 
that is limited to 4 primary partitions,
one for windows, one for Lx, and only 2 left,
so you divide one of these into logical partitions.

hope this is helpful.

---

### Post by zbmowrey on 2007-02-24
SATA connectors are slots that look like a long "L". (Long being 1/2" or so). They come in even numbers, so you'll find 2 or 4 clustered together in the same spot on the motherboard.

As for partitions, if you can have four primary partitions, why not:

Win NTFS
Lin Ext3 - /
Lin Swap
NTFS Storage or Ext3 Storage (using the appropriate drivers to enable access via the other OS... If in Linux, use NTFS-3G which has recently been released as v1.0, or in Windows use Ext2 for Win drivers).

As for remote FTP, you'd need to configure your router/modem to allow pass-through traffic on the FTP ports, and then install and configure an FTP server daemon. Filezilla might work out alright for you, but YMMV as I have no experience with LInux FTP servers (yet).

---

### Post by Chake99 on 2007-02-24
With only four logical partitions allowed, does that include swap?

Thanks for the advice guys, but if I have let's say a data partition that auto-mounts to media and has a link from my home folder, I suppose I still need to install applications on my OS partition? (checking: is it impossible to have binary compatible linux distros/bsd's share applications?). 

Dyn-dns looks like exactly what I wanted.

EDIT: Does KFRB act as a vnc server? using vnc on a windows machine could I access my desktop?

---

### Post by JohnPhys on 2007-02-24
As far as the partitioning goes, you should be able to put a swap in a logical (rather than a primary) partition (I've done it before with edgy eft).

I'm not sure on the applications question.

---

