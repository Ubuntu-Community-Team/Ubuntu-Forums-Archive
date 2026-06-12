---
title: "Cannot connect to lvmetad error"
date: 2019-06-16
forum: General Help
---

### Post by poplarlucrative on 2019-06-16
I am having an issue, while switching from my user account to my root account, my computer froze up(It actually went to a black screen with a blinking cursor in the top left corner). I powered the machine down. When it rebooted I was able to input my fde key but it then gave me the error  "cannot connect to lvmetad. Falling back to device sccanning. Reading all physical volumes. This may take a while... Found volume group "ubuntu-vg" using metadata type lvm2 Warning: failed to connect to lvmetad. Falling back to device sccanning. 2 logical volumes in volume group "ubuntu-vg" now active /dev/mapper/ubuntu-0vg-root: clean, 250690/7675904 files, 29159900/30682112 blocks"  I am running ubuntu 18.04 with FDE. I have seen a few posts to turn off lvmetad though I dont know how to get to the file editor from here.  I believe my issue may be addressed in this issue: Failed to connect to lvmetad - Stuck on boot the poster sssascha mentioned that his disk was full. Just a few moments before I switched from my standard account to root, I saw I had a notification that I was running out of space. I was in the midst of switching to root to change up the disk partition space when this all occurred.  Thats all the context I have. I dont know where to run the command for df to check my disk space. Any help is appreciated.

---

