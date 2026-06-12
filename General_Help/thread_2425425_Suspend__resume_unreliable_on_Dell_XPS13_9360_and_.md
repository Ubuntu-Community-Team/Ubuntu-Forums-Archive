---
title: "Suspend / resume unreliable on Dell XPS13 9360 and Kernel 5"
date: 2019-08-26
forum: General Help
---

### Post by mobile-harvey on 2019-08-26
Hi

I am running Kubuntu 18.04, fully updated with  the 5.0 kernel, on a Dell XPS13 9360. I tend to put the laptop to sleep  by closing the lid when not using it. It will also automatically sleep  after 10 idle minutes when on battery. Basically the default Plasma  power settings.

Mostly the laptop will sleep and resume no problem,  but fairly frequently (perhaps once every couple of days) it will freeze  with a blank screen (sometimes with just the pointer visible) and the power light on. This can happen when  sleeping after being idle for 10 minutes, or when the lid is closed.  Also sometimes it will not sleep when the lid is closed, meaning when I  later open the lid the laptop still responds but has a drained battery.

I  am finding it difficult to diagnose these problems so does anyone know  which logs I should look at to try to pin this down? Of course if anyone  has seen this before and knows how to fix it then even better! I am seeing the same problem on KDE Neon User Edition and my hunch is the recent Kernel 5.0 upgrade may be a factor as this problem was not seen prior to then.

Thanks in advance for any help.
Nick

---

### Post by mobile-harvey on 2019-08-26
I have just triggered this manually by selecting 'suspend from the  KDE 'leave' menu. This resulted in a blank screen with just the cursor  displayed and the whole machine locked-up. So this is fairly reliably  reproducible. I would love to know where to start in diagnosing this as  this is seriously affecting my trust in this set-up.

---

### Post by Doug S on 2019-08-27
Has it always had this issue, or only with kernel 5.0? You might find some useful information in /var/log/kern.log and/or /var/log/syslog. As a test, and to determine if the issue is already fixed upstream, you could also try the [Ubuntu mainline kernel 5.3-rc6]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.3-rc6/").

---

### Post by mobile-harvey on 2019-08-27
Hi Doug

I am pretty certain this has started since the HWE kernel 5.0 update was available. I was originally running KDE Neon which was fine prior to the kernel update. Then this problem occurred so I re-installed using Kubuntu 18.04 (with the same kernel) and I am getting the same issue. I will see if I can test the latest RC kernel as you suggest, meanwhile here are some logs in case this helps. I shut the lid on my laptop at 19:25:18 and then had to hard reboot at 20:41:25 when I opened the lid and found the laptop had locked-up.

