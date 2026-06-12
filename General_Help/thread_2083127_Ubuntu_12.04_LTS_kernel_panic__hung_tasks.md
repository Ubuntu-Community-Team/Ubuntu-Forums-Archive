---
title: "Ubuntu 12.04 LTS kernel panic / hung tasks"
date: 2012-11-11
forum: General Help
---

### Post by smannem on 2012-11-11
Hi,
I was hoping someone might be able to help me out a bit.
I am develloping a website and want to host it from a home server.
I have a ML370 G4 and I'm having some stability issues.
Once in a while (about every day) the server would start to run slower and slower, until it hung.
During the running slower I found out that I could not kill -9 processes.
Furthermore the display shows the following error for some processes: task hung for more than 120 seconds.
I have also registered this as a bug: [https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/1077688](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/1077688).

I have changed some stuff to solve this issue, but have not solved it yet:
- I started out whith Fedora F16, but soon decided that I'd feel more for ubuntu (12.04 LTS 64 bit) and hoped to get rid by changing the distro at the same time. After changing to Ubuntu 12.04 the server run stable for about 3 days. Then the issues started again.
- I changed from btrfs to ext4 (created ext4 partitions, copied and deinstalled btrfs-tools). The issues remained.
- I found that there were many SSH attempts (aout 14000 in one day from one IP). I filtered them out with IPTables. Since then the performance of the server is
 very good, but the issues remained.
- I have ran a memory test (choose memtest during boot from grub menu). It ran for about 8 hours en gave no errors.
- I have not yet ran a CPU test, but I'm not convinced that this might be an issue.
- I changed to the older kernel 3.2.0.29 (the one that run stable for 3 days). The server ran stable for 3 days, but the showed the same issue (so less often, but the issues remained).
- At this moment I have installed 3.4.0-03 and I'm checking to see how long that will last.
- I have also changed the kernel settings so that hung tasks initiate a kernel panic (kernel.hung_task_panic>0), and that kernel panic initiate a reboot (kernel.panic>0).
- And I have blacklisted te btrfs kernel module (it was still loaded for some unknown reason).

I have been googling for hours and found much interesting info of which some things have been applied (see above).
But for as fare as I am aware, the issues still remain (I will celebrate when the server has an uptime of more than 5 days straight).
I hope that someone might shed some light on some things:
- Can the above issues come from the btrfs module?
- Is there someone that might have any idea on why this issue is far worse with kernel 3.2.0.32 than whith 3.2.0.29? Is this a know issue, is this resolved with a newer kernel version? When might we expect a newer one available in Ubuntu 12.04?
- Should I switch to 3.4 (if I have no issues whith 3.4)? What might be the drawbacks of using 3.4 instead of 3.2 kernel? I use old hardware, should I use an older version instead of a newer version? Perhaps 10.04?
- Are the other people having the same issues as that I have? With what kind of hardware? Is this a known bug?
- Can anyone give some extra info on the mechanism of the kernel and tasks? Why is a hung task so problematic?

I want to ask anyone that might have some info that might help me to solve this issues to reply to this thread.

Please help me...

---

### Post by gordintoronto on 2012-11-11
I don't have a solution. How old is this computer? I found a review from 2011, which is not long ago.

I think 12.04 will stay with the 3.2 kernel for its entire life. 12.10 uses the 3.5 kernel, which might be worth a try.

My personal view is that a home server for a web site is a bad choice. I can put a web site on Go Daddy (or numerous other hosting companies) for about $75 a year, including the domain registration. My rule of thumb is that computer technology is good for 7 years, so if I paid more than $400 for the computer, the value is extremely marginal.

Besides which, most ISPs don't let you host a web site, under their terms of service.

---

