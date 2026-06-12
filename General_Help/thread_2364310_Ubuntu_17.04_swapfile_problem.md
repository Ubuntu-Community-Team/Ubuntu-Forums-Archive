---
title: "Ubuntu 17.04 swapfile problem"
date: 2017-06-21
forum: General Help
---

### Post by BigCityCat on 2017-06-21
Problem started after I hard powered off Ubuntu while my ntfs partition was mounted.

After restarting I began getting failed to activate swapfile cryptswap dependency error messages and I could not login. I have a work around by using recovery. dropping to root shell and entering swapoff --all. Then I can continue boot but I only get the choice to login to X session. no wayland session available. Here are a few commands from my limited knowledge.

cat /proc/swaps
Filename				Type		Size	Used	Priority

sudo swapon --all
swapon: cannot open /dev/mapper/cryptswap1: No such file or directory

grep swap /etc/fstab
/swapfile                                 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
# a swapfile is not a swap partition, no line here
#   use  dphys-swapfile swap[on|off]  for that

swapon -s
Filename				Type		Size	Used	Priority
/swapfile                              	file    	262140	0	-1

---

### Post by TheFu on 2017-06-21
Did you install whole drive encryption during the install?  What is the output from **lsblk**?
Please use *code tags*, so things line up.

---

### Post by BigCityCat on 2017-06-21
> **TheFu said:**
> Did you install whole drive encryption during the install?  What is the output from **lsblk**?
Please use *code tags*, so things line up.

Hey thanks. I had a few more problems so I re installed. Everything is backed up. Didn't take long.

---

