---
title: "rsync First Timer Needs to Backup Failing Machine"
date: 2007-09-16
forum: General Help
---

### Post by moon2js on 2007-09-16
Hi there,

I have a failing Apple iBook with OS X Tiger. It randomly loses power (while plugged in) anywhere between 2 minutes and 2 hours after the startup chime. I'm sending it off for repair as soon as I can back up my home dir on it.

I've been poring over mans and tutorials on rsync and I've got it running now, but I figure it's gonna lose power a number of times before it finishes. I've got about ~60gigs to get off the iBook onto my 'buntu box. I'm wondering if any of you more experienced users can check my work and if you see anything that can be corrected, please let me know so I can update my method after the next power loss.

Basically, I'm looking for quickest but thorough backup of my entire home dir, no compression and no encryption (over a wired ethernet router-managed LAN). I figured I could drop compression because I have plenty of space on the target computer and compression would slow down the process. Also, I need it to pick up from where it last left off.

[just lost power, restarting trying again...]

I set up and run rsyncd on my Ubuntu machine as per [this tutorial]("http://rsync.samba.org/ftp/rsync/rsync.html"), so it has very basic config.

And I ssh into the iBook from ubuntu and run:

```
rsync --verbose  --progress --stats
      --recursive --times --perms --links
      /Users/myname/* ubuntu:backup
```

Any constructive criticism? Am I doing it somewhat correctly? Is there a better way?

---

### Post by JinxAu on 2007-09-16
Gday Moon2js,

Rsync aside, you should be able to remove your HDD (Apple provide documentation on their website on how to do this) and get a 2.5inch -> 3.5inch IDE converter (if the drive is IDE), then backup the drive by plugging it into one of your desktops. I haven't had much experience with 2.5inch SATA drives, though I assume they use the same connector as their 3.5inch counterpart.

Sometimes you will get better results with laptop power issues by removing the battery and running the system off mains power only.

In regards to rsync, it takes up a lot of RAM and CPU, so if you're having an overheating issue, it's definitely going to cause the system to reboot. It has been recommended to me before to try throttling rsync so it uses less bandwidth (assumable this slows the CPU and RAM usage down as well). So, maybe try using:
>  --bwlimit=KBPS          limit I/O bandwidth; KBytes per second

Cya round
Jinx

---

### Post by moon2js on 2007-09-16
Thanks for the tip.

I would try the IDE converter trick if the iBook were not still under warranty (and I'll definitely try that on my friend's dead laptop). But my computer seems to be having a problem with its Power Management Unit or logic board that cuts off the power randomly. I've been using the laptop with the battery completely removed ever since this problem first cropped up.

As far as I can tell my CPU is fine, RAM is plentiful, and heat is within normal operating parameters. The random power losses seem pretty random, happening even when I'm not doing anything intensive.

---

### Post by JinxAu on 2007-09-16
I would double check with Apple, but I am pretty sure you can replace HDDs and RAM without voiding warranty. At least that's what I am lead to believe. I have opened up my Macbook before just to see how easy it was to get at the RAM and HDD. There is no sticker or such declaring warranty to be void if removed. 

Cya round
Jinx

---

### Post by moon2js on 2007-09-16
Oh, but I would like some confirmation that I'm using the right tool for the job.

Normally I'd use samba or something to transfer files across the LAN, but since the computer randomly loses power, I need something that can pick up where the last attempt left off and makes sure all files are intact, not partially copied over. With samba, I'd have no idea what I had copied over and would have to restart the copying.

---

### Post by JinxAu on 2007-09-16
Yep, rsync is probably the best option for intermittent copying... just tedious (as you have probably found) if the computer is rebooting all the time. :\

Cya round
Jinx

---

