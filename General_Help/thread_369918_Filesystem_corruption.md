---
title: "Filesystem corruption?"
date: 2007-02-25
forum: General Help
---

### Post by robi_sabocanec on 2007-02-25
Hello all,
I have a problem, I hope someone here can help me.
I can't boot my system (Ubuntu Edgy) from hard disk. I can boot live CD and then when i mount hard drive everything seems fine except one thing; etc directory on mounted hard drive is marked as a file not as a directory and I can actually list the content of this 'etc' file. 
I have noticed this when I tryed to enable boot log messages. 

Thanks in advance all those who try to help
Bob

---

### Post by cronholio on 2007-02-25
What exactly happens when you try to boot from hard disk? Can you boot into recovery mode (choose it in GRUB)?

---

### Post by robi_sabocanec on 2007-02-25
Here it is what happens in recovery mode:
<dump>
...
Kjournal starting - Commit interval 5 seconds
EXT3-fs: mounted filesystem with ordered data mode
Begin: Running /scripts/local-bottom
Done
Done
Begin: Running /scripts/init-bottom
USB 1-2: configuration #1
Chosen from 1 choice
Done
</dump>

After that it hangs, it doesn't accept Ctrl+Alt+Del to restart.
In normal boot mode, it hangs on approximately 5% in progress bar of boot splash screen

Just to mention, last week I had few (two or three) error messages from filesystem, but after restarting everything worked fine.
I was afraid that my hard disk died, but then, I can mount it from live CD so maybe it is just problem with the filesystem,

---

### Post by cronholio on 2007-02-25
Seems like some USB device creates a problem. Unplug all USB devices and try to boot. It would also help to know the output of "lsusb" (while all devices are connected).

---

### Post by robi_sabocanec on 2007-02-25
Tryed to unplug USB devices, it doesn't help :( 
I'm quite convinced it is filesystem issue. Why is 'etc' shown as file, not as directory, when hard disk is mounted from outside system?

Thanks for the try cronholio

---

### Post by cronholio on 2007-02-25
You should do a check of your file system. Boot the Live CD and run ```
sudo fsck /dev/hda1
```

If your root partition is not hda1, you need to change that.

---

### Post by robi_sabocanec on 2007-02-25
That was the first thing I've tried, it doesn't help. 
I'm afraid I'll have to backup my personal data, and then reinstall ubuntu, although, if it is hard disk hardware failure, I'll have to get new one.
Thanks again for your help

---

