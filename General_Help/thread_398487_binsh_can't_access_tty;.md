---
title: "/bin/sh: can't access tty;"
date: 2007-04-01
forum: General Help
---

### Post by NBX on 2007-04-01
Hi,
When i just restarted my Linux Ubuntu, on booting it show`d this error:
> BusyBox v1.1.3 (Debian 1:1.1.3-2ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs)
When i used CTRL + ALT + F1 it show`d
> Target filesystem doesn`t have sbin/init

I am an amateur at Linux, so please tell me _commands_ to get any infos, fix this problem!

Thanks,
Nils Putni&#326;š

---

### Post by acormack on 2007-04-01
Why did you reboot?  

Was there an error before you shutdown?

Is there a CD in the drive?

Does the normal boot process seem to be working or does this error come up immediately?

---

### Post by NBX on 2007-04-01
> **acormack said:**
> Why did you reboot?  

Was there an error before you shutdown?

Is there a CD in the drive?

Does the normal boot process seem to be working or does this error come up immediately?

I rebooted cause i tried to install two upgrades, but it show`d that apt-get is in use and i couldn`t do that, so i restarted it. It didn`t shutdown completely (i connect throught VNC) - after 5 minutes it didn`t shut down, so i pressend and holded the shutdown button.

There isn`t any CD in the drive.

The error comes up when ubuntu starts loading (the line) - after about 10 seconds.

---

### Post by NBX on 2007-04-01
So..? Please help as fast as You can :(
Thanks!

---

### Post by acormack on 2007-04-01
I think when you powered off the running system it corrupted the hard disk hence why it can't find init in /sbin.

I would try booting from the live CD and seeing what data is left on the hard disk.

If your /home directory is still OK you should probably back it up to DVD/CD then try to reinstall.

Sorry I can't be of more help.

---

### Post by kizmat on 2007-04-12
I had the same problem "file system doesn't have /sbin/init" after upgrading from edgy to feisty beta with the alternate cd.

Upgrade was successful but it couldn't boot. I went into rescue mode and did a "ls /target"
and there was a lot of io error. I did this twice and it was the same problem.

I checked my /target/sbin/ and there wasn't any init file. What's wrong? Now I couldn't boot into feisty anymore.

I suspect it has something to do with the hda converted to sda because during a normal install in text mode, my hda was converted to sda and it couldn't detect the partitions correctly (i have a windows partition in it as well).

If it matters, i'm running thinkpad T41. Hope someone can help, thanks.

---

### Post by Aero9000 on 2007-04-12
Hi there,

Try replacing the MBR. I have written a detailed post here: [http://ubuntuforums.org/showthread.php?t=405691&highlight=can%27t+access+tty+solution](http://ubuntuforums.org/showthread.php?t=405691&highlight=can%27t+access+tty+solution)

---

### Post by kizmat on 2007-04-12
Hi thanks for the reply.
I've managed to solve my problem here
[https://launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/82314](https://launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/82314)

It was a bug in the kernel not being able to detect my T41 hdd properly. Loading the new kernel works, hope it gets into the RC in time :)

---

