---
title: "Boots Kernel OK, but only to # prompt?"
date: 2006-10-09
forum: General Help
---

### Post by irv on 2006-10-09
I have been using Ubuntu 6.06 for sometime now with no problems. I restarted the PC today but it will not boot into graphic mode. Here is what I get after restarting the PC.

> Boots Kernel OK
mount: mounting /dev/hda2 on root failed: No such device
mount: mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/int

Busybox v1.01 (Debian 1:1.01-4ubuntu3) Built-in shell (ash)
Enter 'help' for list of build-in commands.
/bin/sh: can't access tty; job contdrol turned off
#
Is there a way to fix this problem without doing a re-install. I have some much setup that would need to be re-done if I have to re-install. I am not sure what happen. No new software or hardward was added, all I did was restart the pc.
By the way it does the same thing if I try to boot with older kernels. I can boot into kubuntu and winxp from grub but can't get ubuntu 6.06 to boot.
Can anyone help? 
Thanks.

---

### Post by aldegaz on 2006-10-09
Its like its not recognizing your hard drive (hda2)

I havent seen anything like this overnight...

---

### Post by cilynx on 2006-10-09
I agree.  It looks like your hard drive tanked.  Check your primary master (hda) in a different machine or at least make sure the cables are tight.

---

### Post by irv on 2006-10-09
I only have one hard drive in the system, and all the other OS' boot OK, so I don't think the hard drive is bad. Like I said it comes up to the grub, and I can get into kubuntu and winxp, it is just ubuntu 6.06 I can't get up. I thought there was some command I could try at the # prompt? Maybe my boot partition for ubuntu got messed up. I hope this is not the case.

---

