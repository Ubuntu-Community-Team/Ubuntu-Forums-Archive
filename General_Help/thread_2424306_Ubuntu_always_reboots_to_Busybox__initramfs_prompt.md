---
title: "Ubuntu always reboots to Busybox / initramfs prompt"
date: 2019-08-06
forum: General Help
---

### Post by thinqer77 on 2019-08-06
Hello,

I'm relatively new to Ubuntu but have been making good progress on getting to grips with it however this one has me a little stumped.

I have Ubuntu 18.04 (Desktop not Server) installed on a 120GB SSD. There are no other operating systems installed on the disk and I think I picked all of the default options during installation.

I'm running a few server application on there and it's been running generally very smoothly for a few months, but recently I've found that every few days something happens that means I get error messages in some of the web apps I'm running (like UrBackup and Grafana) along the lines of 'unable to write to disk'. When I reboot, the system drops to a Busybox environment and initramfs prompt. When I type 'exit' at the prompt I get the following:

[ATTACH=CONFIG]283743[/ATTACH]

I then run fsck on the /dev/mapper/ubuntu-vg-root folder (with the -y option) and it seems to find and fix a lot of orphaned inodes (see below for screenshot):

[ATTACH=CONFIG]283745[/ATTACH][ATTACH=CONFIG]283744[/ATTACH]

If I then do a reboot it boots just fine and will continue to run for a few days until it happens again.

I think I ran a SMART test on the disk and it seems fine, although I've not done any more testing beyond that. I have read other articles suggesting that an improper shutdown can cause inode issues, but as far as I'm aware the system isn't shutting down - any way to check this? I don't think the disk is full.

So, does anyone know what could be causing this? If so, are there any know fixes I could try?

I haven't checked any logs as I'm not sure where they are or which ones to check but happy to share if it helps. Likewise am happy to provide any other information that would be useful as long as you tell me how to get it!

Many thanks in advance for your help!

---

