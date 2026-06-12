---
title: "Ubuntu 8.04 will not boot in normal mode"
date: 2008-07-05
forum: General Help
---

### Post by gordon3913 on 2008-07-05
Ubuntu 8.04 kernel 2.6.24-19-generic
When booting I get a warning that the system is unable to resolve the UUID.
It asks me to type Ctrl D to continue and run fsck later.
It continues to the login screen but when I try to login it stays that it is unable to find my /home and asks me to boot in safe mode.
When booting in "recovery mode" I get a message to try and fix my Xserver, which I run and I can boot into the system.
Next time I boot I get the same problem.

in /var/log messages I noticed a line:-
Local APIC disabled by BIOS -- you can enable it with "lapic"
How do I do this and is this my problem to fix to a normal boot?

---

### Post by Elfy on 2008-07-05
You could check the UUID for your partitions I suspect that one has chnaged, have you recently done any work with partitions?

Boot into recovery mode - then when you get the small menu - choose drop to root prompt.

Run first command to get your UUIDs, then check the UUIDs with the second. If nay of them do not match you will need to edit the file.

```
blkid
cat /etc/fstab
```

If you need to edit the file you can use nano from the prompt, Ctrl+O and enter to save, Ctrl+X to exit.

```
nano /etc/fstab
```

Be careful that you enter the UUID correctly if it is needed.

I'm afraid I don't know about the lapic problem.

---

### Post by plucky on 2008-07-05
Have you been changing your partitions?

> When booting I get a warning that the system is unable to resolve the UUID.


The UUID for one of your partitions has changed and it is probably your **home** partition.
As it won't let you login,you can either boot the LIVE cd to fix the problem or boot to the root shell in recovery mode and fix the problem there.

In recovery mode ```
blkid
``` will show you the UUIDs of all your partitions.Make a note of each UUID as you will need to compare them to the ones in your fstab file.

To edit your fstab file ```
cp /etc/fstab /etc/fstab.old
nano /etc/fstab
```

The first command makes a backup copy of your fstab file..
And change the UUIDs of each partition that doesn't match the ones given by **blkid** command.

Remember you are in super user mode,so make sure you are careful.

After you have finished you can reboot by ```
shutdown -r now
```

Good Luck

Beaten by forestpixie

---

### Post by gordon3913 on 2008-07-05
Problem fixed.
I checked the Control Center hardware section and saw that the nVidia driver box was unchecked. I ticked this box and rebooted the computer, it started in normal user but with a reduced resolution (640x480). I had to edit the /etc/X11/xorg.conf file to get back my resolution of 1024x768 and higher. Restarting x and restarting the computer to make sure everything was ok again.
The advise by other will probably help me with another computer. Thanks guys.

---

