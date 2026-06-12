---
title: "Run Memtest86 test on Asus Zenbook UX363E?"
date: 2022-01-06
forum: General Help
---

### Post by thisismyusername111111111 on 2022-01-06
Hey folks,

My understanding is that for memtest86 to appear in the GRUB menu on boot (or via LiveCD) UEFI needs to be disabled in BIOS (Or something to this effect)- however in the Asus Advanced BIOS options I don't see any way of changing this.

The tl;dr is that my new laptop- a few times every day- will "freeze" and the log in /var/log/syslog will simply be a repeating series of '^@'. I've seen conversation around that this could be faulty hardware, but without being able to run memtest I don't see any way of confirming this. Any advice would be greatly appreciated.

ASUSTeK COMPUTER INC. ZenBook UX363EA_UX363EA
Ubuntu 21.10

Thanks,
Christian

```
Jan  5 11:30:48 anon-lt anacron[6333]: Normal exit (0 jobs run)Jan  5 11:30:48 anon-lt systemd[1]: anacron.service: Deactivated successfully.
Jan  5 11:31:52 anon-lt dbus-daemon[1128]: [system] Activating via systemd: service name='net.reactivated.Fprint' unit='fprintd.service' requested by ':1.89' (uid=1000 pid=1994 comm="/usr/bin/gnome-shell " label="unconfined")
Jan  5 11:31:52 anon-lt systemd[1]: Starting Fingerprint Authentication Daemon...
Jan  5 11:31:52 anon-lt dbus-daemon[1128]: [system] Successfully activated service 'net.reactivated.Fprint'
Jan  5 11:31:52 anon-lt systemd[1]: Started Fingerprint Authentication Daemon.
Jan  5 11:31:55 anon-lt gnome-shell[1994]: Object .GUnionVolumeMonitor (0x55f6891f4300), has been already deallocated — impossible to connect to any signal on it. This might be caused by the object having been destroyed from C code using something such as destroy(), dispose(), or remove() vfuncs.
Jan  5 11:31:55 anon-lt gnome-shell[1994]: == Stack trace for context 0x55f687c72150 ==
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #0   55f68918e938 i   resource:///org/gnome/shell/ui/components/autorunManager.js:154 (385720f7420 @ 54)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #1   55f68918e898 i   resource:///org/gnome/shell/ui/components/__init__.js:49 (385720d76f0 @ 59)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #2   55f68918e808 i   resource:///org/gnome/shell/ui/components/__init__.js:18 (385720d7880 @ 15)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #3   7fffab712990 b   self-hosted:225 (3857202a7e0 @ 273)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #4   55f68918e778 i   resource:///org/gnome/shell/ui/components/__init__.js:18 (385720d7920 @ 67)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #5   7fffab7135f0 b   self-hosted:850 (3857202a650 @ 423)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #6   7fffab7136e0 b   resource:///org/gnome/gjs/modules/core/_signals.js:114 (3fe4adfb1330 @ 439)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #7   7fffab713ed0 b   resource:///org/gnome/shell/ui/sessionMode.js:200 (ada2bbe6d30 @ 284)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #8   55f68918e610 i   resource:///org/gnome/shell/ui/sessionMode.js:168 (ada2bbe6e20 @ 116)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #9   55f68918e578 i   resource:///org/gnome/shell/ui/screenShield.js:574 (ada2bbd4a60 @ 79)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #10   55f68918e4e8 i   resource:///org/gnome/shell/ui/screenShield.js:565 (ada2bbd4ab0 @ 17)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #11   55f68918e450 i   resource:///org/gnome/shell/gdm/authPrompt.js:604 (ada2bbf04c0 @ 65)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #12   55f68918e3b8 i   resource:///org/gnome/shell/ui/unlockDialog.js:871 (385720053d0 @ 40)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #13   55f68918e328 i   resource:///org/gnome/shell/ui/screenShield.js:565 (ada2bbd4b00 @ 50)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #14   55f68918e298 i   resource:///org/gnome/shell/ui/screenShield.js:116 (ada2bbdc6f0 @ 13)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #15   7fffab7149c0 b   resource:///org/gnome/gjs/modules/core/_signals.js:114 (3fe4adfb1330 @ 439)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #16   7fffab714aa0 b   resource:///org/gnome/gjs/modules/core/overrides/Gio.js:152 (3fe4adfa5b50 @ 39)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: == Stack trace for context 0x55f687c72150 ==
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #0   55f68918e938 i   resource:///org/gnome/shell/ui/components/autorunManager.js:155 (385720f7420 @ 111)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #1   55f68918e898 i   resource:///org/gnome/shell/ui/components/__init__.js:49 (385720d76f0 @ 59)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #2   55f68918e808 i   resource:///org/gnome/shell/ui/components/__init__.js:18 (385720d7880 @ 15)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #3   7fffab712990 b   self-hosted:225 (3857202a7e0 @ 273)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: Object .GUnionVolumeMonitor (0x55f6891f4300), has been already deallocated — impossible to connect to any signal on it. This might be caused by the object having been destroyed from C code using something such as destroy(), dispose(), or remove() vfuncs.
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #4   55f68918e778 i   resource:///org/gnome/shell/ui/components/__init__.js:18 (385720d7920 @ 67)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #5   7fffab7135f0 b   self-hosted:850 (3857202a650 @ 423)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #6   7fffab7136e0 b   resource:///org/gnome/gjs/modules/core/_signals.js:114 (3fe4adfb1330 @ 439)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #7   7fffab713ed0 b   resource:///org/gnome/shell/ui/sessionMode.js:200 (ada2bbe6d30 @ 284)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #8   55f68918e610 i   resource:///org/gnome/shell/ui/sessionMode.js:168 (ada2bbe6e20 @ 116)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #9   55f68918e578 i   resource:///org/gnome/shell/ui/screenShield.js:574 (ada2bbd4a60 @ 79)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #10   55f68918e4e8 i   resource:///org/gnome/shell/ui/screenShield.js:565 (ada2bbd4ab0 @ 17)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #11   55f68918e450 i   resource:///org/gnome/shell/gdm/authPrompt.js:604 (ada2bbf04c0 @ 65)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #12   55f68918e3b8 i   resource:///org/gnome/shell/ui/unlockDialog.js:871 (385720053d0 @ 40)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #13   55f68918e328 i   resource:///org/gnome/shell/ui/screenShield.js:565 (ada2bbd4b00 @ 50)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #14   55f68918e298 i   resource:///org/gnome/shell/ui/screenShield.js:116 (ada2bbdc6f0 @ 13)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #15   7fffab7149c0 b   resource:///org/gnome/gjs/modules/core/_signals.js:114 (3fe4adfb1330 @ 439)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #16   7fffab714aa0 b   resource:///org/gnome/gjs/modules/core/overrides/Gio.js:152 (3fe4adfa5b50 @ 39)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: == Stack trace for context 0x55f687c72150 ==
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #0   55f68918e938 i   resource:///org/gnome/shell/ui/components/automountManager.js:34 (385720f7fb0 @ 54)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #1   55f68918e898 i   resource:///org/gnome/shell/ui/components/__init__.js:49 (385720d76f0 @ 59)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #2   55f68918e808 i   resource:///org/gnome/shell/ui/components/__init__.js:18 (385720d7880 @ 15)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #3   7fffab712990 b   self-hosted:225 (3857202a7e0 @ 273)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #4   55f68918e778 i   resource:///org/gnome/shell/ui/components/__init__.js:18 (385720d7920 @ 67)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #5   7fffab7135f0 b   self-hosted:850 (3857202a650 @ 423)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #6   7fffab7136e0 b   resource:///org/gnome/gjs/modules/core/_signals.js:114 (3fe4adfb1330 @ 439)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #7   7fffab713ed0 b   resource:///org/gnome/shell/ui/sessionMode.js:200 (ada2bbe6d30 @ 284)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #8   55f68918e610 i   resource:///org/gnome/shell/ui/sessionMode.js:168 (ada2bbe6e20 @ 116)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: Object .GUnionVolumeMonitor (0x55f6891f4300), has been already deallocated — impossible to connect to any signal on it. This might be caused by the object having been destroyed from C code using something such as destroy(), dispose(), or remove() vfuncs.
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #9   55f68918e578 i   resource:///org/gnome/shell/ui/screenShield.js:574 (ada2bbd4a60 @ 79)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #10   55f68918e4e8 i   resource:///org/gnome/shell/ui/screenShield.js:565 (ada2bbd4ab0 @ 17)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #11   55f68918e450 i   resource:///org/gnome/shell/gdm/authPrompt.js:604 (ada2bbf04c0 @ 65)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #12   55f68918e3b8 i   resource:///org/gnome/shell/ui/unlockDialog.js:871 (385720053d0 @ 40)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #13   55f68918e328 i   resource:///org/gnome/shell/ui/screenShield.js:565 (ada2bbd4b00 @ 50)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #14   55f68918e298 i   resource:///org/gnome/shell/ui/screenShield.js:116 (ada2bbdc6f0 @ 13)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #15   7fffab7149c0 b   resource:///org/gnome/gjs/modules/core/_signals.js:114 (3fe4adfb1330 @ 439)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #16   7fffab714aa0 b   resource:///org/gnome/gjs/modules/core/overrides/Gio.js:152 (3fe4adfa5b50 @ 39)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: == Stack trace for context 0x55f687c72150 ==
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #0   55f68918e938 i   resource:///org/gnome/shell/ui/components/automountManager.js:35 (385720f7fb0 @ 111)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #1   55f68918e898 i   resource:///org/gnome/shell/ui/components/__init__.js:49 (385720d76f0 @ 59)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #2   55f68918e808 i   resource:///org/gnome/shell/ui/components/__init__.js:18 (385720d7880 @ 15)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #3   7fffab712990 b   self-hosted:225 (3857202a7e0 @ 273)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #4   55f68918e778 i   resource:///org/gnome/shell/ui/components/__init__.js:18 (385720d7920 @ 67)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #5   7fffab7135f0 b   self-hosted:850 (3857202a650 @ 423)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #6   7fffab7136e0 b   resource:///org/gnome/gjs/modules/core/_signals.js:114 (3fe4adfb1330 @ 439)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #7   7fffab713ed0 b   resource:///org/gnome/shell/ui/sessionMode.js:200 (ada2bbe6d30 @ 284)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #8   55f68918e610 i   resource:///org/gnome/shell/ui/sessionMode.js:168 (ada2bbe6e20 @ 116)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #9   55f68918e578 i   resource:///org/gnome/shell/ui/screenShield.js:574 (ada2bbd4a60 @ 79)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #10   55f68918e4e8 i   resource:///org/gnome/shell/ui/screenShield.js:565 (ada2bbd4ab0 @ 17)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #11   55f68918e450 i   resource:///org/gnome/shell/gdm/authPrompt.js:604 (ada2bbf04c0 @ 65)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #12   55f68918e3b8 i   resource:///org/gnome/shell/ui/unlockDialog.js:871 (385720053d0 @ 40)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: Object .GUnionVolumeMonitor (0x55f6891f4300), has been already deallocated — impossible to connect to any signal on it. This might be caused by the object having been destroyed from C code using something such as destroy(), dispose(), or remove() vfuncs.
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #13   55f68918e328 i   resource:///org/gnome/shell/ui/screenShield.js:565 (ada2bbd4b00 @ 50)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #14   55f68918e298 i   resource:///org/gnome/shell/ui/screenShield.js:116 (ada2bbdc6f0 @ 13)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #15   7fffab7149c0 b   resource:///org/gnome/gjs/modules/core/_signals.js:114 (3fe4adfb1330 @ 439)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #16   7fffab714aa0 b   resource:///org/gnome/gjs/modules/core/overrides/Gio.js:152 (3fe4adfa5b50 @ 39)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: == Stack trace for context 0x55f687c72150 ==
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #0   55f68918e938 i   resource:///org/gnome/shell/ui/components/automountManager.js:36 (385720f7fb0 @ 168)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #1   55f68918e898 i   resource:///org/gnome/shell/ui/components/__init__.js:49 (385720d76f0 @ 59)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #2   55f68918e808 i   resource:///org/gnome/shell/ui/components/__init__.js:18 (385720d7880 @ 15)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #3   7fffab712990 b   self-hosted:225 (3857202a7e0 @ 273)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #4   55f68918e778 i   resource:///org/gnome/shell/ui/components/__init__.js:18 (385720d7920 @ 67)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #5   7fffab7135f0 b   self-hosted:850 (3857202a650 @ 423)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #6   7fffab7136e0 b   resource:///org/gnome/gjs/modules/core/_signals.js:114 (3fe4adfb1330 @ 439)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #7   7fffab713ed0 b   resource:///org/gnome/shell/ui/sessionMode.js:200 (ada2bbe6d30 @ 284)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #8   55f68918e610 i   resource:///org/gnome/shell/ui/sessionMode.js:168 (ada2bbe6e20 @ 116)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #9   55f68918e578 i   resource:///org/gnome/shell/ui/screenShield.js:574 (ada2bbd4a60 @ 79)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #10   55f68918e4e8 i   resource:///org/gnome/shell/ui/screenShield.js:565 (ada2bbd4ab0 @ 17)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #11   55f68918e450 i   resource:///org/gnome/shell/gdm/authPrompt.js:604 (ada2bbf04c0 @ 65)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #12   55f68918e3b8 i   resource:///org/gnome/shell/ui/unlockDialog.js:871 (385720053d0 @ 40)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #13   55f68918e328 i   resource:///org/gnome/shell/ui/screenShield.js:565 (ada2bbd4b00 @ 50)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #14   55f68918e298 i   resource:///org/gnome/shell/ui/screenShield.js:116 (ada2bbdc6f0 @ 13)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #15   7fffab7149c0 b   resource:///org/gnome/gjs/modules/core/_signals.js:114 (3fe4adfb1330 @ 439)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #16   7fffab714aa0 b   resource:///org/gnome/gjs/modules/core/overrides/Gio.js:152 (3fe4adfa5b50 @ 39)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: == Stack trace for context 0x55f687c72150 ==
Jan  5 11:31:55 anon-lt gnome-shell[1994]: Object .GUnionVolumeMonitor (0x55f6891f4300), has been already deallocated — impossible to connect to any signal on it. This might be caused by the object having been destroyed from C code using something such as destroy(), dispose(), or remove() vfuncs.
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #0   55f68918e938 i   resource:///org/gnome/shell/ui/components/automountManager.js:37 (385720f7fb0 @ 225)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #1   55f68918e898 i   resource:///org/gnome/shell/ui/components/__init__.js:49 (385720d76f0 @ 59)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #2   55f68918e808 i   resource:///org/gnome/shell/ui/components/__init__.js:18 (385720d7880 @ 15)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #3   7fffab712990 b   self-hosted:225 (3857202a7e0 @ 273)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #4   55f68918e778 i   resource:///org/gnome/shell/ui/components/__init__.js:18 (385720d7920 @ 67)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #5   7fffab7135f0 b   self-hosted:850 (3857202a650 @ 423)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #6   7fffab7136e0 b   resource:///org/gnome/gjs/modules/core/_signals.js:114 (3fe4adfb1330 @ 439)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #7   7fffab713ed0 b   resource:///org/gnome/shell/ui/sessionMode.js:200 (ada2bbe6d30 @ 284)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #8   55f68918e610 i   resource:///org/gnome/shell/ui/sessionMode.js:168 (ada2bbe6e20 @ 116)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #9   55f68918e578 i   resource:///org/gnome/shell/ui/screenShield.js:574 (ada2bbd4a60 @ 79)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #10   55f68918e4e8 i   resource:///org/gnome/shell/ui/screenShield.js:565 (ada2bbd4ab0 @ 17)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #11   55f68918e450 i   resource:///org/gnome/shell/gdm/authPrompt.js:604 (ada2bbf04c0 @ 65)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #12   55f68918e3b8 i   resource:///org/gnome/shell/ui/unlockDialog.js:871 (385720053d0 @ 40)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #13   55f68918e328 i   resource:///org/gnome/shell/ui/screenShield.js:565 (ada2bbd4b00 @ 50)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #14   55f68918e298 i   resource:///org/gnome/shell/ui/screenShield.js:116 (ada2bbdc6f0 @ 13)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #15   7fffab7149c0 b   resource:///org/gnome/gjs/modules/core/_signals.js:114 (3fe4adfb1330 @ 439)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #16   7fffab714aa0 b   resource:///org/gnome/gjs/modules/core/overrides/Gio.js:152 (3fe4adfa5b50 @ 39)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: == Stack trace for context 0x55f687c72150 ==
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #0   55f68918e938 i   resource:///org/gnome/shell/ui/components/automountManager.js:38 (385720f7fb0 @ 282)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #1   55f68918e898 i   resource:///org/gnome/shell/ui/components/__init__.js:49 (385720d76f0 @ 59)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #2   55f68918e808 i   resource:///org/gnome/shell/ui/components/__init__.js:18 (385720d7880 @ 15)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #3   7fffab712990 b   self-hosted:225 (3857202a7e0 @ 273)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: Object .GUnionVolumeMonitor (0x55f6891f4300), has been already deallocated — impossible to connect to any signal on it. This might be caused by the object having been destroyed from C code using something such as destroy(), dispose(), or remove() vfuncs.
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #4   55f68918e778 i   resource:///org/gnome/shell/ui/components/__init__.js:18 (385720d7920 @ 67)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #5   7fffab7135f0 b   self-hosted:850 (3857202a650 @ 423)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #6   7fffab7136e0 b   resource:///org/gnome/gjs/modules/core/_signals.js:114 (3fe4adfb1330 @ 439)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #7   7fffab713ed0 b   resource:///org/gnome/shell/ui/sessionMode.js:200 (ada2bbe6d30 @ 284)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #8   55f68918e610 i   resource:///org/gnome/shell/ui/sessionMode.js:168 (ada2bbe6e20 @ 116)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #9   55f68918e578 i   resource:///org/gnome/shell/ui/screenShield.js:574 (ada2bbd4a60 @ 79)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #10   55f68918e4e8 i   resource:///org/gnome/shell/ui/screenShield.js:565 (ada2bbd4ab0 @ 17)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #11   55f68918e450 i   resource:///org/gnome/shell/gdm/authPrompt.js:604 (ada2bbf04c0 @ 65)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #12   55f68918e3b8 i   resource:///org/gnome/shell/ui/unlockDialog.js:871 (385720053d0 @ 40)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #13   55f68918e328 i   resource:///org/gnome/shell/ui/screenShield.js:565 (ada2bbd4b00 @ 50)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #14   55f68918e298 i   resource:///org/gnome/shell/ui/screenShield.js:116 (ada2bbdc6f0 @ 13)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #15   7fffab7149c0 b   resource:///org/gnome/gjs/modules/core/_signals.js:114 (3fe4adfb1330 @ 439)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: #16   7fffab714aa0 b   resource:///org/gnome/gjs/modules/core/overrides/Gio.js:152 (3fe4adfa5b50 @ 39)
Jan  5 11:31:55 anon-lt gnome-shell[1994]: Object .GUnionVolumeMonitor (0x55f6891f4300), has been already deallocated — impossible to connect to any signal on it. This might be caused by the object having been destroyed from C code using something such as destroy(), dispose(), or remove() vfuncs.
Jan  5 11:31:55 anon-lt gnome-shell[1994]: cr_parser_new_from_buf: assertion 'a_buf && a_len' failed
Jan  5 11:31:55 anon-lt gnome-shell[1994]: cr_declaration_parse_list_from_buf: assertion 'parser' failed
Jan  5 11:31:55 anon-lt dbus-daemon[1856]: [session uid=1000 pid=1856] Activating service name='org.freedesktop.FileManager1' requested by ':1.34' (uid=1000 pid=1994 comm="/usr/bin/gnome-shell " label="unconfined")
Jan  5 11:32:20 anon-lt nautilus[6384]: The peer-to-peer connection failed: Timeout was reached. Falling back to the session bus. Your application is probably missing --filesystem=xdg-run/gvfsd privileges.
Jan  5 11:32:22 anon-lt systemd[1]: fprintd.service: Deactivated successfully.
^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@Jan  5 11:33:40 anon-lt kernel: [    0.000000] microcode: microcode updated early to revision 0x88, date = 2021-03-31
Jan  5 11:33:40 anon-lt kernel: [    0.000000] Linux version 5.13.0-23-generic (buildd@lcy01-amd64-022) (gcc (Ubuntu 11.2.0-7ubuntu2) 11.2.0, GNU ld (GNU Binutils for Ubuntu) 2.37) #23-Ubuntu SMP Fri Nov 26 11:41:15 UTC 2021 (Ubuntu 5.13.0-23.23-generic 5.13.19)
Jan  5 11:33:40 anon-lt kernel: [    0.000000] Command line: BOOT_IMAGE=/vmlinuz-5.13.0-23-generic root=/dev/mapper/vgubuntu-root ro quiet splash vt.handoff=7
Jan  5 11:33:40 anon-lt kernel: [    0.000000] KERNEL supported cpus:



```

---

### Post by slooksterpsv on 2022-01-07
I would check and see what BIOS version you're running as Intel has had to fix some flaws for the 11th generation chips via BIOS patches. If you can, try to update the BIOS if you're comfortable doing so. **NOTE:** Improperly/incorrectly updating the BIOS (i.e. power outage causes system to shutdown) can result in bricking the machine.

You can also run a memory test inside of the OS, there are utilities out there.

Another item I would do is see if there are any additional drivers (restricted drivers). It looks like the message you output is talking about the Audio system - which depending on what is running, could cause an issue. It may be useful to switch to Pulse audio and see if that makes a difference. (In the past it was the inverse, don't use Pulse audio and go back to ___, but I digress).

Try those and see if that helps.

---

### Post by thisismyusername111111111 on 2022-01-18
Thank you so much, I'll give those a go!

---

### Post by thisismyusername111111111 on 2022-01-20
Just a follow-up. I don't want to speak too soon because it's only been 24 hours, but so far a BIOS update seems to have done the trick. 

Went from Version: UX363EA.311 (I think) to Version: UX363EA.318.

---

