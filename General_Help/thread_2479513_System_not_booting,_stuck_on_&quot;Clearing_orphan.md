---
title: "System not booting, stuck on &quot;Clearing orphaned inodes&quot; screen"
date: 2022-09-27
forum: General Help
---

### Post by phm5024 on 2022-09-27
[COLOR=#1A1A1A][FONT=&quot]I have a Ubuntu/Windows dual-boot. When I boot Ubuntu, I get a screen that says:[/FONT][/COLOR]
```
/dev/nvme0n1p2: recovering journal 
/dev/nvme0n1p2: Clearing orphaned inode...

```[COLOR=#1A1A1A][FONT=&quot]I have been using this dual-boot system for a couple of years and have not encountered this issue before. I have seen this screen before but in the past I have been able to reboot and the problem goes away.[/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=&quot]I have tried a number of solutions based on responses from old forum threads on similar issues. In the terminal in Recovery mode, I ran sudo apt update, sudo apt -f install and sudo apt autoremove.[/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=&quot]I also tried doing a fsck. When I do this I get the following output in the terminal:[/FONT][/COLOR]
```
/lib/recovery-mode/recovery-menu: line 80: /etc/default/rcS: no such file or directory 
fsck from util-linux 2.31.2 
/dev/nvme0n1p2 is mounted. 
e2fsck:Cannot continue, aborting.

```[COLOR=#1A1A1A][FONT=&quot]I have tried restarting a number of times and each time I get the same "Clearing orphaned inodes screen". A couple of times I got "Clearing orphaned inodes" along with another message that said "BIOS contains WGDS but no WRDS". But again, I only got this message twice out of maybe 20 times rebooting.[/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=&quot]Any help would be greatly, greatly appreciated. I have deadlines coming up which I need to use Ubuntu for and am getting desperate.[/FONT][/COLOR]

---

### Post by tea for one on 2022-09-28
> **phm5024 said:**
> 
```
fsck from util-linux 2.31.2 
/dev/nvme0n1p2 is mounted. 
e2fsck:Cannot continue, aborting

```
You have to unmount the partition to use fsck.

Boot into a live session.
Back up your data from both Ubuntu and Windows (if you haven't already done so)
Open a terminal and identify your Ubuntu partitions with:-
```
sudo parted -l
```
```
sudo fsck /dev/nvme0n1p2 - [COLOR="#0000FF"]make sure that you have selected the correct partition[/COLOR].
```

---

