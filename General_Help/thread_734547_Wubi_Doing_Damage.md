---
title: "Wubi Doing Damage?"
date: 2008-03-24
forum: General Help
---

### Post by blah569 on 2008-03-24
I have used Ubuntu before, but I have never installed it.  I actually want to install it, but I have been doing some reading that Wubi can damage the system to where it will not boot into Windows or Ubuntu.  I have a "restore CD," encase such would happen, but I wonder if the CD would even boot up in an event like that.  Anyway, the reading said that doing a "hard-power off" was damaging the systems, as in unplugging or just simply using the power button instead of booting down normally.

I don't wish for any catastrophe to happen, so can anyone tell me what to steer away from, or what could possible damage me.  Thanks.

---

### Post by ago on 2008-03-24
All reported cases of damaged filesystems so far were from people that hard rebooted.

When you hard reboot, you can always damage your filesystem whether you use wubi or not. What happens is that new users sometimes get stacked with wubi/ubuntu and since they do not know what to do they tend to hard-reboot more often than necessary... Sometimes they get lucky, sometimes they do not. Since wubi sits on top of ntfs of course when they do not get lucky, ntfs gets corrupted and people tend to blame Wubi. A quick googling will show you that there are tons of people experiencing ntfs corruption without having used wubi or ntfs-3g (and a full software industry lurking on that...), most of them after a hard reboot.... We have close to a million users and have received a few dozens of such reports. 

The real problem is that at the moment there is no fsck for ntfs on the Linux side. So if ntfs filesystem gets corrupted you have to run chkdsk /r from the windows recovery console (otherwise it would be possible to fix errors automatically within Linux itself, as it happens for other filesystems). 

There are normally several ways to reboot cleanly a Linux installation using key combinations such as ALT+ SYSRQ + RSUB but many ignore them.

In most cases, ntfs corruption can be recovered running chkdsk /r. But best advise is to simply avoid hard rebooting. Whatever the OS.

---

### Post by blah569 on 2008-03-24
> **ago said:**
> All reported cases of damaged filesystems so far were from people that hard rebooted.

When you hard reboot, you can always damage your filesystem whether you use wubi or not. What happens is that new users sometimes get stacked with wubi/ubuntu and since they do not know what to do they tend to hard-reboot more often than necessary... Sometimes they get lucky, sometimes they do not. Since wubi sits on top of ntfs of course when they do not get lucky, ntfs gets corrupted and people tend to blame Wubi. A quick googling will show you that there are tons of people experiencing ntfs corruption without having used wubi or ntfs-3g (and a full software industry lurking on that...), most of them after a hard reboot.... We have close to a million users and have received a few dozens of such reports. 

The real problem is that at the moment there is no fsck for ntfs on the Linux side. So if ntfs filesystem gets corrupted you have to run chkdsk /r from the windows recovery console (otherwise it would be possible to fix errors automatically within Linux itself, as it happens for other filesystems). 

There are normally several ways to reboot cleanly a Linux installation using key combinations such as ALT+ SYSRQ + RSUB but many ignore them.

In most cases, ntfs corruption can be recovered running chkdsk /r. But best advise is to simply avoid hard rebooting. Whatever the OS.

Thank you for the reply.  Do you believe that the restore CD would still boot properly if such damage would occur, though?

---

### Post by ago on 2008-03-25
You can always boot from a restore CD. In most cases chkdsk /r will fix everything, there are a few instances where fs corruption is unrecoverable.

---

### Post by Arleas on 2011-01-30
> **ago said:**
> You can always boot from a restore CD. In most cases chkdsk /r will fix everything, there are a few instances where fs corruption is unrecoverable.

You should run chkdsk /f /r otherwise it won't repair the damage. 

[Chkdsk corrects disk errors only if you specify the /f command-line option.]("http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true")

---

### Post by s.fox on 2011-01-31
[IMG]http://s3.postimage.org/wwatx561a/Thread_Necromancer.jpg[/IMG]

---

