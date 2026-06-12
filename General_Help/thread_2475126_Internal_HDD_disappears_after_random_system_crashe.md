---
title: "Internal HDD disappears after random system crashes"
date: 2022-05-17
forum: General Help
---

### Post by swampsnake on 2022-05-17
Hi all.  I have a small Lenovo desktop workstation setup as a headless Ubuntu file server.  It has a 1TB SSD boot drive and an 8TB HDD data drive., originally running 18.04.  For the past few days I have been getting random crashes where the system appears to reboot itself and the internal drive is no longer visible and doesn't show up anymore. If I manually rebooted the server the drive would re-appear for a while until it crashed again.

I assumed it was a faulty drive so ordered another HDD (this time a 12TB) but I have exactly the same issue.  I have swapped the sata and power cables around, and also the sata ports the drives are plugged into but it always reacts the same - a self reboot after a random amount of time and the HDD not showing anymore.  
I have also upgraded to 20.04, but again I have the same problems.

I have tried looking in the logs but I'm struggling to know where to look, and what to look for so I would be grateful if anybody could point me in the right direction. I'm not sure now whether I'm chasing a hardware or software issue and it's driving me slight mad!

---

### Post by #&amp;thj^% on 2022-05-17
If A large amount of IO or excessive read and write operations,  see if this checklist helps identify anything: [https://askubuntu.com/questions/1243536/ubuntu-20-04-fails-to-write-on-hard-disk-and-freezes-shows-i-o-error](https://askubuntu.com/questions/1243536/ubuntu-20-04-fails-to-write-on-hard-disk-and-freezes-shows-i-o-error)
Also I found anything above * 8TB's a problem in just dropping the drive/s for no reason.
I have two 4 TB's drives now acting nicely. Why? IJDK
Also your logs should be in "/var/log/syslog*"
Also I added a  8 gig swap file.

---

### Post by dragonfly41 on 2022-05-18
Intuitively,  would look at the common factor which has not changed .. firmware.

[https://support.lenovo.com/gb/en/solutions/ht003029-lenovo-system-update-update-drivers-bios-and-applications](https://support.lenovo.com/gb/en/solutions/ht003029-lenovo-system-update-update-drivers-bios-and-applications)

There are of course other common factors to consider such as motherboard but I would start with the easy tests/upgrades.

And what do you see when your run LiveUSB for a period? Same issues? If not you might get Ubuntu running via USB port (as I am running now, as I write).

[P.S.] Another common factor is RAM. Try running a memory test. Could be a faulty RAM card.

---

### Post by swampsnake on 2022-05-18
Thanks for the pointers. I have almost all the hardware disconnected now and it is still doing it so the next step will have to be a fresh install of the OS i guess. I was hoping to avoid that but I'm running out of ideas.

---

### Post by dragonfly41 on 2022-05-18
LiveUSB test and memory test first, or you might be on a wild goose chase.

---

### Post by swampsnake on 2022-05-18
Good call!  I'll get stick-prepping

---

### Post by Autodave on 2022-05-18
Bad RAM is also likely......will cause that same condition.

---

### Post by oldfred on 2022-05-18
You can check logs for issues:
Review log files
sudo egrep -i 'warn|error' /var/log/*g

But I have a couple of pages of issues, none are really issues.

---

