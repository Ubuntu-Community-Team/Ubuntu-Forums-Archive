---
title: "Problem with installation"
date: 2007-04-10
forum: General Help
---

### Post by Nevtus on 2007-04-10
When I try to install ubuntu I keep receiving an error message saying that the “Load installer component form CD” step has failed. 

Could anyone help me?

---

### Post by ago on 2007-04-10
Can you press alt+f4 to see what component did fail?
Also what version of wubi are you using?

---

### Post by Nevtus on 2007-04-10
Here is the log

> Apr 10  19:14:43  main menu [4779] : (process:5896): 
Apr 10  19:14:43  main menu [4779] : (process:5896): +
Apr 10  19:14:43  main menu [4779] : (pro
Apr 10  19:14:43  loop-install : cannot mount /dev/loop7, giving up
Apr 10  19:14:43  loop-install : Unable to mount loop device
Apr 10  19:14:43  main menu [4779] : cess:5896) : logger
Apr 10  19:14:43  main menu [4779] : (process:5896): - t loop-install
Apr 10  19:14:43  main menu [4779] : (process:5896): Cannot mount /dev/loop7, giving up
Apr 10  19:14:43  main menu [4779] : (process:5896):+ return
Apr 10  19:14:43  main menu [4779] : (process:5896): 1
Apr 10  19:14:43  main menu [4779] : (process:5896): + log
Apr 10  19:14:43  main menu [4779] : (process:5896): Unable to mount loop device
Apr 10  19:14:43  main menu [4779] : (process:5896): +
Apr 10  19:14:43  main menu [4779] : (process:5896): logger – t
Apr 10  19:14:43  main menu [4779] : (process:5896): loop-install
Apr 10  19:14:43  main menu [4779] : (process:5896): Unable to mount loop device
Apr 10  19:14:43  main menu [4779] : (process:5896): +
Apr 10  19:14:43  main menu [4779] : (process:5896): return
Apr 10  19:14:43  main menu [4779] : (process:5896): 1
Apr 10  19:14:43  main menu [4779] : (process:5896):
Apr 10  19:14:43  main menu [4779] WARNING ** : Configuring ‘load-cdrom’ failed with error code 1
Apr 10  19:14:43  main menu [4779] WARNING ** : Menu item ‘load-cdrom’ failed



The version of wubi I'm using is "wubi-7.04-beta-v3".

---

### Post by ago on 2007-04-10
press alt+f2
then:
mount -t ext3 /dev/loop7 /target
(watch the white spaces above!)
see if it works.

---

### Post by Nevtus on 2007-04-10
Ok, when I try that I get the output
```
mount : Mounting /dev/loop7 on /target failed: Invalid argument
```

---

### Post by llukax on 2007-04-10
I'm having this exact same problem. 

Just some info:

1. I'm trying to install wubi on a mac mini (bootcamp windows xp installation) My windows patition is FAT

2. When i first installed the installer detected my firewire external hdd (g:) as wubi's root. I unplugged it and reinstalled but still get the same error with detecting cd-rom. 

3. I selected the "eject" option under the cd installer option and hit alt f4 which read pretty "mounted /dev/loop7 as target" and then resulted in a complete system freeze. at first i thought it was just reading slow from the hdd. Fell asleep for 2 hours and came back but the system was still locked.

---

### Post by ago on 2007-04-10
> **Nevtus said:**
> Ok, when I try that I get the output
```
mount : Mounting /dev/loop7 on /target failed: Invalid argument
```


nano /var/log/syslog
where there any errors when loop7 was formatted (look for mkfs.ext3 /dev/loop7)?

---

### Post by ago on 2007-04-10
> **llukax said:**
> 
2. When i first installed the installer detected my firewire external hdd (g:) as wubi's root.
firewire is not supported

> 3. I selected the "eject" option under the cd installer option and hit alt f4 which read pretty "mounted /dev/loop7 as target" and then resulted in a complete system freeze. at first i thought it was just reading slow from the hdd. Fell asleep for 2 hours and came back but the system was still locked.
did it freeze after you pressed eject? What errors exactly are in /var/log/syslog? (toward the end of the file)

---

### Post by llukax on 2007-04-10
i think i may have found the reason why its having trouble mounting the disk image. FAT32 only supports files up to 4 GB in size. Maybe thats why?

---

### Post by ago on 2007-04-10
> **llukax said:**
> i think i may have found the reason why its having trouble mounting the disk image. FAT32 only supports files up to 4 GB in size. Maybe thats why?

Yes that's why, but I am surprised since beta-v3 should not create files greater than 4GB on FAT partitions.

---

### Post by llukax on 2007-04-10
hmmm. the file i had must have been incomplete. it was only 4 gb. well i'm off to reinstall windows as soon as the ubuntu torrent is finished re-downloading. i'll let you know what happens.

---

### Post by Nevtus on 2007-04-10
> **ago said:**
> nano /var/log/syslog
where there any errors when loop7 was formatted (look for mkfs.ext3 /dev/loop7)?

From what I could tell loop7 was formatted without any errors.

Btw, my hard drive is FAT32 as well so that is probably the cause of the problem.

---

### Post by ago on 2007-04-10
> **Nevtus said:**
> 
Btw, my hard drive is FAT32 as well so that is probably the cause of the problem.
Quite likely

---

### Post by Nevtus on 2007-04-10
Converted my drive to NTFS and everything worked :-)

---

### Post by llukax on 2007-04-11
It works with NTFS. Problem solved! :)

---

### Post by ago on 2007-04-11
It's important for us to know what size where the disk images under FAT32. Were they about 4GB or much larger?

---

### Post by llukax on 2007-04-11
the size was about 4.1 GB i believe. Sorry for the delay.

---

### Post by ecology2007 on 2007-04-12
> **llukax said:**
> the size was about 4.1 GB i believe. Sorry for the delay.
Thanks for the report, the file was probably 1 byte too big for FAT32. 
The change has been comitted for coming revisions.

---

