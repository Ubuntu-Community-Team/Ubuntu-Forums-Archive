---
title: "Ubuntu freezing randomly, seems like going to sleep for a second"
date: 2013-08-11
forum: General Help
---

### Post by marek-pestkowski on 2013-08-11
[COLOR=#000000][FONT=Arial]I have a really irritating problem with my laptop (**HP Elitebook 8530w**) and **Ubuntu 13.04**. Every about 30 minutes ( this is not constant) system freezing completely for about 3-5 seconds and then everything is back to normal. During freeze "WIFI" LED is changing color, so I'm guessing that this is some kind of wifi adapter issue:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Can you give me any hints how to find a solution? What logs and settings should I check?

My OS: **Ubuntu 13.04 x64** kernel: [B]3.8.0-19-generic

[/B]Here, some output from dmesg: (just after freeze)

> [/FONT][/COLOR][94049.005577] iwlwifi 0000:03:00.0: No space in command queue[94049.005584] iwlwifi 0000:03:00.0: Restarting adapter queue is full
[94049.005596] iwlwifi 0000:03:00.0: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
[94049.500370] iwlwifi 0000:03:00.0: Failing on timeout while stopping DMA channel 1 [0xa5a5a5a0]
[94049.500370] iwlwifi 0000:03:00.0: Failing on timeout while stopping DMA channel 3 [0xa5a5a5a0]
[94049.500370] iwlwifi 0000:03:00.0: Failing on timeout while stopping DMA channel 4 [0xa5a5a5a0]
[94049.500370] iwlwifi 0000:03:00.0: Failing on timeout while stopping DMA channel 6 [0xa5a5a5a0]
[94056.980495] iwlwifi 0000:03:00.0: Master Disable Timed Out, 100 usec
[94056.988032] ieee80211 phy0: Hardware restart was requested
[94056.989228] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[94056.989613] iwlwifi 0000:03:00.0: Radio type=0x0-0x2-0x0
[94366.000051] iwlwifi 0000:03:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
[94366.000054] iwlwifi 0000:03:00.0: Current CMD queue read_ptr 30 write_ptr 32
[94429.008052] iwlwifi 0000:03:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
[94429.008056] iwlwifi 0000:03:00.0: Current CMD queue read_ptr 30 write_ptr 33
[94492.000316] iwlwifi 0000:03:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
[94492.000328] iwlwifi 0000:03:00.0: Current CMD queue read_ptr 30 write_ptr 34
[94555.004323] iwlwifi 0000:03:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
[94555.004335] iwlwifi 0000:03:00.0: Current CMD queue read_ptr 30 write_ptr 35
[94618.000077] iwlwifi 0000:03:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
[94618.000082] iwlwifi 0000:03:00.0: Current CMD queue read_ptr 30 write_ptr 36
[94681.004303] iwlwifi 0000:03:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
[94681.004315] iwlwifi 0000:03:00.0: Current CMD queue read_ptr 30 write_ptr 37
[94744.000328] iwlwifi 0000:03:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
[94744.000340] iwlwifi 0000:03:00.0: Current CMD queue read_ptr 30 write_ptr 38
[94807.004330] iwlwifi 0000:03:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
[94807.004342] iwlwifi 0000:03:00.0: Current CMD queue read_ptr 30 write_ptr 39
[94870.000330] iwlwifi 0000:03:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
[94870.000342] iwlwifi 0000:03:00.0: Current CMD queue read_ptr 30 write_ptr 40
[94933.004090] iwlwifi 0000:03:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
[94933.004096] iwlwifi 0000:03:00.0: Current CMD queue read_ptr 30 write_ptr 41
[94996.000101] iwlwifi 0000:03:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
[94996.000113] iwlwifi 0000:03:00.0: Current CMD queue read_ptr 30 write_ptr 42
[95059.004320] iwlwifi 0000:03:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
[95059.004332] iwlwifi 0000:03:00.0: Current CMD queue read_ptr 30 write_ptr 43
[95122.000030] iwlwifi 0000:03:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
[95122.000034] iwlwifi 0000:03:00.0: Current CMD queue read_ptr 30 write_ptr 44
[95185.004059] iwlwifi 0000:03:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
[95185.004071] iwlwifi 0000:03:00.0: Current CMD queue read_ptr 30 write_ptr 45
[95248.000338] iwlwifi 0000:03:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
[95248.000351] iwlwifi 0000:03:00.0: Current CMD queue read_ptr 30 write_ptr 46
[95311.004329] iwlwifi 0000:03:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
[95311.004342] iwlwifi 0000:03:00.0: Current CMD queue read_ptr 30 write_ptr 47
[95327.437338] systemd-hostnamed[19333]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[95374.000056] iwlwifi 0000:03:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
[95374.000060] iwlwifi 0000:03:00.0: Current CMD queue read_ptr 30 write_ptr 48
[95437.000153] iwlwifi 0000:03:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
[95437.000164] iwlwifi 0000:03:00.0: Current CMD queue read_ptr 30 write_ptr 49
[95500.000309] iwlwifi 0000:03:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
[95500.000322] iwlwifi 0000:03:00.0: Current CMD queue read_ptr 30 write_ptr 50
[95563.004090] iwlwifi 0000:03:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
[95563.004102] iwlwifi 0000:03:00.0: Current CMD queue read_ptr 30 write_ptr 51
[95626.000079] iwlwifi 0000:03:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
[95626.000085] iwlwifi 0000:03:00.0: Current CMD queue read_ptr 30 write_ptr 52
[95689.004050] iwlwifi 0000:03:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
[95689.004054] iwlwifi 0000:03:00.0: Current CMD queue read_ptr 30 write_ptr 53
[95752.000344] iwlwifi 0000:03:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
[95752.000356] iwlwifi 0000:03:00.0: Current CMD queue read_ptr 30 write_ptr 54
[95815.004047] iwlwifi 0000:03:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
[95815.004059] iwlwifi 0000:03:00.0: Current CMD queue read_ptr 30 write_ptr 55
[95878.000332] iwlwifi 0000:03:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
[95878.000344] iwlwifi 0000:03:00.0: Current CMD queue read_ptr 30 write_ptr 56
[95941.004067] iwlwifi 0000:03:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
[95941.004071] iwlwifi 0000:03:00.0: Current CMD queue read_ptr 30 write_ptr 57
[96004.000074] iwlwifi 0000:03:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
[96004.000078] iwlwifi 0000:03:00.0: Current CMD queue read_ptr 30 write_ptr 58
[96067.004310] iwlwifi 0000:03:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
[96067.004322] iwlwifi 0000:03:00.0: Current CMD queue read_ptr 30 write_ptr 59
[96130.000314] iwlwifi 0000:03:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
[96130.000326] iwlwifi 0000:03:00.0: Current CMD queue read_ptr 30 write_ptr 60
[96191.005055] iwlwifi 0000:03:00.0: No space in command queue
[96191.005067] iwlwifi 0000:03:00.0: Restarting adapter queue is full
[96191.005085] iwlwifi 0000:03:00.0: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
[96191.017720] iwlwifi 0000:03:00.0: Failing on timeout while stopping DMA channel 1 [0xa5a5a5a0]
[96191.017720] iwlwifi 0000:03:00.0: Failing on timeout while stopping DMA channel 3 [0xa5a5a5a0]
[96191.017720] iwlwifi 0000:03:00.0: Failing on timeout while stopping DMA channel 4 [0xa5a5a5a0]
[96191.017720] iwlwifi 0000:03:00.0: Failing on timeout while stopping DMA channel 6 [0xa5a5a5a0]


[COLOR=#000000][FONT=Arial]
[/FONT][/COLOR]

---