```

vi /var/log/sysog
Aug 27 19:25:18 ubuntu-xps13 NetworkManager[1062]: <info>  [1566930318.8584] manager: sleep: sleep requested (sleeping: no  enabled: yes)
Aug 27 19:25:18 ubuntu-xps13 NetworkManager[1062]: <info>  [1566930318.8587] manager: NetworkManager state is now ASLEEP
Aug 27 19:25:18 ubuntu-xps13 NetworkManager[1062]: <info>  [1566930318.8595] device (wlp58s0): state change: activated -> deactivating (reason 'sleeping', sys-iface-state: 'managed')
Aug 27 19:25:18 ubuntu-xps13 whoopsie[1374]: [19:25:18] offline
Aug 27 19:25:18 ubuntu-xps13 dbus-daemon[1055]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service' requested by ':1.11' (uid=0 pid=1062 comm="/usr/sbin/NetworkManager --no-daemon " label="unconfined")
Aug 27 19:25:18 ubuntu-xps13 NetworkManager[1062]: <info>  [1566930318.8708] device (wlp58s0): state change: deactivating -> disconnected (reason 'sleeping', sys-iface-state: 'managed')
Aug 27 19:25:18 ubuntu-xps13 avahi-daemon[1021]: Withdrawing address record for fd4a:cc37:2d32:1:4090:ea35:ea9b:2ec5 on wlp58s0.
Aug 27 19:25:18 ubuntu-xps13 avahi-daemon[1021]: Withdrawing address record for fd4a:cc37:2d32:1:1520:16a8:27d3:6bf8 on wlp58s0.
Aug 27 19:25:18 ubuntu-xps13 avahi-daemon[1021]: Leaving mDNS multicast group on interface wlp58s0.IPv6 with address fd4a:cc37:2d32:1:1520:16a8:27d3:6bf8.
Aug 27 19:25:18 ubuntu-xps13 avahi-daemon[1021]: Joining mDNS multicast group on interface wlp58s0.IPv6 with address fe80::1233:9f84:1748:a070.
Aug 27 19:25:18 ubuntu-xps13 avahi-daemon[1021]: Registering new address record for fe80::1233:9f84:1748:a070 on wlp58s0.*.
Aug 27 19:25:18 ubuntu-xps13 avahi-daemon[1021]: Withdrawing address record for fe80::1233:9f84:1748:a070 on wlp58s0.
Aug 27 19:25:18 ubuntu-xps13 avahi-daemon[1021]: Leaving mDNS multicast group on interface wlp58s0.IPv6 with address fe80::1233:9f84:1748:a070.
Aug 27 19:25:18 ubuntu-xps13 avahi-daemon[1021]: Interface wlp58s0.IPv6 no longer relevant for mDNS.
Aug 27 19:25:18 ubuntu-xps13 systemd[1]: Starting Network Manager Script Dispatcher Service...
Aug 27 19:25:18 ubuntu-xps13 dbus-daemon[1055]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Aug 27 19:25:18 ubuntu-xps13 systemd[1]: Started Network Manager Script Dispatcher Service.
Aug 27 19:25:18 ubuntu-xps13 nm-dispatcher: req:1 'connectivity-change': new request (2 scripts)
Aug 27 19:25:18 ubuntu-xps13 nm-dispatcher: req:1 'connectivity-change': start running ordered scripts...
Aug 27 19:25:18 ubuntu-xps13 NetworkManager[1062]: <info>  [1566930318.9055] dhcp4 (wlp58s0): canceled DHCP transaction, DHCP client pid 9738
Aug 27 19:25:18 ubuntu-xps13 NetworkManager[1062]: <info>  [1566930318.9056] dhcp4 (wlp58s0): state changed bound -> done
Aug 27 19:25:18 ubuntu-xps13 kernel: [13523.266260] wlp58s0: deauthenticating from 68:ff:7b:25:f3:23 by local choice (Reason: 3=DEAUTH_LEAVING)
Aug 27 19:25:18 ubuntu-xps13 wpa_supplicant[1061]: wlp58s0: CTRL-EVENT-DISCONNECTED bssid=68:ff:7b:25:f3:23 reason=3 locally_generated=1
Aug 27 19:25:18 ubuntu-xps13 avahi-daemon[1021]: Withdrawing address record for 192.168.68.134 on wlp58s0.
Aug 27 19:25:18 ubuntu-xps13 avahi-daemon[1021]: Leaving mDNS multicast group on interface wlp58s0.IPv4 with address 192.168.68.134.
Aug 27 19:25:18 ubuntu-xps13 avahi-daemon[1021]: Interface wlp58s0.IPv4 no longer relevant for mDNS.
Aug 27 19:25:18 ubuntu-xps13 whoopsie[1374]: [19:25:18] Cannot reach: [https://daisy.ubuntu.com](https://daisy.ubuntu.com)
Aug 27 19:25:18 ubuntu-xps13 NetworkManager[1062]: <warn>  [1566930318.9294] sup-iface[0x562967f7fb80,wlp58s0]: connection disconnected (reason -3)
Aug 27 19:25:18 ubuntu-xps13 NetworkManager[1062]: <info>  [1566930318.9298] device (wlp58s0): supplicant interface state: completed -> disconnected
Aug 27 19:25:18 ubuntu-xps13 NetworkManager[1062]: <info>  [1566930318.9319] device (wlp58s0): state change: disconnected -> unmanaged (reason 'sleeping', sys-iface-state: 'managed')
Aug 27 19:25:18 ubuntu-xps13 nm-dispatcher: req:2 'down' [wlp58s0]: new request (2 scripts)
Aug 27 19:25:18 ubuntu-xps13 nm-dispatcher: req:2 'down' [wlp58s0]: start running ordered scripts...
Aug 27 19:25:19 ubuntu-xps13 wpa_supplicant[1061]: nl80211: deinit ifname=p2p-dev-wlp58s0 disabled_11b_rates=0
Aug 27 19:25:19 ubuntu-xps13 systemd[1]: Starting TLP suspend/resume...
Aug 27 19:25:19 ubuntu-xps13 wpa_supplicant[1061]: nl80211: deinit ifname=wlp58s0 disabled_11b_rates=0
Aug 27 19:25:19 ubuntu-xps13 systemd[1]: Started TLP suspend/resume.
Aug 27 19:25:19 ubuntu-xps13 systemd[1]: Reached target Sleep.
Aug 27 19:25:19 ubuntu-xps13 systemd[1]: Starting Suspend...
Aug 27 19:25:19 ubuntu-xps13 systemd-sleep[18952]: Suspending system...
Aug 27 20:41:26 ubuntu-xps13 systemd-modules-load[520]: Inserted module 'lp'


vi /var/log/kern.log
Aug 27 19:25:18 ubuntu-xps13 kernel: [13523.266260] wlp58s0: deauthenticating from 68:ff:7b:25:f3:23 by local choice (Reason: 3=DEAUTH_LEAVING)


journalctl -r
Aug 27 20:41:25 ubuntu-xps13 kernel: Linux version 5.0.0-25-generic (buildd@lcy01-amd64-014) (gcc version 7.4.0 (Ubuntu 7.4.0-1ub
-- Reboot --
Aug 27 19:25:19 ubuntu-xps13 systemd-sleep[18952]: Suspending system...
Aug 27 19:25:19 ubuntu-xps13 systemd[1]: Starting Suspend...
Aug 27 19:25:19 ubuntu-xps13 systemd[1]: Reached target Sleep.
Aug 27 19:25:19 ubuntu-xps13 systemd[1]: Started TLP suspend/resume.
Aug 27 19:25:19 ubuntu-xps13 wpa_supplicant[1061]: nl80211: deinit ifname=wlp58s0 disabled_11b_rates=0
Aug 27 19:25:19 ubuntu-xps13 systemd[1]: Starting TLP suspend/resume...
Aug 27 19:25:19 ubuntu-xps13 wpa_supplicant[1061]: nl80211: deinit ifname=p2p-dev-wlp58s0 disabled_11b_rates=0
Aug 27 19:25:18 ubuntu-xps13 nm-dispatcher[18808]: req:2 'down' [wlp58s0]: start running ordered scripts...
Aug 27 19:25:18 ubuntu-xps13 nm-dispatcher[18808]: req:2 'down' [wlp58s0]: new request (2 scripts)
Aug 27 19:25:18 ubuntu-xps13 NetworkManager[1062]: <info>  [1566930318.9319] device (wlp58s0): state change: disconnected -> unma
Aug 27 19:25:18 ubuntu-xps13 NetworkManager[1062]: <info>  [1566930318.9298] device (wlp58s0): supplicant interface state: comple
Aug 27 19:25:18 ubuntu-xps13 NetworkManager[1062]: <warn>  [1566930318.9294] sup-iface[0x562967f7fb80,wlp58s0]: connection discon
Aug 27 19:25:18 ubuntu-xps13 whoopsie[1374]: [19:25:18] Cannot reach: [https://daisy.ubuntu.com](https://daisy.ubuntu.com)
Aug 27 19:25:18 ubuntu-xps13 avahi-daemon[1021]: Interface wlp58s0.IPv4 no longer relevant for mDNS.
Aug 27 19:25:18 ubuntu-xps13 avahi-daemon[1021]: Leaving mDNS multicast group on interface wlp58s0.IPv4 with address 192.168.68.1
Aug 27 19:25:18 ubuntu-xps13 avahi-daemon[1021]: Withdrawing address record for 192.168.68.134 on wlp58s0.
Aug 27 19:25:18 ubuntu-xps13 wpa_supplicant[1061]: wlp58s0: CTRL-EVENT-DISCONNECTED bssid=68:ff:7b:25:f3:23 reason=3 locally_gene
Aug 27 19:25:18 ubuntu-xps13 kernel: wlp58s0: deauthenticating from 68:ff:7b:25:f3:23 by local choice (Reason: 3=DEAUTH_LEAVING)
Aug 27 19:25:18 ubuntu-xps13 NetworkManager[1062]: <info>  [1566930318.9056] dhcp4 (wlp58s0): state changed bound -> done
Aug 27 19:25:18 ubuntu-xps13 NetworkManager[1062]: <info>  [1566930318.9055] dhcp4 (wlp58s0): canceled DHCP transaction, DHCP cli
Aug 27 19:25:18 ubuntu-xps13 nm-dispatcher[18808]: req:1 'connectivity-change': start running ordered scripts...
Aug 27 19:25:18 ubuntu-xps13 nm-dispatcher[18808]: req:1 'connectivity-change': new request (2 scripts)
Aug 27 19:25:18 ubuntu-xps13 systemd[1]: Started Network Manager Script Dispatcher Service.
Aug 27 19:25:18 ubuntu-xps13 dbus-daemon[1055]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Aug 27 19:25:18 ubuntu-xps13 systemd[1]: Starting Network Manager Script Dispatcher Service...
Aug 27 19:25:18 ubuntu-xps13 avahi-daemon[1021]: Interface wlp58s0.IPv6 no longer relevant for mDNS.
Aug 27 19:25:18 ubuntu-xps13 avahi-daemon[1021]: Leaving mDNS multicast group on interface wlp58s0.IPv6 with address fe80::1233:9
Aug 27 19:25:18 ubuntu-xps13 avahi-daemon[1021]: Withdrawing address record for fe80::1233:9f84:1748:a070 on wlp58s0.
Aug 27 19:25:18 ubuntu-xps13 avahi-daemon[1021]: Registering new address record for fe80::1233:9f84:1748:a070 on wlp58s0.*.
Aug 27 19:25:18 ubuntu-xps13 avahi-daemon[1021]: Joining mDNS multicast group on interface wlp58s0.IPv6 with address fe80::1233:9
Aug 27 19:25:18 ubuntu-xps13 avahi-daemon[1021]: Leaving mDNS multicast group on interface wlp58s0.IPv6 with address fd4a:cc37:2d
Aug 27 19:25:18 ubuntu-xps13 avahi-daemon[1021]: Withdrawing address record for fd4a:cc37:2d32:1:1520:16a8:27d3:6bf8 on wlp58s0.
Aug 27 19:25:18 ubuntu-xps13 avahi-daemon[1021]: Withdrawing address record for fd4a:cc37:2d32:1:4090:ea35:ea9b:2ec5 on wlp58s0.
Aug 27 19:25:18 ubuntu-xps13 NetworkManager[1062]: <info>  [1566930318.8708] device (wlp58s0): state change: deactivating -> disc
Aug 27 19:25:18 ubuntu-xps13 dbus-daemon[1055]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' uni
Aug 27 19:25:18 ubuntu-xps13 whoopsie[1374]: [19:25:18] offline
Aug 27 19:25:18 ubuntu-xps13 NetworkManager[1062]: <info>  [1566930318.8595] device (wlp58s0): state change: activated -> deactiv
Aug 27 19:25:18 ubuntu-xps13 NetworkManager[1062]: <info>  [1566930318.8587] manager: NetworkManager state is now ASLEEP
Aug 27 19:25:18 ubuntu-xps13 NetworkManager[1062]: <info>  [1566930318.8584] manager: sleep: sleep requested (sleeping: no  enabl
Aug 27 19:25:18 ubuntu-xps13 systemd-logind[1066]: Lid closed.


```

