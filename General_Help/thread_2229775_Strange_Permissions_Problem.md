---
title: "Strange Permissions Problem"
date: 2014-06-15
forum: General Help
---

### Post by matthew20 on 2014-06-15
I'm trying to make a backup image of my Linux machine's hard drive before upgrading from Ubuntu 12 LTS to Ubuntu 13 LTS. I'm using the process described here: [http://community.spiceworks.com/how_to/show/1778-using-ubuntu-to-backup-one-off-system-images](http://community.spiceworks.com/how_to/show/1778-using-ubuntu-to-backup-one-off-system-images)

I can boot to the live CD, install the smbclient, and mount my Windows machine's file share to /mnt/share.

If I run:

sudo touch /mnt/share/test

the file gets created. However, if I run:

sudo dd if=/dev/sda bs=64K conv=sync,noerror | gzip -c > /mnt/share/test

I get an error:

bash: /mnt/share/test: Permission denied

Doing a Wireshark capture on the Windows 7 machine to which the file is supposed to be written, I see a total of 3 packets between the two machines when I run the dd | gzip command. the first is an SMB QUERY_PATH_INFO for path \test, the second is a QUERY_PATH_INFO response with error STATUS_OBJECT_NAME_NOT_FOUND. When I issue a touch /mnt/share/test from the Linux machine, I see on the Windows machine that the conversation starts with an SMB NT Create Request.

Anyone have any ideas?

Thanks!

---

### Post by steeldriver on 2014-06-15
The 'sudo' is only getting applied to the dd command - probably the easiest thing would be to use an interactive sudo shell

```

sudo -i
dd if=/dev/sda bs=64K conv=sync,noerror | gzip -c > /mnt/share/test
exit

```

---

### Post by Bucky Ball on 2014-06-15
Which 13.** release are you upgrading to? 13.04 is no longer supported so you won't get far there, and a bit of a waste of time if you do. Please see the forum staff's recent recommendations on EOL (end-of-life) releases:

[http://ubuntuforums.org/showthread.php?t=2229730](http://ubuntuforums.org/showthread.php?t=2229730)

You're not very specific, so hard to know, but if you are running 12.04 LTS then you can upgrade directly to 14.04 LTS via the update manager. A clean install is generally less problematic, though.

---

