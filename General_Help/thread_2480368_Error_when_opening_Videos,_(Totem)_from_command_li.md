---
title: "Error when opening Videos, (Totem) from command line"
date: 2022-10-27
forum: General Help
---

### Post by adrian-h on 2022-10-27
I run a simple script when receiving a stream from a hardware device, In ubuntu 20.04 on a different machine this would work fine.

Now on a small machine running 22.04 I get several errors :-
```

mesa: for the --simplifycfg-sink-common option: may only occur zero or one times!
mesa: for the --global-isel-abort option: may only occur zero or one times!
mesa: for the --amdgpu-atomic-optimizations option: may only occur zero or one times!
```

If from command line I enter totem I get errors

```
adrian@t630:~$ totem

(totem:4003): GLib-GObject-CRITICAL **: 15:52:00.111: g_param_values_cmp: assertion 'G_IS_VALUE (value1)' failed

(totem:4003): GLib-GObject-CRITICAL **: 15:52:00.111: g_param_values_cmp: assertion 'G_IS_VALUE (value1)' failed
```

Can anyone assist in figuring out what is going wrong.

The pc is a HP Thin client type T630
128 gig SSD
8 Gig Ram
AMD GX-420GI SOC: quad-core APU 2.0-2.2GHz
Radeon R7E graphics

If anything else would be of help to fault find please let me know what I have to do?

Adrian

---

### Post by Xian on 2022-10-27
It's a known bug: 

[https://bugs.launchpad.net/ubuntu/+source/totem/+bug/1966787](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/1966787)

---

### Post by adrian-h on 2022-10-28
OK thanks, for that I am never sure on how to find these, I will await updates, up to now it will play giving the errors, if the stream disappears for any time and restarts then totem will crash and a crash report is sent off.

In the command line script, I have added 2>/dev/null to stop the errors appearing on screen.

Thanks again.

Adrian

---

