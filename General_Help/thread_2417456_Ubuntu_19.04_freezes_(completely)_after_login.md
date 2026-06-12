---
title: "Ubuntu 19.04 freezes (completely) after login"
date: 2019-04-23
forum: General Help
---

### Post by vegardsv on 2019-04-23
Hi,

I recently upgraded from 18.10 to 19.04.

Before the upgrade the machine was running fine.

After the upgrade, it completely locks up (freezes) about 20-30 seconds after I've logged in. Mouse pointer freezes and switching to a TTY (ctrl-alt-f3 etc.) does not work. I can not log in via ssh from another machine. The hard drive led blinks about a couple times per second or so.

SysRQ REISUB works, but there is no way to get to the text console.

However... Logging in with a new user works - no hangs! So there's apparently something in my current profile causing this.

I'd like to figure out what it is.

Various notes:

[LIST]
[*] It's an Intel 8700K overclocked to 4.8 GHz. I tried restoring the defaults - no difference.
[*] I've tried the recent (ppa-mainline) kernels (5.0.9 and 5.1rc6)
[*] I've tried with and without the NVIDIA drivers (I have a 1070Ti)
[*] There's nothing to go on in the logs and the systemd journal. The only lines I've found of interest in Xorg.log are the likes of: "systemd-logind: got pause for 13:65"
[*] I've tried unplugging all devices I don't use
[*] Wayland is disabled (always has been)
[*] The same happens irrespective of desktop environment (I've tried both KDE and Gnome).
[*] I've had occasional complete crashes in previous Ubuntu versions as well, but those crashes have always happened whilst flying in X-Plane, so I assumed those to be GPU-related (and they've seemed to vanish - haven't had a crash in a long time)
[/LIST]

One peculiar thing: I've tried opening (logging in to) a TTY before logging into the GUI. If I log in to the GUI, then switch to the TTY before the freeze occurs, the TTY will also hang once the GUI login process has completed. However: After a seemingly random time period (usually minutes), the system will respond very briefly (half a second), then lock up again. Also, SysRQ output is displayed on the terminal even though the computer is otherwise unresponsive.

I'm thinking along the lines of this being some sort of strange race condition, but I'm at my wits end now.

Any ideas?

---

### Post by similar2 on 2019-04-26
Hi,

Without access to a TTY, the only alternative is to use **chroot** from a Live CD to access the crippled system. Looks like a broken upgrade to me (conflicting/missing packages from PPA?).
Also, it could be an issue with gdm3: Try setting up sddm (KDE Plasma login manager if I remember correctly) as default.

[https://help.ubuntu.com/community/LiveCdRecovery](https://help.ubuntu.com/community/LiveCdRecovery)

---

### Post by vegardsv on 2019-05-02
For anyone facing the same problem, it seems to stem from a bug in the tracker-extract process. I've filed bugs here, which can be followed:

[https://bugs.launchpad.net/ubuntu/+source/tracker-miners/+bug/1826439?comments=all](https://bugs.launchpad.net/ubuntu/+source/tracker-miners/+bug/1826439?comments=all)

[https://gitlab.gnome.org/GNOME/tracker/issues/95](https://gitlab.gnome.org/GNOME/tracker/issues/95)

---

### Post by similar2 on 2019-05-03
Have you tried disabling the tracker services from a chrooted environment (Live CD)?

Hint:
[https://www.soimort.org/notes/171103/](https://www.soimort.org/notes/171103/)

---

