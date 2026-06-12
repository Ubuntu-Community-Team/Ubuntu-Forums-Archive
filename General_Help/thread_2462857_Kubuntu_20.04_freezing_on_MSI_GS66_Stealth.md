---
title: "Kubuntu 20.04 freezing on MSI GS66 Stealth"
date: 2021-05-28
forum: General Help
---

### Post by veramocor on 2021-05-28
Hi all, I am running Kubuntu 20.04 on a MSI GS66 Stealth. Everything is working great ... except about once a week the computer crashes. Specifically, everything freezes and will not respond to any keyboard or mouse commands. The only recourse is then to perform a hard reset via the power button. Here are the contents of /var/log/syslog in the moments leading to the crash:

[FONT=monospace][COLOR=#000000]ay 28 18:26:14 dracolich dbus-daemon[745]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service' requested by ':1.11' (uid=0 pid=746 comm="/usr/sbin/NetworkManager --no-daemon " label="unconfined"[/COLOR]
) 
May 28 18:26:14 dracolich NetworkManager[746]: <info>  [1622251574.0546] device (wlo1): state change: ip-config -> ip-check (reason 'none', sys-iface-state: 'managed') 
May 28 18:26:14 dracolich systemd[1]: Starting Network Manager Script Dispatcher Service... 
May 28 18:26:14 dracolich dbus-daemon[745]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher' 
May 28 18:26:14 dracolich systemd[1]: Started Network Manager Script Dispatcher Service. 
May 28 18:26:14 dracolich NetworkManager[746]: <info>  [1622251574.0687] device (wlo1): state change: ip-check -> secondaries (reason 'none', sys-iface-state: 'managed') 
May 28 18:26:14 dracolich NetworkManager[746]: <info>  [1622251574.0689] device (wlo1): state change: secondaries -> activated (reason 'none', sys-iface-state: 'managed') 
May 28 18:26:14 dracolich NetworkManager[746]: <info>  [1622251574.0693] manager: NetworkManager state is now CONNECTED_LOCAL 
May 28 18:26:14 dracolich NetworkManager[746]: <info>  [1622251574.0716] manager: NetworkManager state is now CONNECTED_SITE 
May 28 18:26:14 dracolich NetworkManager[746]: <info>  [1622251574.0718] policy: set 'cybertron' (wlo1) as default for IPv4 routing and DNS 
May 28 18:26:14 dracolich NetworkManager[746]: <info>  [1622251574.0723] device (wlo1): Activation: successful, device activated. 
May 28 18:26:14 dracolich NetworkManager[746]: <info>  [1622251574.0729] manager: NetworkManager state is now CONNECTED_GLOBAL 
May 28 18:26:14 dracolich whoopsie[1424]: [18:26:14] The default IPv4 route is: /org/freedesktop/NetworkManager/ActiveConnection/19 
May 28 18:26:14 dracolich whoopsie[1424]: [18:26:14] Not a paid data plan: /org/freedesktop/NetworkManager/ActiveConnection/19 
May 28 18:26:14 dracolich whoopsie[1424]: [18:26:14] Found usable connection: /org/freedesktop/NetworkManager/ActiveConnection/19 
May 28 18:26:14 dracolich whoopsie[1424]: [18:26:14] online 
May 28 18:26:23 dracolich wpa_supplicant[784]: wlo1: CTRL-EVENT-SIGNAL-CHANGE above=1 signal=-39 noise=9999 txrate=866700 
May 28 18:26:24 dracolich systemd[1]: NetworkManager-dispatcher.service: Succeeded. 
May 28 18:26:27 dracolich systemd-resolved[693]: Using degraded feature set (UDP) for DNS server 192.168.0.104. 
May 28 18:26:29 dracolich wpa_supplicant[784]: wlo1: CTRL-EVENT-SIGNAL-CHANGE above=1 signal=-39 noise=9999 txrate=866700 
May 28 18:27:28 dracolich kernel: [267154.127703] i915 0000:00:02.0: [drm] *ERROR* Atomic update failure on pipe A (start=20230 end=20231) time 220 us, min 1053, max 1079, scanline start 1023, end 1082 
May 28 18:29:21 dracolich kernel: [267266.367089] i915 0000:00:02.0: [drm] Resetting rcs0 for preemption time out 
May 28 18:29:21 dracolich kernel: [267266.367792] i915 0000:00:02.0: [drm] *ERROR* rcs0 reset request timed out: {request: 00000001, RESET_CTL: 00000001} 
May 28 18:29:21 dracolich kernel: [267266.374443] i915 0000:00:02.0: [drm] GPU HANG: ecode 9:1:85dffffa, in Xorg [988] 
[COLOR=#ffffff]^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@[/COLOR]
[COLOR=#ffffff]^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@[/COLOR]
[/FONT]

Please let me know what other information you might need to help me trouble-shoot this. I greatly appreciate any and all help.

---

### Post by veramocor on 2021-05-28
Also, here is the output from uname -a:

[FONT=monospace][COLOR=#000000]Linux dracolich 5.8.0-53-generic #60~20.04.1-Ubuntu SMP Thu May 6 09:52:46 UTC 2021 x86_[/COLOR]64 x86_64 x86_64 GNU/Linux
[/FONT]

---

### Post by Yellow Pasque on 2021-05-30
Can you test a mainline kernel and see if the problem still occurs?
[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)
[https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.12.8/](https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.12.8/)

---

### Post by veramocor on 2021-06-01
It just happened again. What on Earth is happening here? Here is the contents of /var/log/syslog leading up to the crash:

[FONT=monospace][COLOR=#000000]May 31 21:48:25 dracolich kernel: [26842.403417] i915 0000:00:02.0: [drm] *ERROR* Atomic update failure on pipe A (start=6444652 end=6444653) time 152 us, min 1053, max 1079, scanline start 1048, end 1084 [/COLOR]
May 31 21:50:52 dracolich kernel: [26989.353671] i915 0000:00:02.0: [drm] *ERROR* Atomic update failure on pipe A (start=6479920 end=6479921) time 234 us, min 1053, max 1079, scanline start 1019, end 1078 
May 31 21:54:42 dracolich rtkit-daemon[1057]: Supervising 6 threads of 4 processes of 1 users. 
May 31 21:55:58 dracolich rtkit-daemon[1057]: message repeated 7 times: [ Supervising 6 threads of 4 processes of 1 users.] 
May 31 21:55:58 dracolich rtkit-daemon[1057]: Successfully made thread 13872 of process 13772 owned by '1000' RT at priority 10. 
May 31 21:55:58 dracolich rtkit-daemon[1057]: Supervising 7 threads of 5 processes of 1 users. 
May 31 22:06:37 dracolich wpa_supplicant[791]: wlo1: WPA: Group rekeying completed with 1c:3b:f3:3b:5c:ab [GTK=CCMP] 
May 31 22:10:34 dracolich kernel: [28171.931412] i915 0000:00:02.0: [drm] Resetting rcs0 for preemption time out 
May 31 22:10:34 dracolich kernel: [28171.932115] i915 0000:00:02.0: [drm] *ERROR* rcs0 reset request timed out: {request: 00000001, RESET_CTL: 00000001} 
May 31 22:10:34 dracolich kernel: [28171.945593] i915 0000:00:02.0: [drm] GPU HANG: ecode 9:1:85dffffa, in Renderer [1803] 
May 31 22:10:44 dracolich kernel: [28181.654622] Asynchronous wait on fence 0000:00:02.0:kwin_x11[1270]:88250 timed out (hint:intel_atomic_commit_ready [i915]) 
[COLOR=#ffffff]^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@[/COLOR][COLOR=#000000] [/COLOR]
[COLOR=#ffffff]^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@[/COLOR][COLOR=#000000] [/COLOR]
[COLOR=#ffffff]^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@[/COLOR][COLOR=#000000] [/COLOR]
[COLOR=#ffffff]^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@[/COLOR][COLOR=#000000] [/COLOR]
[COLOR=#ffffff]^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@[/COLOR][COLOR=#000000] [/COLOR]
[COLOR=#ffffff]^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@[/COLOR][COLOR=#000000] [/COLOR]
[COLOR=#ffffff]^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@[/COLOR][COLOR=#000000] [/COLOR]
[COLOR=#ffffff]^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@[/COLOR][COLOR=#000000]M[/COLOR]
[/FONT]

---

### Post by Yellow Pasque on 2021-06-01
> **veramocor said:**
> It just happened again. 

Is this with the 5.12.x kernel?

---

### Post by veramocor on 2021-06-01
> **Yellow Pasque said:**
> Is this with the 5.12.x kernel?

My kernel is [FONT=monospace][COLOR=#000000]"5.8.0-53-generic". Thank you for your response above BTW. I am a complete newbie when it comes to changing kernel, so I'm investigating exactly how to do that without doing anything catastrophic. I have also been looking up some of the error messages I see in syslog, such as "GPU HANG", and have found forum pages that vaguely suggest kernel change, but it's unclear which one I should use. Any suggestions on a "kernel change for dummies" site and which kernels I should be trying would be most welcome![/COLOR] I was hoping that the messages from the syslog would provide enough information to pinpoint the issue.
[/FONT]

---

### Post by Yellow Pasque on 2021-06-02
```
cd ~/ && mkdir kernel512 && cd kernel512
wget https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.12.8/amd64/linux-headers-5.12.8-051208-generic_5.12.8-051208.202105281232_amd64.deb
wget https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.12.8/amd64/linux-headers-5.12.8-051208_5.12.8-051208.202105281232_all.deb
wget https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.12.8/amd64/linux-image-unsigned-5.12.8-051208-generic_5.12.8-051208.202105281232_amd64.deb
wget https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.12.8/amd64/linux-modules-5.12.8-051208-generic_5.12.8-051208.202105281232_amd64.deb
sudo dkpg -i linux-*
```
Reboot.

---

### Post by veramocor on 2021-06-03
> **Yellow Pasque said:**
> ```
cd ~/ && mkdir kernel512 && cd kernel512
wget https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.12.8/amd64/linux-headers-5.12.8-051208-generic_5.12.8-051208.202105281232_amd64.deb
wget https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.12.8/amd64/linux-headers-5.12.8-051208_5.12.8-051208.202105281232_all.deb
wget https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.12.8/amd64/linux-image-unsigned-5.12.8-051208-generic_5.12.8-051208.202105281232_amd64.deb
wget https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.12.8/amd64/linux-modules-5.12.8-051208-generic_5.12.8-051208.202105281232_amd64.deb
sudo dkpg -i linux-*
```
Reboot.

Thank you! I will try this.

---

### Post by veramocor on 2021-06-28
The system has been stable these past three weeks with no crashes, leading me to believe the problem had been solved. However, it just crashed again, this time with different messages in the syslog:

[FONT=monospace][COLOR=#000000]Jun 28 09:17:22 dracolich kernel: [321810.267068] iwlwifi 0000:00:14.3: Unhandled alg: 0x71b [/COLOR]
Jun 28 09:17:22 dracolich kernel: [321810.267088] iwlwifi 0000:00:14.3: Unhandled alg: 0x71b 
Jun 28 09:17:23 dracolich kernel: [321810.507663] iwlwifi 0000:00:14.3: Unhandled alg: 0x71b 
Jun 28 09:17:01 dracolich rtkit-daemon[1056]: Supervising 1 threads of 1 processes of 1 users. 
Jun 28 09:17:25 dracolich wpa_supplicant[785]: wlo1: CTRL-EVENT-SIGNAL-CHANGE above=0 signal=-73 noise=9999 txrate=292500 
Jun 28 09:17:27 dracolich kernel: [321814.365466] iwlwifi 0000:00:14.3: Unhandled alg: 0x71b 
Jun 28 09:17:27 dracolich kernel: [321814.727562] iwlwifi 0000:00:14.3: Unhandled alg: 0x71b 
Jun 28 09:17:27 dracolich kernel: [321814.924991] iwlwifi 0000:00:14.3: Unhandled alg: 0x71b 
Jun 28 09:17:28 dracolich kernel: [321815.396736] iwlwifi 0000:00:14.3: Unhandled alg: 0x71b 
Jun 28 09:17:28 dracolich kernel: [321815.396768] iwlwifi 0000:00:14.3: Unhandled alg: 0x71b 
Jun 28 09:17:28 dracolich kernel: [321816.160987] iwlwifi 0000:00:14.3: Unhandled alg: 0x71b 
Jun 28 09:17:29 dracolich kernel: [321816.418301] iwlwifi 0000:00:14.3: Unhandled alg: 0x71b 
Jun 28 09:17:30 dracolich kernel: [321818.029578] iwlwifi 0000:00:14.3: Unhandled alg: 0x71b 
Jun 28 09:17:30 dracolich kernel: [321818.162910] iwlwifi 0000:00:14.3: Unhandled alg: 0x71b 
Jun 28 09:17:30 dracolich kernel: [321818.166996] iwlwifi 0000:00:14.3: Unhandled alg: 0x71b 
Jun 28 09:17:34 dracolich kernel: [321822.083733] net_ratelimit: 6 callbacks suppressed 
Jun 28 09:17:34 dracolich kernel: [321822.083739] iwlwifi 0000:00:14.3: Unhandled alg: 0x71b 
Jun 28 09:17:37 dracolich kernel: [321824.333132] iwlwifi 0000:00:14.3: Unhandled alg: 0x71b 
Jun 28 09:17:37 dracolich kernel: [321824.333154] iwlwifi 0000:00:14.3: Unhandled alg: 0x71b 
Jun 28 09:17:37 dracolich kernel: [321824.333161] iwlwifi 0000:00:14.3: Unhandled alg: 0x71b 
Jun 28 09:17:37 dracolich kernel: [321824.553341] iwlwifi 0000:00:14.3: Unhandled alg: 0x71b 
Jun 28 09:17:37 dracolich kernel: [321824.575428] iwlwifi 0000:00:14.3: Unhandled alg: 0x71b 
Jun 28 09:17:37 dracolich kernel: [321824.609975] iwlwifi 0000:00:14.3: Unhandled alg: 0x71b 
Jun 28 09:17:37 dracolich kernel: [321824.609986] iwlwifi 0000:00:14.3: Unhandled alg: 0x71b 
Jun 28 09:17:37 dracolich kernel: [321824.708436] iwlwifi 0000:00:14.3: Unhandled alg: 0x71b 
Jun 28 09:17:37 dracolich kernel: [321824.776725] iwlwifi 0000:00:14.3: Unhandled alg: 0x71b 
Jun 28 09:17:40 dracolich kernel: [321828.163398] net_ratelimit: 2 callbacks suppressed 
Jun 28 09:17:40 dracolich kernel: [321828.163401] iwlwifi 0000:00:14.3: Unhandled alg: 0x71b 
Jun 28 09:17:40 dracolich kernel: [321828.163658] iwlwifi 0000:00:14.3: Unhandled alg: 0x71b 
Jun 28 09:17:40 dracolich kernel: [321828.167517] iwlwifi 0000:00:14.3: Unhandled alg: 0x71b 
Jun 28 09:17:40 dracolich kernel: [321828.167521] iwlwifi 0000:00:14.3: Unhandled alg: 0x71b 
Jun 28 09:17:40 dracolich kernel: [321828.234732] iwlwifi 0000:00:14.3: Unhandled alg: 0x71b 
Jun 28 09:17:44 dracolich kernel: [321832.014768] iwlwifi 0000:00:14.3: Unhandled alg: 0x71b 
Jun 28 09:17:45 dracolich kernel: [321832.599553] iwlwifi 0000:00:14.3: Unhandled alg: 0x71b 
Jun 28 09:17:45 dracolich kernel: [321832.650514] iwlwifi 0000:00:14.3: Unhandled alg: 0x71b 
Jun 28 09:17:45 dracolich kernel: [321832.891664] iwlwifi 0000:00:14.3: Unhandled alg: 0x71b 
Jun 28 09:17:47 dracolich kernel: [321835.022307] iwlwifi 0000:00:14.3: Unhandled alg: 0x71b 
Jun 28 09:17:50 dracolich kernel: [321837.899223] iwlwifi 0000:00:14.3: Unhandled alg: 0x71b 
Jun 28 09:17:53 dracolich kernel: [321840.572389] iwlwifi 0000:00:14.3: Unhandled alg: 0x71b 
Jun 28 09:17:54 dracolich kernel: [321842.168862] iwlwifi 0000:00:14.3: Unhandled alg: 0x71b 
Jun 28 09:17:55 dracolich kernel: [321842.419316] iwlwifi 0000:00:14.3: Unhandled alg: 0x71b 
Jun 28 09:17:55 dracolich kernel: [321842.636869] iwlwifi 0000:00:14.3: Unhandled alg: 0x71b 
Jun 28 09:17:57 dracolich kernel: [321844.483152] iwlwifi 0000:00:14.3: Unhandled alg: 0x71b 
Jun 28 09:17:57 dracolich kernel: [321844.573580] iwlwifi 0000:00:14.3: Unhandled alg: 0x71b 
Jun 28 09:17:57 dracolich kernel: [321844.636573] iwlwifi 0000:00:14.3: Unhandled alg: 0x71b 
Jun 28 09:17:57 dracolich kernel: [321844.796559] iwlwifi 0000:00:14.3: Unhandled alg: 0x71b 
Jun 28 09:17:57 dracolich kernel: [321844.868921] iwlwifi 0000:00:14.3: Unhandled alg: 0x71b 
Jun 28 09:17:57 dracolich kernel: [321845.030444] iwlwifi 0000:00:14.3: Unhandled alg: 0x71b 
[COLOR=#ffffff]^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@[/COLOR][COLOR=#000000] [/COLOR]
[COLOR=#ffffff]^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@[/COLOR][COLOR=#000000] [/COLOR]
[COLOR=#ffffff]^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@[/COLOR][COLOR=#000000] [/COLOR]
[COLOR=#ffffff]^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@[/COLOR][COLOR=#000000] [/COLOR]
[COLOR=#ffffff]^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@[/COLOR][COLOR=#000000] [/COLOR]
[COLOR=#ffffff]^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@[/COLOR][COLOR=#000000] [/COLOR]
[COLOR=#ffffff]^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@[/COLOR][COLOR=#000000] [/COLOR]
[COLOR=#ffffff]^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@

[/COLOR]This seems wifi related, no?
[/FONT]

---

### Post by veramocor on 2021-06-28
And ... happen again ... just a few hours later. Here is the syslog before crash:

[FONT=monospace][COLOR=#000000]Jun 28 15:34:13 dracolich kernel: [22334.408095] i915 0000:00:02.0: [drm] *ERROR* Atomic update failure on pipe A (start=5362779 end=5362780) time 177 us, min 1053, max 1079, scanline start 1042, end 1088 [/COLOR]
Jun 28 15:35:41 dracolich kernel: [22421.899807] i915 0000:00:02.0: [drm] *ERROR* Atomic update failure on pipe A (start=5383777 end=5383778) time 129 us, min 1053, max 1079, scanline start 1048, end 1080 
Jun 28 15:41:11 dracolich kernel: [22752.425098] i915 0000:00:02.0: [drm] *ERROR* Atomic update failure on pipe A (start=5463103 end=5463104) time 169 us, min 1053, max 1079, scanline start 1041, end 1084 
Jun 28 15:41:28 dracolich kernel: [22769.039518] i915 0000:00:02.0: [drm] Resetting rcs0 for preemption time out 
Jun 28 15:41:28 dracolich kernel: [22769.040232] i915 0000:00:02.0: [drm] *ERROR* rcs0 reset request timed out: {request: 00000001, RESET_CTL: 00000001} 
Jun 28 15:41:28 dracolich kernel: [22769.044968] i915 0000:00:02.0: [drm] GPU HANG: ecode 9:1:85dffffa, in Xorg [994] 
Jun 28 15:41:37 dracolich kernel: [22778.575152] Asynchronous wait on fence 0000:00:02.0:kwin_x11[1271]:18e898 timed out (hint:intel_atomic_commit_ready [i915]) 
[COLOR=#ffffff]^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@[/COLOR]
[/FONT]

---

### Post by mastablasta on 2021-07-01
what GPU do you have? Intel?

[COLOR=#000000][FONT=monospace]GPU HANG: ecode 9:1:85dffffa, in Xorg [994]

are you maybe experiencing overheating? what happens if you stress test the GPU (you can use phoronix test suite for that).[/FONT][/COLOR]

---

