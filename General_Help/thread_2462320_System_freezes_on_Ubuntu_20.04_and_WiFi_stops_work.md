---
title: "System freezes on Ubuntu 20.04 and WiFi stops working"
date: 2021-05-18
forum: General Help
---

### Post by davy jones on 2021-05-18
[FONT=arial][COLOR=#242729]I suddenly started facing an odd issue a few days ago which seems to happen only sometimes. If I'm streaming video or even doing an audio call on a browser (Chrome or Firefox), my system sometimes freezes completely and the last half second or so of the audio plays on loop. I have to do a hard shut down by long pressing the power button. The last time this happened, I foung the syslog entries immediately preceeding this:
[/COLOR][/FONT]
```
May 12 15:15:22 Machine gnome-shell[12407]: [19904:20:0512/151522.107395:ERROR:webrtc_video_engine.cc(3350)] Absent receive stream; ignoring clearing encoded frame sink for ssrc 0
May 12 15:15:44 Machine gnome-shell[12407]: [19904:20:0512/151544.534097:ERROR:webrtc_video_engine.cc(3350)] Absent receive stream; ignoring clearing encoded frame sink for ssrc 0
May 12 15:16:08 Machine gnome-shell[2103]: ../clutter/clutter/clutter-actor.c:10558: The clutter_actor_set_allocation() function can only be called from within the implementation of the ClutterActor::allocate() virtual function.
May 12 15:16:29 Machine gnome-shell[2103]: ../clutter/clutter/clutter-actor.c:10558: The clutter_actor_set_allocation() function can only be called from within the implementation of the ClutterActor::allocate() virtual function.
May 12 15:17:01 Machine CRON[20644]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May 12 15:17:34 Machine gnome-shell[12407]: [19904:20:0512/151734.483733:ERROR:webrtc_video_engine.cc(3350)] Absent receive stream; ignoring clearing encoded frame sink for ssrc 0
May 12 15:19:21 Machine gnome-shell[12407]: [19904:20:0512/151921.527291:ERROR:webrtc_video_engine.cc(3350)] Absent receive stream; ignoring clearing encoded frame sink for ssrc 0
May 12 15:20:08 Machine gnome-shell[12407]: [19904:20:0512/152008.433602:ERROR:webrtc_video_engine.cc(3350)] Absent receive stream; ignoring clearing encoded frame sink for ssrc 0
May 12 15:20:55 Machine gnome-shell[2103]: ../clutter/clutter/clutter-actor.c:10558: The clutter_actor_set_allocation() function can only be called from within the implementation of the ClutterActor::allocate() virtual function.
May 12 15:24:32 Machine kernel: [12112.697501] perf: interrupt took too long (3145 > 3126), lowering kernel.perf_event_max_sample_rate to 63500
May 12 15:26:18 Machine gnome-shell[2103]: message repeated 3 times: [ ../clutter/clutter/clutter-actor.c:10558: The clutter_actor_set_allocation() function can only be called from within the implementation of the ClutterActor::allocate() virtual function.]
May 12 15:30:01 Machine CRON[20950]: (root) CMD ([ -x /etc/init.d/anacron ] && if [ ! -d /run/systemd/system ]; then /usr/sbin/invoke-rc.d anacron start >/dev/null; fi)
```
[COLOR=#242729][FONT=-apple-system]
[FONT=arial]Not sure if it's related, but my system is also freezing occasionally when I close the lid. And the problems I've had are quite similar to those in [this post]("https://askubuntu.com/questions/1193978/system-freezes-seemingly-randomly-ubuntu-18-04"). I also have a dedicated AMD Radeon GPU besides the integrated Intel one and I also once had a problem with my WiFi. I faced the huge system log problems before fixing that to ensure syslog files never get that huge. But the only problem is that since my system freezes completely I don't have a chance to see whether my RAM and Swap have been completely filled up or not. And the solution given isn't applicable to me.
[/FONT][/FONT][/COLOR][FONT=arial]
[COLOR=#242729]I can't find a common occurrence because it has sometimes happened even when nothing was being streamed. It has happened three times when Firefox was running and once when Chrome was. Also, I have KDE Plasma alongside GNOME and the problem clearly seems more frequent on KDE Plasma. And there is some connection with my WiFi perhaps because now it has happened twice that after doing a hard reboot after the freeze, the WiFi hasn't worked. I have a dual boot and booting into Windows and then back into Ubuntu fixes the WiFi.[/COLOR]

[COLOR=#242729]In case it's relevant, I recently faced [this]("https://askubuntu.com/questions/1333195/screen-flickering-on-ubuntu-20-04?noredirect=1#comment2274623_1333195") problem due to the bad 5.8.0-50 kernel upgrade, which I resolved by going back to the 5.8.0-43 kernel.
[/COLOR]
[COLOR=#242729]Any help would be appreciated.[/COLOR][/FONT]

---

### Post by davy jones on 2021-05-27
bump

---

### Post by tea for one on 2021-05-27
> **davy jones said:**
> I have to do a hard shut down by long pressing the power button. 

It would be better to enable REISUB rather than shut down with the power button.

Ubuntu does not ship with REISUB fully enabled.

Here is a method to enable the process by editing a file:-

```
sudo nano /etc/sysctl.d/10-magic-sysrq.conf
```
Then change the number in line 26 from 176 to 244 i.e. kernel.sysrq = 244

I found the solution at this site [https://digitalfortress.tech/debug/what-should-you-do-when-ubuntu-freezes/](https://digitalfortress.tech/debug/what-should-you-do-when-ubuntu-freezes/) and the information was in section 3.

By the way, the last letter in the process **B** reboots your system, sometimes you may want to power off completely by substituting the **B **for an** O**

---

### Post by davy jones on 2021-05-28
Had another system crash and WiFi stopped working in the middle of a session (this time the system rebooted on its own). Here are the logs:

```
May 28 13:13:04 Machine wpa_supplicant[1103]: wlp8s0: CTRL-EVENT-BEACON-LOSS 
May 28 13:13:05 Machine kernel: [  382.206213] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
May 28 13:13:05 Machine wpa_supplicant[1103]: wlp8s0: CTRL-EVENT-DISCONNECTED bssid=d8:32:14:ac:c3:51 reason=4 locally_generated=1
May 28 13:13:05 Machine NetworkManager[1080]: <warn>  [1622187785.4714] sup-iface[0x5643f88e0120,wlp8s0]: connection disconnected (reason -4)
May 28 13:13:05 Machine kernel: [  382.386690] ath: phy0: Chip reset failed
May 28 13:13:05 Machine kernel: [  382.386692] ath: phy0: Unable to reset channel, reset status -22
May 28 13:13:05 Machine wpa_supplicant[1103]: wlp8s0: CTRL-EVENT-REGDOM-CHANGE init=CORE type=WORLD
May 28 13:13:05 Machine NetworkManager[1080]: <info>  [1622187785.5013] device (wlp8s0): supplicant interface state: completed -> disconnected
May 28 13:13:05 Machine NetworkManager[1080]: <info>  [1622187785.5014] device (p2p-dev-wlp8s0): supplicant management interface state: completed -> disconnected
May 28 13:13:05 Machine kernel: [  382.499354] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
May 28 13:13:05 Machine NetworkManager[1080]: <info>  [1622187785.7671] device (wlp8s0): supplicant interface state: disconnected -> scanning
May 28 13:13:05 Machine NetworkManager[1080]: <info>  [1622187785.7671] device (p2p-dev-wlp8s0): supplicant management interface state: disconnected -> scanning
May 28 13:13:05 Machine kernel: [  382.682440] ath: phy0: Chip reset failed
May 28 13:13:05 Machine kernel: [  382.682444] ath: phy0: Unable to reset channel, reset status -22
May 28 13:13:05 Machine kernel: [  382.694287] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
May 28 13:13:05 Machine kernel: [  382.875265] ath: phy0: Chip reset failed
May 28 13:13:05 Machine kernel: [  382.875269] ath: phy0: Unable to reset channel, reset status -22
May 28 13:13:05 Machine kernel: [  382.886876] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
May 28 13:13:06 Machine kernel: [  383.067340] ath: phy0: Chip reset failed
May 28 13:13:06 Machine kernel: [  383.067343] ath: phy0: Unable to reset channel, reset status -22
May 28 13:13:06 Machine kernel: [  383.078891] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
May 28 13:13:06 Machine kernel: [  383.259781] ath: phy0: Chip reset failed
May 28 13:13:06 Machine kernel: [  383.259786] ath: phy0: Unable to reset channel, reset status -22
May 28 13:13:06 Machine kernel: [  383.271428] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
May 28 13:13:06 Machine kernel: [  383.452775] ath: phy0: Chip reset failed
May 28 13:13:06 Machine kernel: [  383.452779] ath: phy0: Unable to reset channel, reset status -22
May 28 13:13:06 Machine kernel: [  383.464488] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
May 28 13:13:06 Machine gnome-shell[2785]: [2778:2903:0528/131306.670523:ERROR:connection_factory_impl.cc(429)] Failed to connect to MCS endpoint with error -106
May 28 13:13:06 Machine kernel: [  383.645343] ath: phy0: Chip reset failed
May 28 13:13:06 Machine kernel: [  383.645349] ath: phy0: Unable to reset channel, reset status -22
May 28 13:13:06 Machine kernel: [  383.656982] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
May 28 13:13:06 Machine kernel: [  383.837653] ath: phy0: Chip reset failed
May 28 13:13:06 Machine kernel: [  383.837655] ath: phy0: Unable to reset channel, reset status -22
May 28 13:13:06 Machine kernel: [  383.849256] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
May 28 13:13:07 Machine kernel: [  384.029730] ath: phy0: Chip reset failed
May 28 13:13:07 Machine kernel: [  384.029732] ath: phy0: Unable to reset channel, reset status -22
May 28 13:13:07 Machine kernel: [  384.041264] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
May 28 13:13:07 Machine kernel: [  384.221517] ath: phy0: Chip reset failed
May 28 13:13:07 Machine kernel: [  384.221520] ath: phy0: Unable to reset channel, reset status -22
May 28 13:13:07 Machine kernel: [  384.233066] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
May 28 13:13:07 Machine kernel: [  384.413455] ath: phy0: Chip reset failed
May 28 13:13:07 Machine kernel: [  384.413457] ath: phy0: Unable to reset channel, reset status -22
May 28 13:13:07 Machine kernel: [  384.425027] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
May 28 13:13:07 Machine kernel: [  384.606230] ath: phy0: Chip reset failed
May 28 13:13:07 Machine kernel: [  384.606234] ath: phy0: Unable to reset channel, reset status -22
May 28 13:13:07 Machine kernel: [  384.617913] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
May 28 13:13:07 Machine kernel: [  384.827768] ath: phy0: Chip reset failed
May 28 13:13:07 Machine kernel: [  384.827772] ath: phy0: Unable to reset channel, reset status -22
May 28 13:13:07 Machine kernel: [  384.839466] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
May 28 13:13:08 Machine kernel: [  385.021760] ath: phy0: Chip reset failed
May 28 13:13:08 Machine kernel: [  385.021764] ath: phy0: Unable to reset channel, reset status -22
May 28 13:13:08 Machine kernel: [  385.033343] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
May 28 13:13:08 Machine kernel: [  385.214743] ath: phy0: Chip reset failed
May 28 13:13:08 Machine kernel: [  385.214748] ath: phy0: Unable to reset channel, reset status -22
May 28 13:13:08 Machine kernel: [  385.226332] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
May 28 13:13:08 Machine kernel: [  385.408193] ath: phy0: Chip reset failed
May 28 13:13:08 Machine kernel: [  385.408198] ath: phy0: Unable to reset channel, reset status -22
May 28 13:13:08 Machine kernel: [  385.419929] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
May 28 13:13:08 Machine kernel: [  385.602564] ath: phy0: Chip reset failed
May 28 13:13:08 Machine kernel: [  385.602568] ath: phy0: Unable to reset channel, reset status -22
May 28 13:13:08 Machine kernel: [  385.614334] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
May 28 13:13:08 Machine kernel: [  385.796999] ath: phy0: Chip reset failed
May 28 13:13:08 Machine kernel: [  385.797003] ath: phy0: Unable to reset channel, reset status -22
May 28 13:13:08 Machine kernel: [  385.808712] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
May 28 13:13:09 Machine kernel: [  385.989881] ath: phy0: Chip reset failed
May 28 13:13:09 Machine kernel: [  385.989885] ath: phy0: Unable to reset channel, reset status -22
May 28 13:13:09 Machine kernel: [  386.001417] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
May 28 13:13:09 Machine kernel: [  386.181595] ath: phy0: Chip reset failed
May 28 13:13:09 Machine kernel: [  386.181598] ath: phy0: Unable to reset channel, reset status -22
May 28 13:13:09 Machine kernel: [  386.193159] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
May 28 13:13:09 Machine kernel: [  386.373430] ath: phy0: Chip reset failed
May 28 13:13:09 Machine kernel: [  386.373433] ath: phy0: Unable to reset channel, reset status -22
May 28 13:13:09 Machine kernel: [  386.385040] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
May 28 13:13:09 Machine kernel: [  386.566223] ath: phy0: Chip reset failed
May 28 13:13:09 Machine kernel: [  386.566227] ath: phy0: Unable to reset channel, reset status -22
May 28 13:13:09 Machine kernel: [  386.577874] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
May 28 13:13:09 Machine kernel: [  386.759163] ath: phy0: Chip reset failed
May 28 13:13:09 Machine kernel: [  386.759167] ath: phy0: Unable to reset channel, reset status -22
May 28 13:13:09 Machine kernel: [  386.770887] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
May 28 13:13:10 Machine kernel: [  386.953264] ath: phy0: Chip reset failed
May 28 13:13:10 Machine kernel: [  386.953268] ath: phy0: Unable to reset channel, reset status -22
May 28 13:13:10 Machine kernel: [  386.965018] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
May 28 13:13:10 Machine kernel: [  387.146871] ath: phy0: Chip reset failed
May 28 13:13:10 Machine kernel: [  387.146875] ath: phy0: Unable to reset channel, reset status -22
May 28 13:13:10 Machine kernel: [  387.158537] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
May 28 13:13:10 Machine kernel: [  387.366195] ath: phy0: Chip reset failed
May 28 13:13:10 Machine kernel: [  387.366199] ath: phy0: Unable to reset channel, reset status -22
May 28 13:13:10 Machine kernel: [  387.377851] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
May 28 13:13:10 Machine kernel: [  387.560208] ath: phy0: Chip reset failed
May 28 13:13:10 Machine kernel: [  387.560213] ath: phy0: Unable to reset channel, reset status -22
May 28 13:13:10 Machine kernel: [  387.571827] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
May 28 13:13:10 Machine kernel: [  387.753678] ath: phy0: Chip reset failed
May 28 13:13:10 Machine kernel: [  387.753682] ath: phy0: Unable to reset channel, reset status -22
May 28 13:13:10 Machine kernel: [  387.765389] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
May 28 13:13:11 Machine kernel: [  387.947248] ath: phy0: Chip reset failed
May 28 13:13:11 Machine kernel: [  387.947252] ath: phy0: Unable to reset channel, reset status -22
May 28 13:13:11 Machine kernel: [  387.958835] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
May 28 13:13:11 Machine kernel: [  388.139488] ath: phy0: Chip reset failed
May 28 13:13:11 Machine kernel: [  388.139492] ath: phy0: Unable to reset channel, reset status -22
May 28 13:13:11 Machine kernel: [  388.151087] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
May 28 13:13:11 Machine kernel: [  388.331842] ath: phy0: Chip reset failed
May 28 13:13:11 Machine kernel: [  388.331847] ath: phy0: Unable to reset channel, reset status -22
May 28 13:13:11 Machine kernel: [  388.343403] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
May 28 13:13:11 Machine kernel: [  388.524071] ath: phy0: Chip reset failed
May 28 13:13:11 Machine kernel: [  388.524076] ath: phy0: Unable to reset channel, reset status -22
May 28 13:13:11 Machine kernel: [  388.535694] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
May 28 13:13:11 Machine kernel: [  388.716655] ath: phy0: Chip reset failed
May 28 13:13:11 Machine kernel: [  388.716660] ath: phy0: Unable to reset channel, reset status -22
May 28 13:13:11 Machine kernel: [  388.728373] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
May 28 13:13:11 Machine kernel: [  388.909853] ath: phy0: Chip reset failed
May 28 13:13:11 Machine kernel: [  388.909857] ath: phy0: Unable to reset channel, reset status -22
May 28 13:13:12 Machine kernel: [  388.921631] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
May 28 13:13:12 Machine kernel: [  389.103311] ath: phy0: Chip reset failed
May 28 13:13:12 Machine kernel: [  389.103315] ath: phy0: Unable to reset channel, reset status -22
May 28 13:13:12 Machine kernel: [  389.114925] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
May 28 13:13:12 Machine kernel: [  389.296130] ath: phy0: Chip reset failed
May 28 13:13:12 Machine kernel: [  389.296134] ath: phy0: Unable to reset channel, reset status -22
May 28 13:13:12 Machine kernel: [  389.307803] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
May 28 13:13:12 Machine kernel: [  389.488445] ath: phy0: Chip reset failed
May 28 13:13:12 Machine kernel: [  389.488449] ath: phy0: Unable to reset channel, reset status -22
May 28 13:13:12 Machine kernel: [  389.500061] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
May 28 13:13:12 Machine kernel: [  389.681076] ath: phy0: Chip reset failed
May 28 13:13:12 Machine kernel: [  389.681080] ath: phy0: Unable to reset channel, reset status -22
May 28 13:13:12 Machine kernel: [  389.692809] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
May 28 13:13:12 Machine kernel: [  389.874830] ath: phy0: Chip reset failed
May 28 13:13:12 Machine kernel: [  389.874844] ath: phy0: Unable to reset channel, reset status -22
May 28 13:13:12 Machine kernel: [  389.886718] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
May 28 13:13:13 Machine kernel: [  390.068907] ath: phy0: Chip reset failed
May 28 13:13:13 Machine kernel: [  390.068912] ath: phy0: Unable to reset channel, reset status -22
May 28 13:13:13 Machine kernel: [  390.080601] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
May 28 13:13:13 Machine kernel: [  390.262758] ath: phy0: Chip reset failed
May 28 13:13:13 Machine kernel: [  390.262762] ath: phy0: Unable to reset channel, reset status -22
May 28 13:13:13 Machine kernel: [  390.274446] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff

```

And had multiple crashes one after the other within a short period of time. I suspect system overheating has something to do with it because the last one happened just as I logged in (the desktop screen hadn't even loaded). I let the laptop be off for 20 minutes and then started it and it hasn't crashed so far. Here is another log entry before the crash in case it helps pinpoint the source.

```
May 28 13:20:17 Machine gnome-shell[3664]: libva error: /usr/lib/x86_64-linux-gnu/dri/iHD_drv_video.so init failed
May 28 13:20:18 Machine gnome-shell[3664]: [3704:3704:0528/132018.336942:ERROR:sandbox_linux.cc(374)] InitializeSandbox() called with multiple threads in process gpu-process.

```

And this one from a few minutes after that:

```
May 28 13:27:04 Machine systemd[1]: Starting Manage, Install and Generate Color Profiles...
May 28 13:27:04 Machine gnome-session-binary[1482]: Entering running state
May 28 13:27:04 Machine gsd-media-keys[1852]: Failed to grab accelerator for keybinding settings:playback-repeat
May 28 13:27:04 Machine gsd-media-keys[1852]: Failed to grab accelerator for keybinding settings:rfkill
May 28 13:27:04 Machine gsd-media-keys[1852]: Failed to grab accelerator for keybinding settings:hibernate
May 28 13:27:04 Machine gsd-media-keys[1852]: Failed to grab accelerator for keybinding settings:playback-random
May 28 13:27:04 Machine dbus-daemon[1100]: [system] Successfully activated service 'org.freedesktop.ColorManager'
May 28 13:27:04 Machine systemd[1]: Started Manage, Install and Generate Color Profiles.
May 28 13:27:04 Machine xbrlapi.desktop[2027]: openConnection: connect: No such file or directory
May 28 13:27:04 Machine xbrlapi.desktop[2027]: cannot connect to braille devices daemon brltty at :0
May 28 13:27:05 Machine org.gnome.Shell.desktop[2034]: The XKEYBOARD keymap compiler (xkbcomp) reports:
May 28 13:27:05 Machine org.gnome.Shell.desktop[2034]: > Warning:          Unsupported maximum keycode 569, clipping.
May 28 13:27:05 Machine org.gnome.Shell.desktop[2034]: >                   X11 cannot support keycodes above 255.
May 28 13:27:05 Machine org.gnome.Shell.desktop[2034]: > Internal error:   Could not resolve keysym Invalid
May 28 13:27:05 Machine org.gnome.Shell.desktop[2034]: Errors from xkbcomp are not fatal to the X server
May 28 13:27:07 Machine gnome-shell[1542]: Warning: Failed to start gsd-xsettings
May 28 13:27:08 Machine org.gnome.Shell.desktop[1542]: libinput error: client bug: timer event5 keyboard: scheduled expiry is in the past (-74ms), your system is too slow
May 28 13:27:08 Machine gnome-shell[1542]: JS WARNING: [resource:///org/gnome/shell/ui/layout.js 24]: reference to undefined property "MetaWindowXwayland"

```

---

### Post by veramocor on 2021-05-29
Having a very similar problem, described here: [https://ubuntuforums.org/showthread.php?t=2462857](https://ubuntuforums.org/showthread.php?t=2462857)
One thing I didn't mention in my thread is that I also experience the same audio loop as you when the crash happens. I hope there is a solution for this found soon.

---

### Post by davy jones on 2021-05-31
[COLOR=#242729][FONT=-apple-system]UPDATE: Despite reinstalling Ubuntu 20.04 (with a kernel upgrade to 5.8.0-53), this issue persists. Reinstalled yesterday, had the first system freeze today after I opened the laptop lid and opened a couple of tabs on Chrome (the browser was already open). I don't know what the hell is going on and why no can seem to help with this.[/FONT][/COLOR]

---

### Post by dragonfly41 on 2021-05-31
I can only jump in with basic search to test clues (text snippets) taken from your logs (which you can do also).
Found this which suggests as a fix/workaround downgrading gnome-shell in 20.04.
[https://github.com/home-sweet-gnome/dash-to-panel/issues/976](https://github.com/home-sweet-gnome/dash-to-panel/issues/976)
But this is grasping at straws.

---

### Post by davy jones on 2021-05-31
I haven't been able to find any helpful results by searching for text snippets from the logs. But I'm not sure this could be a gnome-shell issue because it also happens with KDE Plasma. Is it possible that the problem occurs because I have two desktop environments installed (I use GDM3 even though I have Plasma alongside Gnome)?

---

### Post by davy jones on 2021-06-02
A little while ago I'd shut the laptop lid (my system is not set to suspend if that happens). I opened it to find that it was restarting on its own. I found the following log entries from around that time:

```
Jun  2 18:15:49 Machine thermald[849]: sensor id 4 : No temp sysfs for reading raw tempJun  2 18:23:11 Machine kernel: [   51.336014] Freezing user space processes ... (elapsed 0.110 seconds) done.
Jun  2 18:23:11 Machine kernel: [   51.446664] OOM killer disabled.
Jun  2 18:23:11 Machine kernel: [   51.446667] Freezing remaining freezable tasks ... (elapsed 0.001 seconds) done.
Jun  2 18:23:11 Machine kernel: [   51.448174] printk: Suspending console(s) (use no_console_suspend to debug)
Jun  2 18:23:11 Machine kernel: [   51.599021] sd 0:0:0:0: [sda] Synchronizing SCSI cache
Jun  2 18:23:11 Machine kernel: [   51.685897] sd 0:0:0:0: [sda] Stopping disk
Jun  2 18:23:11 Machine kernel: [   51.930059] [drm] enabling PCIE gen 2 link speeds, disable with radeon.pcie_gen2=0
Jun  2 18:23:11 Machine kernel: [   51.959324] [drm] PCIE GART of 2048M enabled (table at 0x00000000001D6000).

```

Another bunch of entries are these:

```
Jun  2 18:23:13 Machine thermald[849]: I/O warning : failed to load external entity "/etc/thermald/thermal-conf.xml"
Jun  2 18:23:13 Machine thermald[849]: error: could not parse file /etc/thermald/thermal-conf.xml
Jun  2 18:23:13 Machine thermald[849]: I/O warning : failed to load external entity "/etc/thermald/thermal-conf.xml"
Jun  2 18:23:13 Machine thermald[849]: error: could not parse file /etc/thermald/thermal-conf.xml
Jun  2 18:23:13 Machine thermald[849]: I/O warning : failed to load external entity "/etc/thermald/thermal-conf.xml"
Jun  2 18:23:13 Machine thermald[849]: error: could not parse file /etc/thermald/thermal-conf.xml

```

I've looked up this thermald error but I haven't been able to find any clearcut solutions to it that I can implement.

---

### Post by davy jones on 2021-06-03
Another freeze while running Zoom where a small bit of audio kept playing on loop. Here is a log entry from around the time of the freeze:

```
Jun  3 11:07:59 Machine gnome-shell[2124]: Window manager warning: Invalid WM_TRANSIENT_FOR window 0x2a00010 specified for 0x2a0015b.
```

Is there any chance at all that having both Gnome and KDE Plasma is causing this? Especially since I've set gdm3 as the display manager rather than sddm?

---

### Post by davy jones on 2021-07-04
There is STILL no solution to this and the issue hasn't gone away. I have noticed a few times that when I have around 5-6 Chrome tabs (which I used to have earlier as well) with possibly heavier websites, my memory is over 90% full and the system becomes jittery. But still can't be sure if this is the root cause (why doesn't syslog mention anything about this?). I also don't understand how my Windows install is fine with the 4 GB RAM I have but Ubuntu isn't. Here is another log entry after the most recent crash:

```
Jul  4 14:25:48 Machine google-chrome.desktop[26653]: libva error: /usr/lib/x86_64-linux-gnu/dri/iHD_drv_video.so init failed
Jul  4 14:25:48 Machine google-chrome.desktop[26653]: [26685:26685:0704/142548.700456:ERROR:sandbox_linux.cc(374)] InitializeSandbox() called with multiple threads in process gpu-process.
Jul  4 14:25:53 Machine google-chrome.desktop[26653]: [26646:26666:0704/142553.812893:ERROR:gcm_store_impl.cc(652)] LevelDB remove failed: NotFound:
Jul  4 14:25:53 Machine google-chrome.desktop[26653]: [26646:26669:0704/142553.813045:ERROR:mcs_client.cc(526)] GCM Update failed!
Jul  4 14:27:18 Machine PackageKit: daemon quit
Jul  4 14:27:18 Machine systemd[1]: packagekit.service: Succeeded.
Jul  4 14:27:56 Machine google-chrome.desktop[26653]: [26687:26690:0704/142756.708204:ERROR:ssl_client_socket_impl.cc(980)] handshake failed; returned -1, SSL error code 1, net_error -100
Jul  4 14:27:56 Machine google-chrome.desktop[26653]: [26687:26690:0704/142756.796603:ERROR:ssl_client_socket_impl.cc(980)] handshake failed; returned -1, SSL error code 1, net_error -100
Jul  4 14:27:56 Machine google-chrome.desktop[26653]: [26687:26690:0704/142756.852918:ERROR:ssl_client_socket_impl.cc(980)] handshake failed; returned -1, SSL error code 1, net_error -100
Jul  4 14:28:03 Machine google-chrome.desktop[26653]: [26687:26690:0704/142803.997212:ERROR:ssl_client_socket_impl.cc(980)] handshake failed; returned -1, SSL error code 1, net_error -100
Jul  4 14:28:04 Machine google-chrome.desktop[26653]: [26687:26690:0704/142804.080933:ERROR:ssl_client_socket_impl.cc(980)] handshake failed; returned -1, SSL error code 1, net_error -100
Jul  4 14:28:04 Machine google-chrome.desktop[26653]: [26687:26690:0704/142804.141079:ERROR:ssl_client_socket_impl.cc(980)] handshake failed; returned -1, SSL error code 1, net_error -100
Jul  4 14:28:14 Machine google-chrome.desktop[26653]: [26687:26690:0704/142814.603884:ERROR:ssl_client_socket_impl.cc(980)] handshake failed; returned -1, SSL error code 1, net_error -100
Jul  4 14:28:14 Machine google-chrome.desktop[26653]: [26687:26690:0704/142814.668010:ERROR:ssl_client_socket_impl.cc(980)] handshake failed; returned -1, SSL error code 1, net_error -100
Jul  4 14:28:14 Machine google-chrome.desktop[26653]: [26687:26690:0704/142814.780805:ERROR:ssl_client_socket_impl.cc(980)] handshake failed; returned -1, SSL error code 1, net_error -100
Jul  4 14:28:14 Machine google-chrome.desktop[26653]: [26687:26690:0704/142814.860787:ERROR:ssl_client_socket_impl.cc(980)] handshake failed; returned -1, SSL error code 1, net_error -100
Jul  4 14:28:17 Machine google-chrome.desktop[26653]: (transmission-gtk:27230): GLib-CRITICAL **: 14:28:17.210: g_file_test: assertion 'filename != NULL' failed
Jul  4 14:28:17 Machine dbus-daemon[852]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service' requested by ':1.212' (uid=1000 pid=27230 comm="transmission-gtk magnet:?xt=urn:btih:1EF2D24F1ECFF" label="unconfined")
Jul  4 14:28:17 Machine systemd[1]: Starting Hostname Service...
Jul  4 14:28:18 Machine dbus-daemon[852]: [system] Successfully activated service 'org.freedesktop.hostname1'
Jul  4 14:28:18 Machine systemd[1]: Started Hostname Service.
Jul  4 14:28:21 Machine google-chrome.desktop[26653]: [26687:26690:0704/142821.884753:ERROR:ssl_client_socket_impl.cc(980)] handshake failed; returned -1, SSL error code 1, net_error -100
Jul  4 14:28:21 Machine google-chrome.desktop[26653]: [26687:26690:0704/142821.964205:ERROR:ssl_client_socket_impl.cc(980)] handshake failed; returned -1, SSL error code 1, net_error -100
Jul  4 14:28:22 Machine google-chrome.desktop[26653]: [26687:26690:0704/142822.068246:ERROR:ssl_client_socket_impl.cc(980)] handshake failed; returned -1, SSL error code 1, net_error -100
Jul  4 14:28:22 Machine google-chrome.desktop[26653]: [26687:26690:0704/142822.140346:ERROR:ssl_client_socket_impl.cc(980)] handshake failed; returned -1, SSL error code 1, net_error -100
Jul  4 14:28:32 Machine google-chrome.desktop[26653]: [26685:26685:0704/142832.102447:ERROR:gl_utils.cc(314)] [.RendererMainThread-0x2c11bcb84700] GL_INVALID_FRAMEBUFFER_OPERATION: Draw framebuffer is incomplete
Jul  4 14:28:48 Machine systemd[1]: systemd-hostnamed.service: Succeeded.
```

---

### Post by zircon_34 on 2021-07-04
I may have missed it but could you past what amd gpu model you have and which drivers you installed (proprietary vs. nouveau)?

inxi -b

4Gb is low ram, make sure to have enough swap and perhaps use a less power hungry DE. Like gnome or kde use already 750Mb-1Gb just by running your distro. Use htop to check the ram usage.

Having both gnome alongside kde is not a good idea, it may work but could also result in conflicting behavior. I also had such freeze a couple of months again with gnome/kde install but on arch based distro. Apparently upgrade to a newer kernel fixed the gnome freeze but note I use nvidia which id a different beast (and pain).

What I would do is 1) check and post your video driver, 2) if you do new install only choose one DE, and secondly I would try Ubuntu 21.04 with newer kernel or older ubuntu to check if it could be kernel related. You could also install additional kernels via cli but not sure how easy it is on ubuntu. 3) if none of these things work, could be also hardware related? I would do a hardware test via bios just to make sure.

---

### Post by davy jones on 2021-07-05
Thanks for the reply.

Here is the output for inxi -b

```
System:
  Host: Machine Kernel: 5.8.0-59-generic x86_64 bits: 64 
  Desktop: Gnome 3.36.9 Distro: Ubuntu 20.04.2 LTS (Focal Fossa) 
Machine:
  Type: Portable System: Dell product: Inspiron 3521 v: A05 
  serial: <superuser/root required> 
  Mobo: Dell model: 06X37M v: A00 serial: <superuser/root required> 
  UEFI: Dell v: A05 date: 01/03/2013 
Battery:
  ID-1: BAT1 charge: 12.9 Wh condition: 12.9/66.6 Wh (19%) 
CPU:
  Dual Core: Intel Core i5-3337U type: MT MCP speed: 943 MHz 
  min/max: 800/2700 MHz 
Graphics:
  Device-1: Intel 3rd Gen Core processor Graphics driver: i915 v: kernel 
  Device-2: AMD Mars [Radeon HD 8730M] driver: radeon v: kernel 
  Display: x11 server: X.Org 1.20.9 driver: radeon tty: N/A 
  OpenGL: renderer: Mesa DRI Intel HD Graphics 4000 (IVB GT2) 
  v: 4.2 Mesa 20.2.6 
Network:
  Device-1: Realtek RTL810xE PCI Express Fast Ethernet driver: r8169 
  Device-2: Qualcomm Atheros AR9485 Wireless Network Adapter driver: ath9k 
  Device-3: Qualcomm Atheros type: USB driver: btusb 
Drives:
  Local Storage: total: 931.51 GiB used: 503.95 GiB (54.1%) 
Info:
  Processes: 271 Uptime: 4m Memory: 3.71 GiB used: 1.64 GiB (44.0%) 
  Shell: bash inxi: 3.0.38 

```

I know 4 GB RAM isn't great, but I have 5 GB Swap. Besides, I'm kind of confounded that Windows works fine with 4 GB RAM but Ubuntu doesn't. I just uninstalled KDE Plasma just to be sure (weirdly after doing this, the system has crashed twice within an hour; not sure if it's in any way related).

I've done a hardware test on BIOS and everything turned out fine. This issue only seems to occur in Ubuntu. I've considered a kernel problem as well, but this issue has now occurred across 5 different kernels. After it kept occurring despite kernel upgrades, I gave up the idea that it was kernel related and stopped keeping track of kernel upgrades. But this issue didn't occur for a couple of weeks. The first time it happened after this gap was 4 days after a kernel upgrade from 5.8.0-55 to 5.8.0-59.

And this WiFi issue also occurred again after a long time and led to another system freeze. These are the logs for that:

```

Jul  5 12:27:49 Machine wpa_supplicant[899]: wlp8s0: CTRL-EVENT-BEACON-LOSS 
Jul  5 12:27:54 Machine kernel: [ 5852.894804] sched: RT throttling activated
Jul  5 12:27:54 Machine kernel: [ 5852.908860] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Jul  5 12:27:55 Machine kernel: [ 5853.985438] ath: phy0: Chip reset failed
Jul  5 12:27:55 Machine kernel: [ 5853.985444] ath: phy0: Unable to reset channel, reset status -22
Jul  5 12:27:55 Machine wpa_supplicant[899]: wlp8s0: CTRL-EVENT-DISCONNECTED bssid=d8:32:14:ac:c3:51 reason=4 locally_generated=1
Jul  5 12:27:55 Machine google-chrome.desktop[4361]: [4353:4387:0705/122755.555343:ERROR:connection_factory_impl.cc(429)] Failed to connect to MCS endpoint with error -106
Jul  5 12:27:55 Machine NetworkManager[858]: <warn>  [1625468275.5745] sup-iface[0x557ad5cab920,wlp8s0]: connection disconnected (reason -4)
Jul  5 12:27:55 Machine wpa_supplicant[899]: wlp8s0: CTRL-EVENT-REGDOM-CHANGE init=CORE type=WORLD
Jul  5 12:27:55 Machine NetworkManager[858]: <info>  [1625468275.5961] device (wlp8s0): supplicant interface state: completed -> disconnected
Jul  5 12:27:55 Machine NetworkManager[858]: <info>  [1625468275.5962] device (p2p-dev-wlp8s0): supplicant management interface state: completed -> disconnected
Jul  5 12:27:55 Machine NetworkManager[858]: <info>  [1625468275.6651] device (wlp8s0): supplicant interface state: disconnected -> scanning
Jul  5 12:27:55 Machine NetworkManager[858]: <info>  [1625468275.6651] device (p2p-dev-wlp8s0): supplicant management interface state: disconnected -> scanning
Jul  5 12:27:55 Machine kernel: [ 5854.207917] ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
Jul  5 12:27:55 Machine kernel: [ 5854.219432] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Jul  5 12:27:55 Machine kernel: [ 5854.229898] ath: phy0: Failed to wakeup in 500us
Jul  5 12:27:55 Machine kernel: [ 5854.243859] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Jul  5 12:27:55 Machine kernel: [ 5854.424896] ath: phy0: Chip reset failed
Jul  5 12:27:55 Machine kernel: [ 5854.424900] ath: phy0: Unable to reset channel, reset status -22
Jul  5 12:27:56 Machine kernel: [ 5854.436472] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Jul  5 12:27:57 Machine kernel: [ 5855.772249] ath: phy0: Chip reset failed
Jul  5 12:27:57 Machine kernel: [ 5855.772254] ath: phy0: Unable to reset channel, reset status -22
Jul  5 12:27:57 Machine kernel: [ 5855.784168] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Jul  5 12:27:57 Machine kernel: [ 5856.238163] ath: phy0: Chip reset failed
Jul  5 12:27:57 Machine kernel: [ 5856.238169] ath: phy0: Unable to reset channel, reset status -22
Jul  5 12:27:57 Machine kernel: [ 5856.250385] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Jul  5 12:27:58 Machine kernel: [ 5856.523913] ath: phy0: Chip reset failed
Jul  5 12:27:58 Machine kernel: [ 5856.523919] ath: phy0: Unable to reset channel, reset status -22
Jul  5 12:27:58 Machine kernel: [ 5856.535860] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Jul  5 12:27:58 Machine kernel: [ 5856.722674] ath: phy0: Chip reset failed
Jul  5 12:27:58 Machine kernel: [ 5856.722682] ath: phy0: Unable to reset channel, reset status -22
Jul  5 12:27:58 Machine kernel: [ 5856.734700] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Jul  5 12:27:58 Machine kernel: [ 5856.921212] ath: phy0: Chip reset failed
Jul  5 12:27:58 Machine kernel: [ 5856.921221] ath: phy0: Unable to reset channel, reset status -22
Jul  5 12:27:58 Machine kernel: [ 5856.933220] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Jul  5 12:27:58 Machine kernel: [ 5857.119414] ath: phy0: Chip reset failed
Jul  5 12:27:58 Machine kernel: [ 5857.119423] ath: phy0: Unable to reset channel, reset status -22
Jul  5 12:27:58 Machine kernel: [ 5857.131124] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Jul  5 12:27:58 Machine kernel: [ 5857.312562] ath: phy0: Chip reset failed
Jul  5 12:27:58 Machine kernel: [ 5857.312567] ath: phy0: Unable to reset channel, reset status -22
Jul  5 12:27:58 Machine kernel: [ 5857.324534] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Jul  5 12:27:59 Machine kernel: [ 5857.511527] ath: phy0: Chip reset failed
Jul  5 12:27:59 Machine kernel: [ 5857.511536] ath: phy0: Unable to reset channel, reset status -22
Jul  5 12:27:59 Machine kernel: [ 5857.523244] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Jul  5 12:27:59 Machine kernel: [ 5857.704390] ath: phy0: Chip reset failed
Jul  5 12:27:59 Machine kernel: [ 5857.704394] ath: phy0: Unable to reset channel, reset status -22
Jul  5 12:27:59 Machine kernel: [ 5857.716242] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Jul  5 12:27:59 Machine kernel: [ 5857.902975] ath: phy0: Chip reset failed
Jul  5 12:27:59 Machine kernel: [ 5857.902983] ath: phy0: Unable to reset channel, reset status -22
Jul  5 12:27:59 Machine kernel: [ 5857.914647] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Jul  5 12:27:59 Machine kernel: [ 5858.095902] ath: phy0: Chip reset failed
Jul  5 12:27:59 Machine kernel: [ 5858.095906] ath: phy0: Unable to reset channel, reset status -22
Jul  5 12:27:59 Machine kernel: [ 5858.107924] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Jul  5 12:27:59 Machine kernel: [ 5858.295507] ath: phy0: Chip reset failed
Jul  5 12:27:59 Machine kernel: [ 5858.295517] ath: phy0: Unable to reset channel, reset status -22
Jul  5 12:27:59 Machine kernel: [ 5858.307344] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Jul  5 12:28:00 Machine kernel: [ 5858.491352] ath: phy0: Chip reset failed
Jul  5 12:28:00 Machine kernel: [ 5858.491359] ath: phy0: Unable to reset channel, reset status -22
Jul  5 12:28:00 Machine kernel: [ 5858.503268] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Jul  5 12:28:00 Machine kernel: [ 5858.689389] ath: phy0: Chip reset failed
Jul  5 12:28:00 Machine kernel: [ 5858.689397] ath: phy0: Unable to reset channel, reset status -22
Jul  5 12:28:00 Machine kernel: [ 5858.701225] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Jul  5 12:28:00 Machine kernel: [ 5858.884333] ath: phy0: Chip reset failed
Jul  5 12:28:00 Machine kernel: [ 5858.884340] ath: phy0: Unable to reset channel, reset status -22
Jul  5 12:28:00 Machine kernel: [ 5858.896044] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Jul  5 12:28:00 Machine kernel: [ 5859.080293] ath: phy0: Chip reset failed
Jul  5 12:28:00 Machine kernel: [ 5859.080300] ath: phy0: Unable to reset channel, reset status -22
Jul  5 12:28:00 Machine kernel: [ 5859.091990] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Jul  5 12:28:00 Machine kernel: [ 5859.273309] ath: phy0: Chip reset failed
Jul  5 12:28:00 Machine kernel: [ 5859.273319] ath: phy0: Unable to reset channel, reset status -22
Jul  5 12:28:00 Machine kernel: [ 5859.299640] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Jul  5 12:28:01 Machine kernel: [ 5859.481404] ath: phy0: Chip reset failed
Jul  5 12:28:01 Machine kernel: [ 5859.481410] ath: phy0: Unable to reset channel, reset status -22
Jul  5 12:28:01 Machine kernel: [ 5859.540426] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Jul  5 12:28:01 Machine kernel: [ 5859.722392] ath: phy0: Chip reset failed
Jul  5 12:28:01 Machine kernel: [ 5859.722398] ath: phy0: Unable to reset channel, reset status -22
Jul  5 12:28:01 Machine kernel: [ 5859.734261] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Jul  5 12:28:01 Machine kernel: [ 5859.916391] ath: phy0: Chip reset failed
Jul  5 12:28:01 Machine kernel: [ 5859.916397] ath: phy0: Unable to reset channel, reset status -22
Jul  5 12:28:01 Machine kernel: [ 5859.928291] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Jul  5 12:28:01 Machine kernel: [ 5860.110144] ath: phy0: Chip reset failed
Jul  5 12:28:01 Machine kernel: [ 5860.110150] ath: phy0: Unable to reset channel, reset status -22
Jul  5 12:28:01 Machine kernel: [ 5860.188309] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Jul  5 12:28:01 Machine kernel: [ 5860.369287] ath: phy0: Chip reset failed
Jul  5 12:28:01 Machine kernel: [ 5860.369291] ath: phy0: Unable to reset channel, reset status -22
Jul  5 12:28:01 Machine kernel: [ 5860.381014] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Jul  5 12:28:02 Machine kernel: [ 5860.562843] ath: phy0: Chip reset failed
Jul  5 12:28:02 Machine kernel: [ 5860.562850] ath: phy0: Unable to reset channel, reset status -22
Jul  5 12:28:02 Machine kernel: [ 5860.580714] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Jul  5 12:28:02 Machine kernel: [ 5860.761419] ath: phy0: Chip reset failed
Jul  5 12:28:02 Machine kernel: [ 5860.761425] ath: phy0: Unable to reset channel, reset status -22
Jul  5 12:28:02 Machine kernel: [ 5860.782236] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Jul  5 12:28:02 Machine kernel: [ 5860.964493] ath: phy0: Chip reset failed
Jul  5 12:28:02 Machine kernel: [ 5860.964498] ath: phy0: Unable to reset channel, reset status -22
Jul  5 12:28:02 Machine kernel: [ 5860.976707] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Jul  5 12:28:02 Machine kernel: [ 5861.160653] ath: phy0: Chip reset failed
Jul  5 12:28:02 Machine kernel: [ 5861.160660] ath: phy0: Unable to reset channel, reset status -22
Jul  5 12:28:02 Machine kernel: [ 5861.172763] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Jul  5 12:28:02 Machine kernel: [ 5861.357553] ath: phy0: Chip reset failed
Jul  5 12:28:02 Machine kernel: [ 5861.357565] ath: phy0: Unable to reset channel, reset status -22
Jul  5 12:28:02 Machine kernel: [ 5861.369422] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Jul  5 12:28:03 Machine kernel: [ 5861.551527] ath: phy0: Chip reset failed
Jul  5 12:28:03 Machine kernel: [ 5861.551532] ath: phy0: Unable to reset channel, reset status -22
Jul  5 12:28:03 Machine kernel: [ 5861.563233] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Jul  5 12:28:03 Machine kernel: [ 5861.745485] ath: phy0: Chip reset failed
Jul  5 12:28:03 Machine kernel: [ 5861.745489] ath: phy0: Unable to reset channel, reset status -22
Jul  5 12:28:03 Machine kernel: [ 5861.757319] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Jul  5 12:28:03 Machine kernel: [ 5861.943257] ath: phy0: Chip reset failed
Jul  5 12:28:03 Machine kernel: [ 5861.943265] ath: phy0: Unable to reset channel, reset status -22
Jul  5 12:28:03 Machine kernel: [ 5861.955560] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Jul  5 12:28:03 Machine kernel: [ 5862.141131] ath: phy0: Chip reset failed
Jul  5 12:28:03 Machine kernel: [ 5862.141138] ath: phy0: Unable to reset channel, reset status -22
Jul  5 12:28:03 Machine kernel: [ 5862.153162] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Jul  5 12:28:03 Machine kernel: [ 5862.339926] ath: phy0: Chip reset failed
Jul  5 12:28:03 Machine kernel: [ 5862.339937] ath: phy0: Unable to reset channel, reset status -22
Jul  5 12:28:03 Machine kernel: [ 5862.352647] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Jul  5 12:28:04 Machine kernel: [ 5862.540443] ath: phy0: Chip reset failed
Jul  5 12:28:04 Machine kernel: [ 5862.540450] ath: phy0: Unable to reset channel, reset status -22
Jul  5 12:28:04 Machine kernel: [ 5862.552323] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Jul  5 12:28:04 Machine kernel: [ 5862.738132] ath: phy0: Chip reset failed
Jul  5 12:28:04 Machine kernel: [ 5862.738139] ath: phy0: Unable to reset channel, reset status -22
Jul  5 12:28:04 Machine kernel: [ 5862.749852] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Jul  5 12:28:04 Machine kernel: [ 5862.932937] ath: phy0: Chip reset failed
Jul  5 12:28:04 Machine kernel: [ 5862.932944] ath: phy0: Unable to reset channel, reset status -22
Jul  5 12:28:04 Machine kernel: [ 5862.944730] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Jul  5 12:28:04 Machine kernel: [ 5863.129123] ath: phy0: Chip reset failed
Jul  5 12:28:04 Machine kernel: [ 5863.129131] ath: phy0: Unable to reset channel, reset status -22
Jul  5 12:28:04 Machine kernel: [ 5863.141654] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Jul  5 12:28:04 Machine kernel: [ 5863.326831] ath: phy0: Chip reset failed
Jul  5 12:28:04 Machine kernel: [ 5863.326839] ath: phy0: Unable to reset channel, reset status -22
Jul  5 12:28:04 Machine kernel: [ 5863.338751] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Jul  5 12:28:05 Machine kernel: [ 5863.526654] ath: phy0: Chip reset failed
Jul  5 12:28:05 Machine kernel: [ 5863.526665] ath: phy0: Unable to reset channel, reset status -22
Jul  5 12:28:05 Machine kernel: [ 5863.538588] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Jul  5 12:28:05 Machine kernel: [ 5863.725472] ath: phy0: Chip reset failed
Jul  5 12:28:05 Machine kernel: [ 5863.725480] ath: phy0: Unable to reset channel, reset status -22
Jul  5 12:28:05 Machine kernel: [ 5863.737467] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Jul  5 12:28:05 Machine kernel: [ 5863.920883] ath: phy0: Chip reset failed
Jul  5 12:28:05 Machine kernel: [ 5863.920890] ath: phy0: Unable to reset channel, reset status -22
Jul  5 12:28:05 Machine kernel: [ 5863.933028] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Jul  5 12:28:05 Machine kernel: [ 5864.115139] ath: phy0: Chip reset failed
Jul  5 12:28:05 Machine kernel: [ 5864.115144] ath: phy0: Unable to reset channel, reset status -22
Jul  5 12:28:05 Machine kernel: [ 5864.126971] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Jul  5 12:28:05 Machine kernel: [ 5864.309235] ath: phy0: Chip reset failed
Jul  5 12:28:05 Machine kernel: [ 5864.309239] ath: phy0: Unable to reset channel, reset status -22
Jul  5 12:28:05 Machine kernel: [ 5864.321520] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Jul  5 12:28:06 Machine kernel: [ 5864.503637] ath: phy0: Chip reset failed
Jul  5 12:28:06 Machine kernel: [ 5864.503643] ath: phy0: Unable to reset channel, reset status -22
Jul  5 12:28:06 Machine kernel: [ 5864.515552] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Jul  5 12:28:06 Machine kernel: [ 5864.698083] ath: phy0: Chip reset failed
Jul  5 12:28:06 Machine kernel: [ 5864.698087] ath: phy0: Unable to reset channel, reset status -22
Jul  5 12:28:06 Machine kernel: [ 5864.710103] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Jul  5 12:28:06 Machine kernel: [ 5864.896194] ath: phy0: Chip reset failed
Jul  5 12:28:06 Machine kernel: [ 5864.896201] ath: phy0: Unable to reset channel, reset status -22
Jul  5 12:28:06 Machine kernel: [ 5864.908412] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Jul  5 12:28:06 Machine kernel: [ 5865.090615] ath: phy0: Chip reset failed
Jul  5 12:28:06 Machine kernel: [ 5865.090620] ath: phy0: Unable to reset channel, reset status -22
Jul  5 12:28:06 Machine kernel: [ 5865.102356] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Jul  5 12:28:06 Machine kernel: [ 5865.284169] ath: phy0: Chip reset failed
Jul  5 12:28:06 Machine kernel: [ 5865.284174] ath: phy0: Unable to reset channel, reset status -22
Jul  5 12:28:06 Machine kernel: [ 5865.299140] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Jul  5 12:28:07 Machine kernel: [ 5865.481673] ath: phy0: Chip reset failed
Jul  5 12:28:07 Machine kernel: [ 5865.481679] ath: phy0: Unable to reset channel, reset status -22
Jul  5 12:28:07 Machine kernel: [ 5865.493569] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Jul  5 12:28:07 Machine kernel: [ 5865.680648] ath: phy0: Chip reset failed
Jul  5 12:28:07 Machine kernel: [ 5865.680656] ath: phy0: Unable to reset channel, reset status -22
Jul  5 12:28:07 Machine kernel: [ 5865.692360] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Jul  5 12:28:07 Machine kernel: [ 5865.877772] ath: phy0: Chip reset failed
Jul  5 12:28:07 Machine kernel: [ 5865.877778] ath: phy0: Unable to reset channel, reset status -22
Jul  5 12:28:07 Machine kernel: [ 5865.889681] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Jul  5 12:28:07 Machine kernel: [ 5866.074023] ath: phy0: Chip reset failed
Jul  5 12:28:07 Machine kernel: [ 5866.074030] ath: phy0: Unable to reset channel, reset status -22
Jul  5 12:28:07 Machine kernel: [ 5866.085728] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Jul  5 12:28:07 Machine kernel: [ 5866.267944] ath: phy0: Chip reset failed
Jul  5 12:28:07 Machine kernel: [ 5866.267950] ath: phy0: Unable to reset channel, reset status -22
Jul  5 12:28:07 Machine kernel: [ 5866.279935] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Jul  5 12:28:08 Machine kernel: [ 5866.461606] ath: phy0: Chip reset failed
Jul  5 12:28:08 Machine kernel: [ 5866.461611] ath: phy0: Unable to reset channel, reset status -22
Jul  5 12:28:08 Machine kernel: [ 5866.473557] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Jul  5 12:28:08 Machine kernel: [ 5866.663003] ath: phy0: Chip reset failed
Jul  5 12:28:08 Machine kernel: [ 5866.663013] ath: phy0: Unable to reset channel, reset status -22
Jul  5 12:28:08 Machine kernel: [ 5866.674843] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Jul  5 12:28:08 Machine kernel: [ 5866.862640] ath: phy0: Chip reset failed
Jul  5 12:28:08 Machine kernel: [ 5866.862648] ath: phy0: Unable to reset channel, reset status -22
Jul  5 12:28:08 Machine kernel: [ 5866.874530] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Jul  5 12:28:08 Machine kernel: [ 5867.059071] ath: phy0: Chip reset failed
Jul  5 12:28:08 Machine kernel: [ 5867.059076] ath: phy0: Unable to reset channel, reset status -22
Jul  5 12:28:08 Machine kernel: [ 5867.070805] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Jul  5 12:28:08 Machine kernel: [ 5867.252887] ath: phy0: Chip reset failed
Jul  5 12:28:08 Machine kernel: [ 5867.252891] ath: phy0: Unable to reset channel, reset status -22
Jul  5 12:28:09 Machine kernel: [ 5867.472489] ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
Jul  5 12:28:09 Machine kernel: [ 5867.484121] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Jul  5 12:28:10 Machine NetworkManager[858]: <warn>  [1625468290.7655] device (wlp8s0): link timed out.
Jul  5 12:28:10 Machine NetworkManager[858]: <info>  [1625468290.7666] device (wlp8s0): state change: activated -> failed (reason 'ssid-not-found', sys-iface-state: 'managed')
Jul  5 12:28:10 Machine NetworkManager[858]: <info>  [1625468290.8647] manager: NetworkManager state is now DISCONNECTED
Jul  5 12:28:10 Machine NetworkManager[858]: <warn>  [1625468290.8673] device (wlp8s0): Activation: failed for connection 'WiFi'
Jul  5 12:28:10 Machine whoopsie[1219]: [12:28:10] offline
Jul  5 12:28:10 Machine gnome-shell[2440]: An active wireless connection, in infrastructure mode, involves no access point?
Jul  5 12:28:10 Machine kernel: [ 5869.318583] ath: phy0: Failed to wakeup in 500us
Jul  5 12:28:10 Machine whoopsie[1219]: [12:28:10] Cannot reach: https://daisy.ubuntu.com
Jul  5 12:28:10 Machine avahi-daemon[853]: Withdrawing address record for fe80::5893:3fbe:29ec:8b8d on wlp8s0.
Jul  5 12:28:10 Machine NetworkManager[858]: <info>  [1625468290.8723] device (wlp8s0): state change: failed -> disconnected (reason 'none', sys-iface-state: 'managed')
Jul  5 12:28:10 Machine avahi-daemon[853]: Leaving mDNS multicast group on interface wlp8s0.IPv6 with address fe80::5893:3fbe:29ec:8b8d.
Jul  5 12:28:10 Machine systemd[1]: Starting Network Manager Script Dispatcher Service...
Jul  5 12:28:10 Machine avahi-daemon[853]: Interface wlp8s0.IPv6 no longer relevant for mDNS.
Jul  5 12:28:10 Machine gnome-shell[2440]: An active wireless connection, in infrastructure mode, involves no access point?
Jul  5 12:28:11 Machine kernel: [ 5869.535392] ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
Jul  5 12:28:11 Machine kernel: [ 5869.546892] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Jul  5 12:28:11 Machine dbus-daemon[857]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service' requested by ':1.11' (uid=0 pid=858 comm="/usr/sbin/NetworkManager --no-daemon " label="unconfined")
Jul  5 12:28:11 Machine gnome-shell[2440]: An active wireless connection, in infrastructure mode, involves no access point?
Jul  5 12:28:11 Machine gnome-shell[2440]: message repeated 2 times: [ An active wireless connection, in infrastructure mode, involves no access point?]
Jul  5 12:28:11 Machine NetworkManager[858]: <info>  [1625468290.9463] dhcp4 (wlp8s0): canceled DHCP transaction
Jul  5 12:28:11 Machine NetworkManager[858]: <info>  [1625468290.9463] dhcp4 (wlp8s0): state changed bound -> done
Jul  5 12:28:11 Machine dbus-daemon[857]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jul  5 12:28:11 Machine systemd[1]: Started Network Manager Script Dispatcher Service.
Jul  5 12:28:11 Machine whoopsie[1219]: [12:28:11] Cannot reach: https://daisy.ubuntu.com
Jul  5 12:28:11 Machine nm-dispatcher[16981]: run-parts: failed to stat component /etc/network/if-post-down.d/avahi-daemon: No such file or directory
Jul  5 12:28:11 Machine avahi-daemon[853]: Withdrawing address record for 192.168.0.117 on wlp8s0.
Jul  5 12:28:11 Machine avahi-daemon[853]: Leaving mDNS multicast group on interface wlp8s0.IPv4 with address 192.168.0.117.
Jul  5 12:28:11 Machine avahi-daemon[853]: Interface wlp8s0.IPv4 no longer relevant for mDNS.
Jul  5 12:28:11 Machine kernel: [ 5870.423757] ath: phy0: Failed to wakeup in 500us
Jul  5 12:28:12 Machine kernel: [ 5870.435374] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Jul  5 12:28:12 Machine kernel: [ 5870.615758] ath: phy0: Chip reset failed
Jul  5 12:28:12 Machine kernel: [ 5870.615762] ath: phy0: Unable to reset channel, reset status -22

```

---

### Post by zircon_34 on 2021-07-05
Thats for sure frustrating. 

For one, your system may be borked with kernel upgrades/downgrades and two different DE with now KDE wiped. It is rather difficult to troubleshoot. Perhaps focus first on the system freeze and then issue a separate ticket for the wifi driver.

I have not dealt much with radeon but someone may be able to help since now we have a model posted &#128521;

I would probably try reinstalling Ubuntu, perhaps check a live usb with 21.04 to see if it runs well with gnome 3.38. From my experience these freeze are graphics card driver related or some bug in gnome. Make sure to backup your data.

---

