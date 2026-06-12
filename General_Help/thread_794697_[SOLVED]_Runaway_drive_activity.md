---
title: "[SOLVED] Runaway drive activity"
date: 2008-05-14
forum: General Help
---

### Post by elamericano on 2008-05-14
At first I thought I was having a problem with firefox, but then I noticed that if I open my ebooks folder in nautilus (with lots of pdfs), it also starts using the drive so much that all my apps become unresponsive and even the arrow gets updated once every few seconds. If I'm able to kill what triggered it soon enough, everything is fine. Otherwise it will soon stop responding at all.

Could it be a problem with swap use? I've fsck'ed my non-swap partitions, with no problems found. Recently I installed another distro on an unused partition to try it out, and I'm reusing the swap partition for that, but that should be ok - I just mention it due to the timing of when this started to happen. It's just as likely to be caused be a recent update.

I listed 'top' once, but nothing was eating CPU cycles, just drive access. Is there a utility to list the file system calls that are happening? I didn't spot the cause by checking my system log. Has anyone had similar experiences in the past? I'd be willing to turn something off to restore system stability, but I'm not sure where to start.

---

### Post by sdennie on 2008-05-14
You could see what's causing the disk activity by doing the following in a terminal:

```

sudo sh -c "echo 1 > /proc/sys/vm/block_dump"

```

Then, do the thing that cuases huge amounts of disk activity then:

```

sudo sh -c "echo 0 > /proc/sys/vm/block_dump"
dmesg

```

You should have a lot of information in dmesg about what is using the disk.

---

### Post by elamericano on 2008-05-15
Thanks, the messages went to syslog, not dmesg, but I see them just the same. Unfortunately, nobody monopolizes the reads. There's 30 messages of one process, then 30 of something else. gnome-panel, pptp, networkmanager, pdflush, nautilus, evince, compiz.real, etc. Almost all the writes are pdflush.

Do you think I can avoid a reinstall?

---

### Post by elamericano on 2008-05-15
Here's the problem:

```
             total       used       free     shared    buffers     cached
Mem:        515028     509176       5852          0       1540      65696
-/+ buffers/cache:     441940      73088
Swap:            0          0          0
```

There's no Swap!! That explains everything. It must have happened when I installed the other distro, which reformatted the Swap partition. But why? The format should still be compatible. Did the uuid change? (Why do we use that instead of /dev/sda5?) Does anyone else know what might have happened?

I still don't know how to fix this, but I'm happy to know what's going on.

---

### Post by elamericano on 2008-05-15
That was it. In /etc/fstab I replaced:

UUID=a306e5a8-f767-4c4b-bdb7-dab5b140c361

with

/dev/sda5

and all is right with the world. I can open tons of apps, and there's less disk activity - and more importantly, it stops after a while.

So, the question is, why on earth would we want to use UUID=a306e5a8-f767-4c4b-bdb7-dab5b140c361, instead of the more reliable and easy to remember /dev/sda5? Is this progress?!

---

### Post by bingoUV on 2008-05-15
UUID still works if you take out two of your hard disks and swap their (SATA/PATA) ports. Device nodes are likely to change then. 

/dev/sdXi still works if you shred/reformat/dd a device. UUID is likely to change in that event.

Choose your evil.

EDIT : 
I guess UUID wins in removable devices. Any number of them could be plugged in so device node cannot be relied upon.

---

### Post by elamericano on 2008-05-15
I see what it's for now - and it's completely inappropriate for my laptop.

I've converted my fstab to /dev/sdax, so I don't expect to be hit by this again.

---

### Post by Yombute on 2008-05-16
Hi Folks,

Man!  I am so new I've still go the shrink wrap on and haven't the first idea what I'm doing...

However, I was getting a ridiculous amount of HD activity with nothing running except the (multitudinous) startup services and figured I might have to ditch linux yet again.

Fortunately, I found this post with a search for Hard Drive Activity and followed the instructions for what to enter into a terminal window.  Evidently,after installing Myth TV and looking around without really trying to get it to work yet, I must have started some process that couldn't complete its task.  At any rate, I have no idea WHY it worked, but after I uninstalled MYTH and all of it's components, the HD activity is almost nil.

There's still hope and I guess I may stick with this for another day...

Thanks for helping without even realizing it!

Yom

---