---

### Post by mobile-harvey on 2019-08-27
OK - I am now running kernel 5.3-rc6 and initial tests are proving positive. I have just done about 15 suspends in a row. No lockups and the majority of the suspends resulted in a suspended laptop. A few however - say every 4-5 attempts - resulted in the laptop just going straight back to the lock screen, almost as if it had suspended and immediately resumed again. I will run this kernel for a few days and see if I get any more lock-ups and will report back.

Thanks,
Nick

---

### Post by mobile-harvey on 2019-08-29
I have raised a bug on the 5.0.0.25 kernel: [https://bugs.launchpad.net/ubuntu/+source/linux-signed-hwe/+bug/1841905](https://bugs.launchpad.net/ubuntu/+source/linux-signed-hwe/+bug/1841905)

---

### Post by Doug S on 2019-08-29
> **mobile-harvey said:**
> I have raised a bug on the 5.0.0.25 kernel: [https://bugs.launchpad.net/ubuntu/+source/linux-signed-hwe/+bug/1841905](https://bugs.launchpad.net/ubuntu/+source/linux-signed-hwe/+bug/1841905)O.K. I don't know that you will get anywhere with that bug report. If upstream is fixed, then what else is there to do? I am on the linux-pm (linux power management) e-mail list, and there is currently (actually always) suspend related activity. Likely your new problem will get sorted out eventually upstream.

My recommendation for you would be to find an older kernel that works for you, then wait until a new one that works comes along. The alternative is to bisect the kernel to isolate the exact commit that introduced the issue, but such work is extremely time consuming.

---

### Post by mobile-harvey on 2019-08-29
Hi Doug - fair points. I'm certain the earlier kernel (4.18 was it?)  didn't have this problem. Is there a way to downgrade from the 5.0.0.25  to that one?

Thanks
Nick

---

