---
title: "Installation failed..."
date: 2006-11-29
forum: General Help
---

### Post by Infiltraitor on 2006-11-29
*If this thread doesn't belong here... feel free to move it.*

Firstly, I chose that 'create partition using the largest continuous free space' option while installing.

The initial setup went well, and the progress bar comes up showing the progress of the installation. When it was near 70% done, I walked away to do something and when I came back, I got punched in the face with a 'installation failed' error or something similar. It showed me a whole bunch of code stuff, and I just exited out.

I went to the partition manager in the live session and saw a 'linux-swap' for I think around 250MB. It had blank spaces in the 'used' and 'unused' columns. The boot flag was on that linux partition. I wanted to experiment, so I reboot the computer and a 'operating system not found' error occurred.

I remembered that the 'boot' flag was on that corrupted 'linux-swap' partition and I rebooted with the live session CD. I changed the 'boot' flag to my C: drive with my Windows OS and deleted the corrupted 'linux-swap' partition.

Everything is still perfect back in Win XP, so that's good..

So if you listened to my story... what went wrong? Should I just try again and experiment a bit more? I'll give you any info to make things easier...

Cheers,

---

### Post by Joe_CoT on 2006-11-29
... Sometimes things break :D If you can reproduce the error, and provide it to us, I'm sure we'd be able to figure out what went wrong, and/or forward it to the dev team. If you're willing to, please do so.

That said, you can probably rectify the situation by choosing "manually edit partition table" in the installer. Delete the old swap partition, make a partition for swap, a partition for the root partition, and a partition for anything else you want to be on a separate partition (ex: /home, or /etc, etc). Just don't select and delete/format your windows partition, and you should be fine.

---

### Post by louieb on 2006-11-29
Wow that a new one. Glad you got XP back up.   Might want to check the [COLOR="Red"]md5sum[/COLOR] of you install CD. Open Office has a good page on [how to do it]("http://www.openoffice.org/dev_docs/using_md5sums.html"). And the install CD has an option to check itself. 
Assuming you have backed up anything it would kill you to loose and you have a Windows install disk. I would go ahead and check the Ubuntu CD then try it again.
Are you trying to install on a second hard drive? If so you might want to unplug your windows drive before you try again just to be safe.

---

