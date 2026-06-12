---
title: "Ubuntu 14.04 Fails to Load After Entering Encryption Password"
date: 2015-12-25
forum: General Help
---

### Post by pf49 on 2015-12-25
I'm running Ubuntu 14.04LTS with kernel 3.13.0-74 and hard drive encryption and the OS is now failing to load after entering my encryption password after GRUB. Normally I would get the message "something something crypt set up successfully" and now I'm just getting the Ubuntu logo with the five dots underneath it. This just started out of the blue this morning, what a wonderful Christmas present. Tried restarting and booting into an earlier kernel and had the same problem. Any advice on what might be the problem and how to go about fixing it?

ETA: Tried to access the drive from another hard drive running Mint 13. Entered encryption password when trying to mount drive and received the following:

"Unable to mount location

DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expire, or the network connection was broken."

---

### Post by TheFu on 2015-12-25
Boot from an Ubuntu 14.04.3 CDROM/USB Flash setup - "Try Ubuntu", run **lsblk** and post the output so we know what we're working with. Please use code tags, so things line up here.

Older versions of other OSes probably don't have a compatible version of the encryption tools. That is why Mint 13 didn't work, probably.

---

### Post by pf49 on 2015-12-25
Alright, let me see if this works. sda is my main hard drive, the one I'm trying to access. sdb is where Mint 13 is, and sdc is an old hard drive that dual boots Ubuntu 10.04 (the larger partition) and Windows XP. 

```
NAME                                                          MAJ:MIN  RM      SIZE RO TYPE
MOUNTPOINT
sda                                                           8:0       0   931.5G   0 disk
|__sda1                                                       8:1       0     243M   0 part
|__sda2                                                       8:2       0       1K   0 part
|__sda5                                                       8:5       0   931.3G   0 part
   |__luks-7fd5a5d2-b418-472f-a4c0-fde48709dba3 (dm-0)        252:0     0   931.3G   0 crypt
sdb                                                           8:16      0   931.5G   0 disk
|__sdb1                                                       8:17      0   915.6G   0 part
|__sdb2                                                       8:18      0       1K   0 part
|__sdb5                                                       8:21      0      16G   0 part
[SWAP]
sdc
|__sdc1                                                       8:32      0   596.2G   0 disk
|__sdc2                                                       8:33      0   130.7G   0 part
|__sdc5                                                       8:34      0       1K   0 part
[SWAP]
|__sdc6                                                       8:38      0   459.8G   0 part
sr0                                                           11:0      1    1006M   0 rom
/cdrom
sr1                                                           11:1      1    1024M   0 rom
loop0                                                         7:0       0   962.1M   1 loop
/rofs
```

---

### Post by TheFu on 2015-12-26
Appears that sda5 is enrypted, but I don't see any LVs or file systems.  Before going any farther, if you don't have perfect backups make some.

For effective whole system encryption, swap needs to be encrypted tooo, BTW.

---

### Post by pf49 on 2015-12-26
sdc was the hard drive for the computer I built in 2004, sdb was the hard drive for the computer I built in 2008. sda was installed in 2012. When I built the computer I installed just sda, installed Ubuntu 14.04 with encryption, then hooked up the other two hard drives after installation. The intention was to have three hard drives that were each capable of running solo if one of them went down. I trusted Ubuntu to set up the partitions properly, so sda should have everything it needs to operate without the other two being connected. None of them should be accessing partitions on another drive.

I backed up the content of sda to sdb about a week or two ago using the default backup manager. I would hate to lose a few weeks of data, but it wouldn't be the end of the world. If need be I can just try to restore from that backup. Otherwise, how would I go about backing up data from sda since I can't currently access it?

---

### Post by TheFu on 2015-12-27
To backup the data, the encryption must be accessed. Of course, having a bit-for-bit backup could work, provided there isn't anything wrong with any disk sectors under the encrypted partition.

So - boot off a current LTS CDROM/Live Flash - Try Ubuntu. Then open a terminal and run ```

sudo cryptsetup luksOpen /dev/sdf5 enc_disk
lsblk
```
and then, hopefully, the logical volumes will be seen and available to be mounted in the normal way.  Create some temporary mount points for each and mount them as you like.  Then make a data backup. May need to install cryptsetup into the liveBoot/CD environment first.

