---
title: "Random freezing/shutdowns"
date: 2020-01-06
forum: General Help
---

### Post by stonysmith on 2020-01-06
Experienced user here.
I've got 18.04 with latest patches running on a Dell 3050 micro-machine...  Intel Celeron CPU  J1800  @ 2.41GHz with 4gb of ram.
It has a monitor attached, but most of the time I'm just using ssh to access the machine.
I'm not running a lot of tasks, most of the usage of this machine is with three rsync commands daily to keep my various backup drives fresh.

Every two or three days, the machine locks up. It stops responding to mouse/keyboard, and stops responding to SSH
The scheduled cron tasks also cease.

The only thing that will bring it back is power cycling the device.

I've looked thru the logs but nothing jumps out at me, other than stuff like this:
Jan  5 18:31:38 id84 kernel: [97928.158752] [drm:vlv_set_power_well [i915]] *ERROR* timeout setting power well state 0000c000 (00fffcc0)
Jan  5 18:31:38 id84 kernel: [97928.267961] [drm:vlv_set_power_well [i915]] *ERROR* timeout setting power well state 00003000 (00fffcc0)
Jan  5 18:31:38 id84 kernel: [97928.375748] [drm:vlv_set_power_well [i915]] *ERROR* timeout setting power well state 000000c0 (00fffcc0)
Jan  5 18:31:38 id84 kernel: [97928.566256] [drm:vlv_set_power_well [i915]] *ERROR* timeout setting power well state 000000c0 (00fffcc0)
<end of log>

Any suggestions?  Is this simply a hardware failure?

---

### Post by ponef on 2020-01-29
> **stonysmith said:**
> Experienced user here.
I've got 18.04 with latest patches running on a Dell 3050 micro-machine...  Intel Celeron CPU  J1800  @ 2.41GHz with 4gb of ram.
It has a monitor attached, but most of the time I'm just using ssh to access the machine.
I'm not running a lot of tasks, most of the usage of this machine is with three rsync commands daily to keep my various backup drives fresh.

Every two or three days, the machine locks up. It stops responding to mouse/keyboard, and stops responding to SSH
The scheduled cron tasks also cease.

The only thing that will bring it back is power cycling the device.

I've looked thru the logs but nothing jumps out at me, other than stuff like this:
Jan  5 18:31:38 id84 kernel: [97928.158752] [drm:vlv_set_power_well [i915]] *ERROR* timeout setting power well state 0000c000 (00fffcc0)
Jan  5 18:31:38 id84 kernel: [97928.267961] [drm:vlv_set_power_well [i915]] *ERROR* timeout setting power well state 00003000 (00fffcc0)
Jan  5 18:31:38 id84 kernel: [97928.375748] [drm:vlv_set_power_well [i915]] *ERROR* timeout setting power well state 000000c0 (00fffcc0)
Jan  5 18:31:38 id84 kernel: [97928.566256] [drm:vlv_set_power_well [i915]] *ERROR* timeout setting power well state 000000c0 (00fffcc0)
<end of log>

Any suggestions?  Is this simply a hardware failure?

Hi buddy, which load you are on to, and any possible solution?

Regards,
Noel Smith [[COLOR=#000000]Plex[/COLOR]](https://plex.software/) [[COLOR=#000000]Tutuapp[/COLOR]](https://tutuappx.com/) [[COLOR=#000000]Vidmate[/COLOR]](https://vidmate.onl/)

---

