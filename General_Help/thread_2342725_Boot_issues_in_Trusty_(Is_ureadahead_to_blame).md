---
title: "Boot issues in Trusty (Is ureadahead to blame?)"
date: 2016-11-09
forum: General Help
---

### Post by Scary Rob on 2016-11-09
Some context: I think my boot has always been slightly buggy. My monitor blanks (no input > go to standby) after the computer's own start screen, so I don't see the grub menu or the loading dialogues. Vision just sort of kicks in again at the login screen.

Lead up: when I last ran an update over the weekend, ureadahead said it needed a system reboot, where it would make some change or other that I can't now recall. The next time I booted up after the restart, my monitor was on standby for longer than usual. I pressed the up and down keys and found a dialogue reporting a couple of errors that soon cleared to the login screen.

The actual problem: Now when I switch on, once I've pressed a key or two to actually see what's going on after it seems to have been taking a while, I might catch the Kubuntu logo (I'm using kubuntu 14.04) followed by:

(each line below is preceded by a number in square brackets, formatted [ xx.xxxxxx], but I assume that's some kind of boot order or time stamp)
```
ata1: softreset failed (1st FIS failed)
```  for a couple of lines, then
```
ata1.00: revalidation failed (errno=-5)
```

This repeats for a little while, before:
```
INFO: task init:1 blocked for more than 120 seconds.
      Not tainted 4.2.0-42-generic #49"14.04.1-Ubuntu
"echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
```

And the same for the following tasks:
```
kworker/u8:6:152
plymouthd:187
jbd2/sda2-8:211
rs:main Q:Reg:889
NetworkManager:911
find:1129
```

I then get the softreset and revalidation errors again for a few lines followed by:
```
Buffer I/O error on device sda2, logical block 82968577
```
for several lines. The number at the end is different for each line.
Then:
```
Aborting journal on device sda2-8.
EXT4-fs (sda2): previous I/O error to superblock detected
EXT4-fs error (device sda2): ext4_journal_check_start:56: Detected aborted journal
EXT4-fs (sda2): Remounting filesystem read-only
```

I then get:
```
EXT4-fs (sda2): previous I/O error to superblock detected
EXT4-fs error (device sda2): __ext4_get_inode_loc:3955: inode #5637346: block: 82837555: comm NetworkManager: unable to read itable block
```
a few times with different inodes (and possibly different blocks).

Then:
```
JBD2: Error -5 detected when updating journal superblock
```

followed by a few more EXT4-fs errors, then lines of:
```
init: Error while reading from descriptor: Bad file descriptor
```

Finally, I get a load more of the inode notifications before the process seems to hang completely.

As you can imagine, I'm baffled. I've googled around this and can't find anything that appears relevant. The softreset business, for example, turns up an Arch forum thread attributing the problem to an update to kernel 3.16....

Any insight gratefully appreciated.

---

### Post by Scary Rob on 2016-11-10
Update:

I tried
```
sudo sed -i 's+^start on starting mountall+start on mounted MOUNTPOINT=/var+' /etc/init/ureadahead.conf
``` as suggested here: [https://ubuntuforums.org/showthread.php?t=1518110&p=9555086#post9555086](https://ubuntuforums.org/showthread.php?t=1518110&p=9555086#post9555086)

I'm not sure that it was the same problem exactly, but my desktop booted up without issue just now. If it continues to boot smoothly over the next couple of days, I'll mark this as solved.

---

### Post by Scary Rob on 2016-11-12
Five boots in a row with no issues. This seems to have worked.

---

