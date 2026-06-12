---
title: "Auto unmount drives when invoking hibernate"
date: 2016-12-11
forum: General Help
---

### Post by numessanguis on 2016-12-11
I have the following dual-boot setup:
- SSD with Windows 7 64-bit (NTFS)
- SSD with Ubuntu 16.04 (Ext4)
- HDD for data (NTFS)

Since I corrupted data with hibernating, because I forgot to unmount my HDD drive:
[https://ubuntuforums.org/showthread.php?t=2346064](https://ubuntuforums.org/showthread.php?t=2346064)
I want to modify my hibernate configuration so that it will automatically **unmount all NTFS devices on Hibernate**.

I turned on hibernation with this guide: [https://ubuntuforums.org/showthread.php?t=2334278](https://ubuntuforums.org/showthread.php?t=2334278)
However I do not know how to setup auto unmount.

Googling it will give me this:
[http://manpages.ubuntu.com/manpages/precise/man5/hibernate.conf.5.html](http://manpages.ubuntu.com/manpages/precise/man5/hibernate.conf.5.html)
But I cannot find a `/etc/hibernate/hibernate.conf` file and it does not say if you have to create it.
Other results were about how the unmounting worked relating to Windows hibernate.

Your help is appreciated.

---

### Post by DuckHook on 2016-12-11
Hibernate is disabled by default in latest 'buntu flavours for many reasons, one of which is exactly the reason that your posting illustrates. Also, the hibernate.conf file has been deprecated at least since the advent of systemd. Moreover, the way systemd handles hibernate will likely continue to change, thus making any workaround or howto temporary and therefore misleading.

The way to execute sleep-driven scripts in systemd is covered in: [http://manpages.ubuntu.com/manpages/wily/man8/systemd-suspend.service.8.html](http://manpages.ubuntu.com/manpages/wily/man8/systemd-suspend.service.8.html)

In particular, note this warning:>  Note that scripts or binaries dropped in /lib/systemd/system-sleep/ are intended for local use only and **should be considered hacks** (emphasis mine).

This in itself should give one pause.

While I would never discourage exploration of the OS or experimentation, many searchers land on threads such as this one thinking that hibernate was turned off for no good reason, and can be turned back on with no consequence. This is a misconception with potentially disastrous results. Aside from issues of data corruption, hibernate flushes the whole security model down the toilet. Coincidentally, this was dealt with it another recent post you can read about [here]("https://ubuntuforums.org/showthread.php?t=2345900&p=13580899#post13580899") if you wish.

For any lurkers reading this: I would never activate hibernate on a production box or one containing important data, not just for reasons of data integrity, but for reasons of data security.

---

