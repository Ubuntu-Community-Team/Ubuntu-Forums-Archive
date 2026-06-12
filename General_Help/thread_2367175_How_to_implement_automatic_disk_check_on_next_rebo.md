---
title: "How to implement automatic disk check on next reboot on dirty shutdown"
date: 2017-07-26
forum: General Help
---

### Post by Marcelo Ruiz on 2017-07-26
Hi community,

I want to make Ubuntu 16.04 check the file system on the next reboot if the previous shutdown was not clean (sudden power off for example). I do **not** want it to check the file system on *every* boot. On top of that, I would like the user to be able to schedule a file system check on the next reboot if desired, using the famous "*sudo touch /forcefsck*"

I was thinking of creating three scripts with their respective services files:

- The first service creates a '/autofsck' file on the root system on every boot, right after the service that check for the existence of '/forcefsck' runs.
- The second one deletes the '/autofsck' right before the shutdown, so if there is an abrupt shutdown the marker file remains on the file system.
- The third one is the one I am having problems with. I wanted it to check the existence of  '/autofsck' and rename it to  '/forcefsck', right before the service that triggers the file system check gets executed.

My problem is that I don't know which the script that triggers the file system check if '/forcefsck' is. Does anyone know which service does that?
Ideally I would like this solution to work with upcoming LTS versions of Ubuntu.
If you think I should tackle the problem in a different way, please let me know. I am open to suggestions.

Thanks!

[Edit]
I forgot to mention that I know that */etc/init/mountall.conf* and */etc/init.d/checkroot.sh* are involved in the file system check process, and I could edit those files to make them check for the existence of '/autofsck', but I wanted to avoid editing those files or any files that could potentially be updated by the system.

---

### Post by igdfpm on 2017-07-27
/forcefsck no longer works as it was a SysV thing (and early upstart) - ubuntu is Systemd these days.

If you add ```
fsck.mode=auto
``` to your kernel line the system will fsck as and when required - no other scripting required.

---

### Post by TheFu on 2017-07-27
My understanding of all this is a little different from yours.

Periodic checks are part of the file system metadata.  Use tune2fs (or whatever the specific file system uses) to control it. A default is set during file system creation, but it is tunable. Every 60 mounts is the default, methinks.  Let me check a 16.04 box ... well ... seems it is disabled completely.
```
$ sudo tune2fs -l  /dev/mapper/vg-root
...
Mount count:              24
Maximum mount count:      -1
Last checked:             Sun Jun  4 07:46:44 2017
Check interval:           0 (<none>)
...
```
It is running whole drive encryption with LVM, so perhaps it isn't the normal settings?

Checked a 14.04 system.  
```
Filesystem created:       Wed Sep 25 10:08:16 2013

Mount count:              44
Maximum mount count:      -1
Last checked:             Sat Oct 17 11:59:06 2015
Check interval:           0 (<none>)

```
Scary.  Just forced a check at next reboot.

If a file system isn't cleanly closed, at the next mount, it will get checked automatically. At least that is the way it should work.  That is the way it has worked here for decades.

/forcefsck only works for the root file system. Others need a manual solution.

So, looking at my data, seems I need to change the Max mount count to something like 5 if I want checks every few months of reboots. That shouldn't be too hard for Ansible.

---

### Post by Marcelo Ruiz on 2017-07-27
@igdfpm
Thanks for the suggestion. I will try it, but I thought that was the default behavior... So why is the parameter needed? Kind of confused over here #-o
I will report back if there is another sudden power failure!

@TheFu's
The check interval for my disks is also zero. I also expected the disk check to be done automatically when the system doesn't shutdown properly, but sometimes the filesystem state does not show as 'clean', nor it is corrected during next boot...

---

### Post by TheFu on 2017-07-27
On my 16.04 box, the /forcefsck didn't work.  Probably a "systemd improvement" .... that actually is NOT an improvement.  Had a system lockup (intel video problem, well understood), and I'd touched the /forcefsck file TODAY.

```
Mount count:              25
Maximum mount count:      -1
Last checked:             Sun Jun  4 07:46:44 2017
Check interval:           0 (<none>)
```
Booted about 5 min ago and it wasn't checked.

[https://www.cyberciti.biz/faq/linux-force-fsck-on-the-next-reboot-or-boot-sequence/](https://www.cyberciti.biz/faq/linux-force-fsck-on-the-next-reboot-or-boot-sequence/) says that systemd has a different method.  Booooo.  If I'm reading the link correctly, what a pain.

---

### Post by Bashing-om on 2017-07-27
fsck on systemd:

[https://wiki.archlinux.org/index.php/fsck](https://wiki.archlinux.org/index.php/fsck)
[https://www.freedesktop.org/software/systemd/man/systemd-fsck@.service.html](https://www.freedesktop.org/software/systemd/man/systemd-fsck@.service.html)

- The times - they are achange'n -

---

