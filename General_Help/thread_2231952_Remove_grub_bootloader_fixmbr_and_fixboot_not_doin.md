---
title: "Remove grub bootloader /fixmbr and /fixboot not doing anything"
date: 2014-06-29
forum: General Help
---

### Post by Ryan_ on 2014-06-29
I tried out Ubuntu on a dual boot and i decided dual booting was not working for me, so i'm trying to remove it and get back to normal. So i followed a few tutorials online and deleted the swap and ubuntu partition, and then I make a recovery USB using windows 8's 'Create a Recovery Drive' tool, and then restarted my computer. Upon booting, i was greeted with Grub's command interface. Unsure what to do, i googled it and someone suggested using the exit command and i was brought to a screen where i could choose different devices to boot from, i tried the windows bootloader option, and that worked, I tried the Ubuntu option and that brought me back to the grub command line, and i tried the USB option and that brought me to a recovery screen for windows where it asked me to choose a language just like in the tutorials. The part that is different and i don't understand is on the tutorials, the next screen is always where it gives you an option to install windows 8 or repair windows 8. I don't get that option. For me, it is either troubleshoot or continue to windows 8. In the troubleshoot menu, i found my way into the command prompt just like in the tutorial, and executed ```
bootrec.exe /fixmbr and bootrec.exe /fixboot 
``` both of these said they were successful, so i exited out of the command prompt and clicked continue to windows 8. Doing this brought me back to the grub command line. I tried restarting my computer to see if that would work, but it too brought me to the grub command line. What am i doing wrong and how can i fix it? I want grub bootloader gone and for my computer to boot into windows normally.
Any help or suggestions is greatly appreciated. Thanks.

---

### Post by lisati on 2014-06-29
Please do not start multiple threads for the same question, it dilutes the community's ability to help.

Duplicate of [http://ubuntuforums.org/showthread.php?t=2231861](http://ubuntuforums.org/showthread.php?t=2231861) closed.

---

