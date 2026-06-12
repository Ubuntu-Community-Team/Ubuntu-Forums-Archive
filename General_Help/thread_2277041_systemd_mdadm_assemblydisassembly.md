---
title: "systemd mdadm assembly/disassembly"
date: 2015-05-06
forum: General Help
---

### Post by xWEkxhW on 2015-05-06
I'm running Ubuntu 15.04 and still having trouble writing systemd units to assemble/disassemble my imsm raid5 array.

I need systemd to assemble the array (mdadm --assemble --scan) during boot at the right time so the filesystem can be mounted before networking is up, but after udev is up (presumably, as mdadm.conf refers to block UUIDs).
systemd needs to also disassemble the array (mdadm --stop --scan) during shutdown after the filesystem has been unmounted.

This is what I have so far, any thoughts?

[FONT=lucida console][Unit][/FONT]
[FONT=lucida console]Description=Assemble/disassemble MD arrays[/FONT]
[FONT=lucida console]DefaultDependencies=no[/FONT]
[FONT=lucida console]
[/FONT]
[FONT=lucida console]Requires=local-fs.target[/FONT]
[FONT=lucida console]After=local-fs.target[/FONT]
[FONT=lucida console]Before=network.target[/FONT]
[FONT=lucida console]
[/FONT]
[FONT=lucida console][Service][/FONT]
[FONT=lucida console]Type=oneshot[/FONT]
[FONT=lucida console]RemainAfterExit=yes[/FONT]
[FONT=lucida console]ExecStart=/sbin/mdadm --assemble --scan[/FONT]
[FONT=lucida console]ExecStop=/sbin/mdadm --stop --scan[/FONT]
[FONT=lucida console]
[/FONT]
[FONT=lucida console][Install][/FONT]
[FONT=lucida console]WantedBy=multi-user.target[/FONT]


I'm really struggling to figure out how to get this right. Is anyone able to assist?

Thanks very much

---

### Post by dino99 on 2015-05-06
you might post on askubuntu to get devs comments

---

