---
title: "Partition Table (GPT) damaged while reading from disk?"
date: 2018-12-03
forum: General Help
---

### Post by helmut-mon on 2018-12-03
First of all: I got it repaired (from restoring partition table). My partition table was suddenly damaged. This happened during a disc cloning operation with dd after 5 of 8 TB were already transferred.

I want to understand why this happened - is this possibly a hardware/raid issue? I've never heard of problematic disc/data corruption during read operations.

Here's what I did:

- I wanted to clone my main 8TB-Backup-Raid(1) to another Homelab-Server, also 8TB-Backup-Raid (this is the 2nd Backup that moves to a physically separate location).
- on the **receiving server (S2)**, I started ```
 nc -l 5670| dd if=/dev/stdin of=/dev/sda bs=8M status=progress
```
- on the **sending server (S1)**, I started ```
 dd if=/dev/sda of=/dev/stdout bs=8M | nc 192.168.1.4 5678
```

It was reporting the transfer for about 24 hours when S1 shell suddenly was waiting for input again, the dd command quit without notice. I checked and noticed that /dev/sda/ does not exist or cannot be accessed.
- I repaired it with **gdisk -r** (recovery), **gdisk -c** (load from backup on disk) and **gdisk -w** (write to disk)

So far, so good. But why? How can a simple read operation corrupt my partition table? Should I run a complete hard drive test, raid tests etc.? Was it perhaps the memory, or could this happen when network cable/ netcat choked (I hope not)?

The data on the raid is important to me. I currently don't understand what is going on, so I think I will try transferring the data with rsync in little chunks first and not with dd.

I have:
Ubuntu 1804 (S1)
Proxmox Debian (S2)
All updates to date.

---

### Post by HermanAB on 2018-12-03
I don't know exactly why your disk got corrupted, but:

a.  You were reading/writing from the same disk that you were running from?  That means that you were reading/writing a changing target, so the clone likely would not have worked anyway, even if the process terminated normally.

...and from the superfluous use of dd department (I've been guilty of that too!):
b. Instead of using dd with its somewhat confusing syntax, you can just let netcat do its thing without dd.

Assuming that you are running off a CDROM or memory stick:

# nc -l 5670 > /dev/sda

# nc 192.168.1.4 5678 < /dev/sda

---

### Post by helmut-mon on 2018-12-03
> **HermanAB said:**
> 
a.  You were reading/writing from the same disk that you were running from?  That means that you were reading/writing a changing target, so the clone likely would not have worked anyway, even if the process terminated normally.


I don't exactly understand what you mean, could you explain this? I was reading from **/dev/sda** with **if=/dev/sda**, sending it over netcat to my 2nd Server and writing to **/dev/sda** with of=**/dev/sda** (yes, both servers have a similar setup and both 8TB Raids are **/dev/sda** - this surely doesn't mean I was reading and writing from and to the same disk/raid? (I saw the status=progress report report until 5TB was transferred).[COLOR=#000000][FONT=&quot]
[/FONT][/COLOR]
> 
...and from the superfluous use of dd department (I've been guilty of that too!):
b. Instead of using dd with its somewhat confusing syntax, you can just let netcat do its thing without dd.

Good idea, I've never heard about this but others were using pv, cat etc. to clone disks. however, I felt most secure with the (much tested) dd command.

> 
Assuming that you are running off a CDROM or memory stick:

# nc -l 5670 > /dev/sda

# nc 192.168.1.4 5678 < /dev/sda

Both Raids are not where my os is on - the os drives are **/dev/sdb **and I am running directly from shell.

Many thanks for these commands!

---