When it comes to encryption, I never assume that Ubuntu will do what I want. Call me paranoid. Also, if there is any file system corruption, it is usually too late to make backups, so having daily, versioned, automatic, backups is critical.  I've never used the default backup tool - I actually don't run an ubuntu desktop at all anymore.Been using rdiff-backup for 7-ish years happily. The tool or method used doesn't really matter, as long as it works and can actually be restored. Backups are only 10% of the goal. The other 90% are the restores.

---

### Post by pf49 on 2015-12-29
Okay, I tried running that first command and I got "cryptsetup: Unknown action." as a reply. 

I can see the hard drive on the launcher as "1000 GB Encrypted" but when I click on it and enter the encryption password it does nothing. Right-clicking and clicking "Open" does nothing either. I can view the "255 MB Volume" on that drive which appears to have the Grub files and kernel-related information in it. 

And just to make sure I'm doing this right, when it prompts me for the encryption password, it wants the password I enter when I first boot the computer, not the 32-character encrypted Home folder password, right?

---

### Post by TheFu on 2015-12-29
sudo apt-get install cryptsetup

I don't know anything about using a GUI tool for this stuff. No GUIs on servers. Sorry. OTOH, server programs don't completely change every three years either, so most of the commands I learned in 1995 still work either exactly or almost exactly the same way.  IME, GUIs provide 20% of the features of the CLI/shell versions. Often, the GUI tool is NOT created by the core development team, so all bets are off for how well it works.  Reputation for the tool is the best guide that I know.  Don't forget that most of these tools are created by someone with an itch to scratch, not a commercial dev team.

If you can't tell, I'm little use for anything GUI related. Sorry.

---

### Post by pf49 on 2015-12-29
I get: 

```

Reading package lists... Done
Building dependency tree
Reading state information... Done
cryptsetup is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

I also tried running:

```

sudo cryptsetup luksOpen /dev/sda5 unlock

```

Entered the passphrase and got:

```

Cannot use device /dev/sda5 which is in use (already mapped or mounted).

```

---

### Post by pf49 on 2015-12-29
Went into text mode from Grub, attempted to log in and got:

```

ata1.00: exception Emask 0x0 SAct 0x1000000 SErr 0x0 action 0x0
ata1.00: irq_stat 0x40000008
ata1.00: failed command: READ FPDMA QUEUED
ata1.00: cmd 60/08:c0:00:b8:07/00:00:00:00:00/40 tag 24 ncq 4096 in
        res 41/40:00:00:b8:07/00:00:00:00:00/40 Emask 0x409 (media error) <F>
ata1.00: status {DRDY ERR }
ata1.00: error: { UNC }
ata1.00: configured for UDMA/133
sd 0:0:0:0: [sda]
Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
sd 0:0:0:0: [sda]
Sense Key : Medium Error [current] [descriptor]
Descriptor sense data with sense descriptors (in hex):
        72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00
        00 07 b8 00
sd 0:0:0:0: [sda]
Add. Sense: Unrecovered read error - auto reallocate failed
sd 0:0:0:0: [sda] CDB:
Read(10): 28 00 00 07 b8 00 00 00 08 00
end_request: I/O error, dev sda, sector 505856
Buffer I/O error on device dm-0, logical block 0
ata1: EH complete

```

And then it repeats that a few times and stops.

I have no idea what all of that means, but I'm assuming that the one sector being named means a bad drive sector that causes it to fail to be read.

---

### Post by TheFu on 2015-12-29
Bad drive or bad cable or bad {insert-something-bad-connected to drive access}.

With encryption, having great backups is a must.

> Add. Sense: Unrecovered read error - auto reallocate failed
Seems the physical disk has used all the spare sectors already and cannot relocate the next failed sectors, however that might be. Time for a new disk and to restore those backups onto the new disk.

---

### Post by pf49 on 2015-12-30
That's what I was afraid of. I rebooted into Mint, installed testdisk and found that sda5 has 10 bad sectors. I'll try to see if I can fix them temporarily, but until then I'm attempting to restore the backup onto sdb while the new hard drives are in transit. 

Thanks so much for taking the time to walk me through this, I really appreciate it.

---

