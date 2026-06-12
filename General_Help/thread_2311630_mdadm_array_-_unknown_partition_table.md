---
title: "mdadm array - unknown partition table"
date: 2016-01-28
forum: General Help
---

### Post by ylavi on 2016-01-28
Hi

I would welcome any assistance!

I've been using Linux for a long time but I'm finding myself in territory I'm not familiar with and I'm concerned that a wrong step will do a lot of damage.

**Background**

My home server is built from hand-me-down hardware, being upgraded occasionally when I have newer hardware I can use. As far as I remember it's had a RAID-1 setup all along, and I've moved the drives from machine to machine a number of times. Since I haven't seen a particular need to upgrade, and since I haven't had any SATA drives, I'm still using a pair of IDE drives. 

If I remember correctly, the drives are partitioned as follows:

[TABLE="class: grid, width: 500"]
[TR]
[TD]Partition[/TD]
[TD]Array[/TD]
[TD]Used as[/TD]
[/TR]
[TR]
[TD]sd[ab]1[/TD]
[TD]md0[/TD]
[TD]/[/TD]
[/TR]
[TR]
[TD]sd[ab]5[/TD]
[TD]md1[/TD]
[TD]swap[/TD]
[/TR]
[TR]
[TD]sd[ab]6[/TD]
[TD]md2 (?)[/TD]
[TD]/home[/TD]
[/TR]
[/TABLE]

You'll probably tell me that swap shouldn't be mirrored, but that's what I did (on the basis that if I only ended up with one drive my swap would be properly configured), although in recent years I added an old small drive as swap with higher priority.

Due to changes over time the /home partition is a recent change, and I remember that the configuration in mdadm.conf (I think) for md2 was a little different from those of the other drives; from what I can see in my web history it may actually have been md127 and there was something to do with UUID_SUB. I mention this because maybe it's related to my current problem.

I'll mention too (because of things I saw in forum posts) that I only upgraded to grub2 a month or so ago, so the grub configuration for mdadm should have been current, and I believe that I updated my Ubuntu 14.04 installation with package updates then.

**My problem**

Since I changed a case fan a few weeks ago, the server began freezing at intervals (nothing on the screen to indicate problems) and in some cases showing screen corruption during boot. I was a bit too persistent in trying to narrow down the failing component (was thinking PSU but maybe it was the motherboard) and pushing off just moving the drives to another computer due to time constraints until it just wouldn't stay running for long. In the meantime I was tinkering to see if disconnecting one component or other would restore stability. On Sunday I discovered that I had no SMART monitoring going and set up smartd. On Tuesday night I got a message regarding the older of my two drives: "[FONT=Courier New]ATA error count increased from 0 to 2[/FONT] ... [FONT=Courier New]For details see host's SYSLOG.[/FONT]" Unfortunately the system didn't stay up long enough for me to be able to see in the log what the problem was. I'll note that that email was stored in my mail folder within /home, so all partitions were apparently OK at that time.

Last night I finally gave in and moved the drives to a replacement machine. This one only has one IDE controller so I had to put only the two main drives in, as master and slave, rather than a master on each of the two controllers in the dying machine. On the first, normal, boot I could see that that wasn't a wrong move as all three arrays assembled correctly (I *have* done this before). However the boot process stuck with a slow repeat of:

[FONT=courier new]mdadm: Create user root not found
mdadm: Create group disk not found
[/FONT]
If it wasn't exactly that, it was very close; unfortunately I didn't think of taking a photo of the screen.

Since I didn't think much progress was going to happen I restarted the computer and booted into recovery mode. There were some odd aspects - it seemed that I saw the boot messages in order and then the display skipped back to older ones but maybe I was confused. What's for sure - I saw messages about the arrays being recognised, and among them a message like

[FONT=courier new]md2: unknown partition table[/FONT]

At some point (maybe I looked at /proc/mdstat) I saw that md2 was being resynced. Fine. I checked "mount" and saw that md2 was supposedly mounted where it should be on /home but when I looked at /home it was empty. That was enough for me to panic and just shut down the computer straight away (with "shutdown"...). What I read since then basically said "don't do anything you don't fully understand" so I haven't started the computer up again. Today it occurred to me that if there was no lost+found on there, it's not like I suddenly had an empty, clean filesystem there, and perhaps the /home which was empty is actually the empty mount point rather than the mounted volume.

I do have backups on USB drives, but I think the last one I have is from June or so, so I'd like to recover what I can.

[B]My questions
[/B]

[LIST]
[*]Should I just boot again and let the sync finish and see whether /home is properly mounted after all?
[*]Could it be that a sync is making things worse? That's to say: Could it be that sdb6 was OK and sda6 was corrupted and sdb6 is now worse than it was? (On the other hand since it's mirroring sector to sector it shouldn't be spreading the chaos unless sda6 is returning rubbish)
[*]Using a live CD/USB is there a way to see what's on each drive separately without breaking/damaging the array?
[*]If the filesystem is corrupted what is likely to be the best way to repair it?
[*]Can I make a ddrescue copy of the partition and try to repair that? If so, how do I make it? From sd[ab]6 or from md2 after it has synced?
[*]Is there something else I should be trying?
[/LIST]

Thanks!

---

### Post by ylavi on 2016-01-30
I trod carefully and checked the disks from a live USB. All was well, including file system checks.

On reflection, it seems that I relied solely on the output from "mount" and if I had checked /proc/mounts I might have seen that md2 wasn't mounted at all, and that the empty directory I saw would be expected.

I was also told by one user on #mdadm on IRC that he (?) also sees [FONT=Courier New]unknown partition table[/FONT] and, despite that, everything works fine, so it doesn't necessarily indicate an error - in fact I notice that on boot I see that message regarding both md0 and md2.

---

