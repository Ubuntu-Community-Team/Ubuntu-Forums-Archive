---
title: "Disabling de-installation of previous kernels  in automatic kernel upgrades"
date: 2015-03-12
forum: General Help
---

### Post by ofnuts on 2015-03-12
Since I upgraded to 14.04 it seems that kernel upgrade N de-installs kernels N-2 and before. One one hand this is nice since this removes the need to clean up /boot periodically by de-installing old kernels. By I'm wondering what will happen if a kernel comes that doesn't work well for me. I can back out to the previous version, but the next version could be just as unusable(*) and will wipe out the only good kernel version I have.

So is there a way to disable this if needed, typically, by keeping a specific kernel version available?

(*) On 10.04, 5 or 6 kernel versions in a row made my system rather crash-prone and a trusted kernel version turned out to be rather handy.

---

### Post by SeijiSensei on 2015-03-12
I actually complained to the maintainers about the old practice.  Not deleting stale kernels could make a machine unbootable if /boot were assigned to a separate partition.  Usually /boot partitions are fairly small so it was easy to run out of space if stale kernels weren't deleted.

I suppose you could consider writing a script to back up /boot in case you encounter the problem you describe.  Something like 
```
cd /; rsync -av boot /usr/local
```
would copy all of /boot to /usr/local/boot for safe keeping.  You could put these commands in /etc/rc.local so they would be run at every boot.  If there are no new kernels to back up, the command should terminate quickly.  As long as you don't use the --delete switch to rsync, /usr/local/boot will contain a complete inventory of all prior kernels and associated files.

---

### Post by ofnuts on 2015-03-13
Having a backup of the kernel doesn't mean that the system can boot it. So if there is no way to disable this I would have to:

1) keep a backup of the trusted kernel files
2) notice installation of new kernel
3) reinstate the old kernels from the backup
4) run the grub config again

Can of course be done (everything is doable on Linux...) but if I can avoid it...

---

### Post by SeijiSensei on 2015-03-14
I must run pretty vanilla machines because I haven't encountered a problem with a kernel update in quite a long time now, probably years.  I only use LTS releases these days, though.

---

### Post by ofnuts on 2015-03-14
> **SeijiSensei said:**
> I must run pretty vanilla machines because I haven't encountered a problem with a kernel update in quite a long time now, probably years.  I only use LTS releases these days, though.

So have I, but better safe than  sorry :)

---

### Post by ian-weisser on 2015-03-15
Kernel autoremove is set by the script at /etc/kernel/postinst.d/apt-auto-removal

The script author, Steve Langasek, gave thought to how many kernels to save, and which kernels to select. See the comments in the script.
Naturally, patches to improve the script are welcome.

It doesn't look difficult to hardcode a kernel version you really want to keep.

---

### Post by ofnuts on 2015-03-15
Great. Yes, not difficult to hack if I want to keep a specific version. Thanks for the pointer.

---

