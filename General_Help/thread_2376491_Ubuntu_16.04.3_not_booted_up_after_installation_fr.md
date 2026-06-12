---
title: "Ubuntu 16.04.3 not booted up after installation from USB Ubuntu bootable drive"
date: 2017-11-03
forum: General Help
---

### Post by yuezhizhong on 2017-11-03
I was told by someone from Ubuntu Forums, I should forward my questions to above email.

Hi,

I am new in Ubuntu forums. 
When I finished running boot-repair and I uploaded the log file to 
pasetbin ([http://paste.ubuntu.com/25869676/](http://paste.ubuntu.com/25869676/)) 
Even though I successfully get all commands executed and completed I still cannot boot Ubuntu 16.04.03 from SSD ( instead, I stopped at Grub prompt) 
To describe what I did before hitting the problem I also added text to the uploaded RESULTS.TXT ([http://paste.ubuntu.com/25870198/](http://paste.ubuntu.com/25870198/))

However, when I log back to forums account again, I only can see the later posted pastebin (25870198)
I am wondering how I check if I get analyzed answer? 
Can helpers read both tickets all together? 

Let me know what I should do to construct a good question with sufficient detail/information.

boot-repair log files and steps I did attached. If you need more information please let me know.

Thanks for your patience!


-Roger





1. Ran MBR2GPT to convert Windows 10 file format 
2. Make Bootable Ubuntu 16.04.3 into a USB drive
3. Boot Ubuntu from the USB drive
4. Choose "somewhere else" to define four partitions on a newly installed Samsung NVme SSD drive. ("boot" with EFI, "/" with ext4 "/home" with ext4 and swap)
5. From boot options menu, tried to boot from the Ubuntu/SSD 
   but stopped at "Grub>"

6. Ran boot-repair by following three commands:
 sudo add-apt-repository ppa:yannubuntu/boot-repair
 sudo apt-get update
 sudo apt-get install -y boot-repair && boot-repair

 Repairing went smoothly and no error found.

7. tried to boot Ubuntu from SSD again, still stuck at "grub" prompt.

---

### Post by QIII on 2017-11-03
Your email to the Forum Council (the first half of your post) seemed to indicate that you were having a problem seeing your links in a post you had made on the Forums.

As it is now clear that it is not the issue, moved to General Help.

---

### Post by yuezhizhong on 2017-12-07
Did not get any reply up to now, any idea? which post already "resolved" this issue?

---

