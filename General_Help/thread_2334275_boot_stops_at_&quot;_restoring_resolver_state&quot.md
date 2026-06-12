---
title: "boot stops at &quot;* restoring resolver state&quot;"
date: 2016-08-18
forum: General Help
---

### Post by ski-brimson on 2016-08-18
[FONT=arial][SIZE=3]I use 14.04 UEFI, and dual boot using the BIOS/UEFI selection.

Of course "* restoring resolver state is just the last thing that printed".  Most LSB scripts and upstart daemons print nothing, so this isn't useful.  Even with DEBUG turned on, they still don't print enough to tell what is going on.

This is what I know:

We had a power outage, so I had to boot.  Everything was fine.  Then I went to a meeting, and the password box was flickering, and I unplugged and replugged the keyboard and mouse to no avail, and when I rebooted for the 2nd time that day, the boot stopped at "* restoring resolver state".  I found it just about impossible to get to the grub menu with the shift key (is this a bug?), so the next day I used an ubuntu demo/install DVD and mounted root got into grub and removed the boot menu hiding "feature" so I could boot into text mode reliably, which was just fine.  It went to run level 2.

So I saw someone out there said a possible fix was to remove and reinstall gdm.  So I did that.  Now I can boot normal mode, but the system doesn't go into graphics mode unless I manually start gdm.  I changed [COLOR=#111111]/etc/init/rc-sysinit.conf from run level 2 to run level 5, but even though runlevel now says 5, gdm still doesn't come up.

So ubuntu 14.04 is some kind of amalgamation of LSB scripts and upstart?

I did go into various /etc/rc2.d/S70* through S99*, and verified that all startup scripts in rc2.d complete.

Here is what upstart says about gdm (which never starts):
[/COLOR][/SIZE][/FONT][SIZE=2][FONT=courier new]gdm
  emits login-session-start
  emits desktop-session-start
  emits desktop-shutdown
  start on ((((filesystem and runlevel [!06]) and started dbus) and plymouth-ready) or runlevel PREVLEVEL=S)
[/FONT][/SIZE][FONT=arial][SIZE=2][FONT=courier new]  stop on runlevel [016][/FONT][/SIZE]
[SIZE=3]
[/SIZE][/FONT][COLOR=#111111][FONT=Consolas][FONT=arial][SIZE=3]Here is /var/log/syslog (the rc.local entry was added by me for debug purposes):[/SIZE][/FONT]
[/FONT][/COLOR][SIZE=2][FONT=courier new]
Aug 17 19:01:35 jklugUB14LTS logger: rc.local start
Aug 17 19:01:35 jklugUB14LTS whoopsie[1382]: whoopsie 0.2.24.6ubuntu2 starting up.
Aug 17 19:01:35 jklugUB14LTS whoopsie[1382]: Using lock path: /var/lock/whoopsie/lock
Aug 17 19:01:35 jklugUB14LTS kernel: [   23.601182] init: plymouth-stop pre-start process (1546) terminated with status 1
Aug 17 19:01:35 jklugUB14LTS kernel: [   23.715520] FS-Cache: Netfs 'cifs' registered for caching
Aug 17 19:01:35 jklugUB14LTS kernel: [   23.715576] Key type cifs.spnego registered
Aug 17 19:01:35 jklugUB14LTS kernel: [   23.715590] Key type cifs.idmap registered
Aug 17 19:01:35 jklugUB14LTS NetworkManager[1281]: <info> Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
Aug 17 19:01:35 jklugUB14LTS NetworkManager[1281]: message repeated 3 times: [ <info> Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))]
Aug 17 19:01:35 jklugUB14LTS NetworkManager[1281]: <info> NetworkManager state is now CONNECTED_GLOBAL
Aug 17 19:01:35 jklugUB14LTS NetworkManager[1281]: <info> Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
Aug 17 19:01:35 jklugUB14LTS whoopsie[1548]: offline[/FONT][/SIZE][COLOR=#111111][FONT=Consolas][SIZE=2][FONT=courier new]
[/FONT][/SIZE]
[FONT=arial][SIZE=3]
If I type in start gdm, it fires right up.  Any suggestions?  I look at ps, and I don't seen any rc scripts out their hanging.  dbus is definitely running.  Have no idea what plymouth-ready is.[/SIZE][/FONT]
 [/FONT][/COLOR]

---

