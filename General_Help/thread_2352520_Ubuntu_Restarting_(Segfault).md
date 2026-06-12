---
title: "Ubuntu Restarting (Segfault)"
date: 2017-02-13
forum: General Help
---

### Post by renny2125 on 2017-02-13
Hi there! I run Lubuntu 16.10 on a Pentium(R) Dual-Core E5200 @ 2.50GHZ\z

At the time of these crashes (about two in a row now), I've been playing Minecraft and a flash game called "Flower Knight Girl" in the background.

This is the output from /var/log/kern.log

```
Feb 12 00:48:56 rubicon-iii indicator-appli[1587]: Application already exists, re-requesting properties.
Feb 12 00:52:56 rubicon-iii indicator-appli[1587]: Application already exists, re-requesting properties.
Feb 12 00:54:42 rubicon-iii lightdm[807]: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
Feb 12 00:56:56 rubicon-iii indicator-appli[1587]: Application already exists, re-requesting properties.
Feb 12 01:02:56 rubicon-iii indicator-appli[1587]: Application already exists, re-requesting properties.
Feb 12 01:16:56 rubicon-iii indicator-appli[1587]: message repeated 4 times: [ Application already exists, re-requesting properties.]
Feb 12 01:18:56 rubicon-iii indicator-appli[1587]: Application already exists, re-requesting properties.
Feb 12 02:14:57 rubicon-iii indicator-appli[1587]: message repeated 18 times: [ Application already exists, re-requesting properties.]
Feb 12 02:18:56 rubicon-iii indicator-appli[1587]: Application already exists, re-requesting properties.
Feb 12 03:14:56 rubicon-iii indicator-appli[1587]: message repeated 22 times: [ Application already exists, re-requesting properties.]
Feb 12 03:20:56 rubicon-iii indicator-appli[1587]: Application already exists, re-requesting properties.
Feb 12 03:32:56 rubicon-iii indicator-appli[1587]: message repeated 5 times: [ Application already exists, re-requesting properties.]
Feb 12 03:33:29 rubicon-iii kernel: [10230.561729] perf: interrupt took too long (2504 > 2500), lowering kernel.perf_event_max_sample_rate to 79750
Feb 12 03:34:13 rubicon-iii kernel: [10274.834129] perf: interrupt took too long (3140 > 3130), lowering kernel.perf_event_max_sample_rate to 63500
Feb 12 03:34:57 rubicon-iii indicator-appli[1587]: Application already exists, re-requesting properties.
Feb 12 03:38:22 rubicon-iii kernel: [10524.141707] perf: interrupt took too long (3948 > 3925), lowering kernel.perf_event_max_sample_rate to 50500
Feb 12 03:38:57 rubicon-iii indicator-appli[1587]: Application already exists, re-requesting properties.
Feb 12 03:44:56 rubicon-iii kernel: [10918.116794] perf: interrupt took too long (4969 > 4935), lowering kernel.perf_event_max_sample_rate to 40250
Feb 12 03:49:49 rubicon-iii kernel: [11211.286362] perf: interrupt took too long (6226 > 6211), lowering kernel.perf_event_max_sample_rate to 32000
Feb 12 04:14:57 rubicon-iii indicator-appli[1587]: message repeated 8 times: [ Application already exists, re-requesting properties.]
Feb 12 04:20:57 rubicon-iii indicator-appli[1587]: Application already exists, re-requesting properties.
Feb 12 04:29:07 rubicon-iii kernel: [13568.285348] show_signal_msg: 24 callbacks suppressed
Feb 12 04:29:07 rubicon-iii kernel: [13568.285352] plugin-containe[6934]: segfault at 20562f7e3c4 ip 00007fb7899fe522 sp 00007ffc9c843ee8 error 6 in libflashplayer.so[7fb78938d000+107b000]
Feb 12 04:24:57 rubicon-iii indicator-appli[1587]: Application already exists, re-requesting properties.
Feb 12 04:34:57 rubicon-iii indicator-appli[1587]: Application already exists, re-requesting properties.
Feb 12 04:53:25 rubicon-iii indicator-appli[1587]: message repeated 3 times: [ Application already exists, re-requesting properties.]
Feb 12 05:01:03 rubicon-iii indicator-appli[1587]: Application already exists, re-requesting properties.
Feb 12 05:09:09 rubicon-iii kernel: [15969.328043] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Feb 12 05:09:14 rubicon-iii indicator-appli[1587]: Application already exists, re-requesting properties.
Feb 12 05:17:10 rubicon-iii indicator-appli[1587]: Application already exists, re-requesting properties.
Feb 12 05:29:06 rubicon-iii indicator-appli[1587]: message repeated 4 times: [ Application already exists, re-requesting properties.]
Feb 12 05:31:06 rubicon-iii indicator-appli[1587]: Application already exists, re-requesting properties.
Feb 12 05:31:18 rubicon-iii lightdm[807]: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
Feb 12 05:31:30 rubicon-iii at-spi-bus-laun[8474]: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
Feb 12 05:33:43 rubicon-iii lightdm[807]: Error using VT_WAITACTIVE 7 on /dev/tty0: Interrupted system call
Feb 12 05:35:10 rubicon-iii indicator-appli[1587]: Application already exists, re-requesting properties.
Feb 12 06:15:07 rubicon-iii indicator-appli[1587]: message repeated 15 times: [ Application already exists, re-requesting properties.]
Feb 12 06:17:06 rubicon-iii indicator-appli[1587]: Application already exists, re-requesting properties.
Feb 12 06:17:36 rubicon-iii lightdm[807]: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
Feb 12 06:17:38 rubicon-iii at-spi-bus-laun[10065]: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
Feb 12 06:19:06 rubicon-iii indicator-appli[1587]: Application already exists, re-requesting properties.
Feb 12 06:23:06 rubicon-iii indicator-appli[1587]: Application already exists, re-requesting properties.
Feb 12 06:23:33 rubicon-iii lightdm[807]: Error using VT_WAITACTIVE 7 on /dev/tty0: Interrupted system call
Feb 12 06:25:14 rubicon-iii indicator-appli[1587]: Application already exists, re-requesting properties.
Feb 12 06:28:36 rubicon-iii indicator-sound[1586]: Sink input info callback : SINK INPUT INFO IS NULL or our user_data is not what we think it should be
Feb 12 06:29:11 rubicon-iii indicator-appli[1587]: Application already exists, re-requesting properties.
Feb 12 06:39:08 rubicon-iii indicator-appli[1587]: message repeated 2 times: [ Application already exists, re-requesting properties.]
Feb 12 06:47:08 rubicon-iii indicator-appli[1587]: Application already exists, re-requesting properties.
Feb 12 06:47:16 rubicon-iii lightdm[807]: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
Feb 12 06:47:22 rubicon-iii at-spi-bus-laun[11064]: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
Feb 12 06:49:07 rubicon-iii indicator-appli[1587]: Application already exists, re-requesting properties.
Feb 12 07:11:07 rubicon-iii indicator-appli[1587]: message repeated 8 times: [ Application already exists, re-requesting properties.]
Feb 12 07:17:07 rubicon-iii indicator-appli[1587]: Application already exists, re-requesting properties.
Feb 12 07:29:07 rubicon-iii indicator-appli[1587]: message repeated 5 times: [ Application already exists, re-requesting properties.]
Feb 12 07:31:07 rubicon-iii indicator-appli[1587]: Application already exists, re-requesting properties.
Feb 12 07:55:07 rubicon-iii indicator-appli[1587]: message repeated 8 times: [ Application already exists, re-requesting properties.]
Feb 12 07:57:07 rubicon-iii indicator-appli[1587]: Application already exists, re-requesting properties.
Feb 12 08:06:07 rubicon-iii NetworkManager[669]: <warn>  [1486904767.2012] sup-iface[0x55ffceef8d90,wlx9cefd5ffaae6]: connection disconnected (reason -4)
Feb 12 08:06:07 rubicon-iii NetworkManager[669]: <info>  [1486904767.3576] device (wlx9cefd5ffaae6): supplicant interface state: completed -> scanning
Feb 12 08:06:08 rubicon-iii NetworkManager[669]: <info>  [1486904768.6848] device (wlx9cefd5ffaae6): supplicant interface state: scanning -> authenticating
Feb 12 08:06:08 rubicon-iii NetworkManager[669]: <info>  [1486904768.6912] device (wlx9cefd5ffaae6): supplicant interface state: authenticating -> associating
Feb 12 08:06:08 rubicon-iii NetworkManager[669]: <info>  [1486904768.7571] device (wlx9cefd5ffaae6): supplicant interface state: associating -> associated
Feb 12 08:06:08 rubicon-iii kernel: [26589.996765] wlx9cefd5ffaae6: authenticate with 04:a1:51:e7:09:0d
Feb 12 08:06:09 rubicon-iii kernel: [26590.023464] wlx9cefd5ffaae6: send auth to 04:a1:51:e7:09:0d (try 1/3)
Feb 12 08:06:09 rubicon-iii kernel: [26590.025268] wlx9cefd5ffaae6: authenticated
Feb 12 08:06:09 rubicon-iii kernel: [26590.028038] wlx9cefd5ffaae6: associate with 04:a1:51:e7:09:0d (try 1/3)
Feb 12 08:06:09 rubicon-iii kernel: [26590.032710] wlx9cefd5ffaae6: RX AssocResp from 04:a1:51:e7:09:0d (capab=0x411 status=0 aid=8)
Feb 12 08:06:09 rubicon-iii NetworkManager[669]: <info>  [1486904769.0331] device (wlx9cefd5ffaae6): supplicant interface state: associated -> 4-way handshake
Feb 12 08:06:09 rubicon-iii kernel: [26590.041068] wlx9cefd5ffaae6: associated
Feb 12 08:06:09 rubicon-iii NetworkManager[669]: <info>  [1486904769.0476] device (wlx9cefd5ffaae6): supplicant interface state: 4-way handshake -> completed
Feb 12 08:07:07 rubicon-iii indicator-appli[1587]: Application already exists, re-requesting properties.
Feb 12 08:15:07 rubicon-iii indicator-appli[1587]: message repeated 2 times: [ Application already exists, re-requesting properties.]
Feb 12 08:17:08 rubicon-iii indicator-appli[1587]: Application already exists, re-requesting properties.
Feb 12 09:15:08 rubicon-iii indicator-appli[1587]: message repeated 14 times: [ Application already exists, re-requesting properties.]
Feb 12 09:19:07 rubicon-iii indicator-appli[1587]: Application already exists, re-requesting properties.
Feb 12 10:13:07 rubicon-iii indicator-appli[1587]: message repeated 15 times: [ Application already exists, re-requesting properties.]
Feb 12 10:17:07 rubicon-iii indicator-appli[1587]: Application already exists, re-requesting properties.
Feb 12 10:25:07 rubicon-iii indicator-appli[1587]: message repeated 3 times: [ Application already exists, re-requesting properties.]
Feb 12 10:31:08 rubicon-iii indicator-appli[1587]: Application already exists, re-requesting properties.
Feb 12 11:15:07 rubicon-iii indicator-appli[1587]: message repeated 10 times: [ Application already exists, re-requesting properties.]
Feb 12 11:17:07 rubicon-iii indicator-appli[1587]: Application already exists, re-requesting properties.
Feb 12 12:15:07 rubicon-iii indicator-appli[1587]: message repeated 17 times: [ Application already exists, re-requesting properties.]
Feb 12 12:17:07 rubicon-iii indicator-appli[1587]: Application already exists, re-requesting properties.
Feb 12 12:21:08 rubicon-iii indicator-appli[1587]: message repeated 2 times: [ Application already exists, re-requesting properties.]
Feb 12 12:23:51 rubicon-iii NetworkManager[669]: <info>  [1486920231.3203]   address 10.0.0.17
Feb 12 12:23:51 rubicon-iii NetworkManager[669]: <info>  [1486920231.3204]   plen 24 (255.255.255.0)
Feb 12 12:23:51 rubicon-iii NetworkManager[669]: <info>  [1486920231.3204]   gateway 10.0.0.1
Feb 12 12:23:51 rubicon-iii NetworkManager[669]: <info>  [1486920231.3204]   server identifier 10.0.0.1
Feb 12 12:23:51 rubicon-iii NetworkManager[669]: <info>  [1486920231.3204]   lease time 86400
Feb 12 12:23:51 rubicon-iii NetworkManager[669]: <info>  [1486920231.3204]   nameserver '10.0.0.1'
Feb 12 12:23:51 rubicon-iii NetworkManager[669]: <info>  [1486920231.3479] dhcp4 (wlx9cefd5ffaae6): state changed bound -> bound
Feb 12 12:25:07 rubicon-iii indicator-appli[1587]: Application already exists, re-requesting properties.
Feb 12 13:11:07 rubicon-iii indicator-appli[1587]: message repeated 12 times: [ Application already exists, re-requesting properties.]
Feb 12 13:17:07 rubicon-iii indicator-appli[1587]: Application already exists, re-requesting properties.
Feb 12 14:05:07 rubicon-iii indicator-appli[1587]: message repeated 15 times: [ Application already exists, re-requesting properties.]
Feb 12 14:09:08 rubicon-iii indicator-appli[1587]: Application already exists, re-requesting properties.
Feb 12 14:15:08 rubicon-iii indicator-appli[1587]: message repeated 2 times: [ Application already exists, re-requesting properties.]
Feb 12 14:21:08 rubicon-iii indicator-appli[1587]: Application already exists, re-requesting properties.
Feb 12 14:35:08 rubicon-iii indicator-appli[1587]: message repeated 5 times: [ Application already exists, re-requesting properties.]
Feb 12 14:35:39 rubicon-iii NetworkManager[669]: <warn>  [1486928139.1050] sup-iface[0x55ffceef8d90,wlx9cefd5ffaae6]: connection disconnected (reason -4)
Feb 12 14:35:39 rubicon-iii NetworkManager[669]: <info>  [1486928139.1256] device (wlx9cefd5ffaae6): supplicant interface state: completed -> disconnected
Feb 12 14:35:39 rubicon-iii NetworkManager[669]: <info>  [1486928139.2101] device (wlx9cefd5ffaae6): supplicant interface state: disconnected -> scanning
Feb 12 14:35:40 rubicon-iii kernel: [49961.475054] wlx9cefd5ffaae6: authenticate with 04:a1:51:e7:09:0d
Feb 12 14:35:40 rubicon-iii kernel: [49961.507493] wlx9cefd5ffaae6: send auth to 04:a1:51:e7:09:0d (try 1/3)
Feb 12 14:35:40 rubicon-iii NetworkManager[669]: <info>  [1486928140.5879] device (wlx9cefd5ffaae6): supplicant interface state: scanning -> authenticating
Feb 12 14:35:40 rubicon-iii kernel: [49961.509233] wlx9cefd5ffaae6: authenticated
Feb 12 14:35:40 rubicon-iii NetworkManager[669]: <info>  [1486928140.5936] device (wlx9cefd5ffaae6): supplicant interface state: authenticating -> associating
Feb 12 14:35:40 rubicon-iii kernel: [49961.512097] wlx9cefd5ffaae6: associate with 04:a1:51:e7:09:0d (try 1/3)
Feb 12 14:35:40 rubicon-iii kernel: [49961.515479] wlx9cefd5ffaae6: RX AssocResp from 04:a1:51:e7:09:0d (capab=0x411 status=0 aid=8)
Feb 12 14:35:40 rubicon-iii kernel: [49961.523829] wlx9cefd5ffaae6: associated
Feb 12 14:35:40 rubicon-iii NetworkManager[669]: <info>  [1486928140.6086] device (wlx9cefd5ffaae6): supplicant interface state: associating -> 4-way handshake
Feb 12 14:35:40 rubicon-iii NetworkManager[669]: <info>  [1486928140.6260] device (wlx9cefd5ffaae6): supplicant interface state: 4-way handshake -> completed
Feb 12 14:37:08 rubicon-iii indicator-appli[1587]: Application already exists, re-requesting properties.
Feb 12 15:13:08 rubicon-iii indicator-appli[1587]: message repeated 13 times: [ Application already exists, re-requesting properties.]
Feb 12 15:19:08 rubicon-iii indicator-appli[1587]: Application already exists, re-requesting properties.
Feb 12 15:49:08 rubicon-iii indicator-appli[1587]: message repeated 7 times: [ Application already exists, re-requesting properties.]
Feb 12 15:54:55 rubicon-iii lightdm[807]: Error using VT_WAITACTIVE 7 on /dev/tty0: Interrupted system call
Feb 12 15:57:08 rubicon-iii indicator-appli[1587]: Application already exists, re-requesting properties.
Feb 12 15:59:08 rubicon-iii indicator-appli[1587]: Application already exists, re-requesting properties.
Feb 12 16:03:08 rubicon-iii indicator-appli[1587]: Application already exists, re-requesting properties.
Feb 12 16:13:18 rubicon-iii indicator-appli[1587]: message repeated 3 times: [ Application already exists, re-requesting properties.]
Feb 12 16:14:08 rubicon-iii indicator-sound[1586]: Sink input info callback : SINK INPUT INFO IS NULL or our user_data is not what we think it should be
Feb 12 16:14:13 rubicon-iii kernel: [55873.419561] sysrq: SysRq : This sysrq operation is disabled.
Feb 12 16:15:11 rubicon-iii indicator-appli[1587]: Application already exists, re-requesting properties.
Feb 12 16:15:12 rubicon-iii kernel: [55932.591820] sysrq: SysRq : This sysrq operation is disabled.
Feb 12 16:15:42 rubicon-iii kernel: [55963.115003] Chrome_ChildThr[25063]: segfault at 0 ip 0000555894365ae9 sp 00007f77d98fe370 error 6 in plugin-container[55589435d000+3e000]
Feb 12 16:21:22 rubicon-iii indicator-appli[1587]: Application already exists, re-requesting properties.
Feb 12 16:45:12 rubicon-iii indicator-appli[1587]: message repeated 2 times: [ Application already exists, re-requesting properties.]
Feb 12 16:51:56 rubicon-iii lightdm[807]: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
Feb 12 16:52:13 rubicon-iii at-spi-bus-laun[25977]: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
Feb 12 16:55:11 rubicon-iii indicator-appli[1587]: Application already exists, re-requesting properties.
Feb 12 17:13:11 rubicon-iii indicator-appli[1587]: message repeated 4 times: [ Application already exists, re-requesting properties.]
Feb 12 17:17:11 rubicon-iii indicator-appli[1587]: Application already exists, re-requesting properties.
Feb 12 17:25:11 rubicon-iii indicator-appli[1587]: message repeated 2 times: [ Application already exists, re-requesting properties.]
Feb 12 17:26:28 rubicon-iii lightdm[807]: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
Feb 12 17:26:28 rubicon-iii lightdm[807]: session_real_run: assertion '!session->priv->command_run' failed
Feb 12 17:26:29 rubicon-iii lightdm[807]: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
Feb 12 20:40:36 rubicon-iii gvfsd-network[31663]: Couldn't create directory monitor on smb://x-gnome-default-workgroup/. Error: Operation not supported by backend
Feb 12 20:54:42 rubicon-iii lightdm[807]: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
Feb 12 20:54:44 rubicon-iii at-spi-bus-laun[31880]: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
Feb 12 21:41:03 rubicon-iii lightdm[807]: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
Feb 12 21:41:04 rubicon-iii at-spi-bus-laun[863]: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
Feb 12 22:40:59 rubicon-iii kernel: [79079.798463] Chrome_ChildThr[31165]: segfault at 0 ip 000056486a1baae9 sp 00007fd6857fe370 error 6 in plugin-container[56486a1b2000+3e000]

```

---

