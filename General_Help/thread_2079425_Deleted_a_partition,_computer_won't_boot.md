---
title: "Deleted a partition, computer won't boot"
date: 2012-11-01
forum: General Help
---

### Post by Jt00 on 2012-11-01
I was repartitioning my hard drive. I had had backtrack on a partition previously, but it was deleted when I upgraded Ubuntu via flash drive because of networking issues with 12.04. I was going to use the backtrack partition for a backup area to reinstall windows 7 if windows 8 turns out to suck. Since the windows disk manager wouldn't tell me anything about the partitions, I went to Ubuntu. After deleting the backtrack partition (/dev/sda4) I rebooted to go back to windows and upgrade. But instead I get a "grub rescue" command line. I am positive I did not delete the boot partition - it was 96 gb. Before I did anything to the disks, I got an error message saying Ubuntu 12.10 has experienced an internal error. I reported it and thought nothing of it since the system appeared to continue working properly. I am now on a live USB. How do I remount everything?

I know for sure that windows is sda1, win recovery is sda2, and Ubuntu is sda5. I deleted sda4. Please help!

---

### Post by Jt00 on 2012-11-01
Actually, while I was in the grub rescue I did something incredibly stupid. I overwrote windows with a boot partition. Oh well, at least I have the disks I need to reinstall it, and I didn't lose any files I just can't live without, since I've only had the computer a couple of months. Looks like I'll be reinstalling everything now. Thanks anyway.

---

