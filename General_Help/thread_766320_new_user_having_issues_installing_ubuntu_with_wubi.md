---
title: "new user having issues installing ubuntu with wubi"
date: 2008-04-25
forum: General Help
---

### Post by hilad on 2008-04-25
Hey, I'm having problems installing ubuntu 8.04 with wubi. The installation part with windows works fine but when it boots my computer freezes when it reaches:

formatting swap space in partition #1 of host/ubuntu/disks/...

I tried launching it in verbose mode and when it froze I pressed
ctrl + alt + f1 and the last line says starting ubiquity...

I could really use some help with this!

---

### Post by ago on 2008-04-25
please boot in verbose mode (press esc at boot after ubuntu), and post c:\ubuntu\installation-logs.zip here: [https://bugs.launchpad.net/wubi/+bug/206113](https://bugs.launchpad.net/wubi/+bug/206113)

---

### Post by hilad on 2008-04-25
OK I'm doing that now

---

### Post by ago on 2008-04-25
hmm the relevant log is C:\ubuntu\installation-logs.zip

Boot in verbose mode (press esc after selecting ubuntu)
When it jams, press ctrl+alt+f2 and run

sudo sh /custom-installation/hooks/failure-command.sh

reboot into windows and post C:\ubuntu\installation-logs.zip

---

### Post by sixsidepentagon on 2008-04-25
Hey hilad, I had the same problem. But when I went into verbose mode, and it definitely paused at Ubiquity, but after a minute or so, it launched into the GUI. So I would try verbose mode again and wait for a few minutes to see if it's really freezing.
But I still have the problem where it freezes at 
formatting swap space in partition #1 of host/ubuntu/disks/...
Anyone who can help would be greatly appreciated!

---

### Post by rainpl on 2008-04-26
I've got exact the same problem. 

I was installing Ubuntu 8.04 with Wubi. Windows part went fine and after reboot Ubuntu installer kicked off, checked the installation status and started formatting swap partition. That's where it stopped (I've been waiting 3 mins.) with 0%.

Logs in attachment.

Thanks!

---

### Post by jillesvangurp on 2008-04-26
I have the same issue with the final LTS released this week. However, it occurs only with the 32 bit 386 version and not with the AMD64 bit version. The 386 version always blocks at this point.

I was able to install the 64 bit version without blocking. However, I will need the 32 bit version due to driver issues (nvidia).

---

### Post by rainpl on 2008-04-26
Ok, I managed to cope with it. Suprisingly it could have something to do with fragmentation of the Windows drive...

Here's what I did:
-uninstalled Wubi
-installed Wubi on another partition

Now it works!
So if it doesn't work you can try to defragment your HDD.

---

### Post by mataal on 2008-04-26
@rainpl: thanks for the tip... am trying that out now...
defragging my single HDD with JKDefrag... fingers crossed.

---

### Post by Nikell on 2008-04-26
I had the same issue.

I defraged three consecutives times with JKDefrag (My HDD was reaaallyy messy) then following Ago's advice I deleted swap.disk and using "fsutil" i created a new file of ~100Mb who wasn't fragmented.

It worked :] (Now I have another bug, but at least is not a swap space in partition problem :D)

Thanks Ago, and the others :)

---

