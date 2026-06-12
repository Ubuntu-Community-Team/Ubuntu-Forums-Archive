---
title: "Network Manager is too verbose in syslog"
date: 2006-07-03
forum: General Help
---

### Post by A.Skwar on 2006-07-03
Hello.

In my syslog, I find **A LOT** of messages like this:

```
Jun 30 23:07:06 localhost NetworkManager: <information>^Iwpa_supplicant(9561): 8 b9 ff bb 4b c0 07 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 84 b1 31 5c 74 10 71 81 69 c1 f4 9b 20 3e 5b 0b 00 20 98 63 a7 c1 0b 44 ab a7 ca 6b 83 fb 56 c0 42 03 b7 8e 70 ee b4 6f 07 ff 49 0e 77 9f 0e d4 a1 cc
Jun 30 23:07:06 localhost NetworkManager: <information>^Iwpa_supplicant(9561): IEEE 802.1X RX: version=1 type=3 length=127
Jun 30 23:07:06 localhost NetworkManager: <information>^Iwpa_supplicant(9561):   EAPOL-Key type=254
Jun 30 23:07:06 localhost NetworkManager: <information>^Iwpa_supplicant(9561): WPA: RX EAPOL-Key - hexdump(len=131): 01 03 00 7f fe 03 a1 00 20 00 00 00 00 00 00 00 02 75 da c2 bc 04 56 ed 0b d0 93 22 ba c4 eb 95 bd 61 6d ef bb 67 f7 d0 8d b2 46 a8 b9 ff bb 4b b4 61 6d ef bb 67 f7 d0 8d b2 46 a8 b9 ff bb 4b c0 07 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 84 b1 31 5c 74 10 71 81 69 c1 f4 9b 20 3e 5b 0b 00 20 98 63 a7 c1 0b 44 ab a7 ca 6b 83 fb 56 c0 42 03 b7 8e 70 ee b4 6f 07 ff 49 0e 77 9f 0e d4 a1 cc
```

This seems to be debug information from NetworkManager, I suppose.

Well - I don't care about those messages. And the huge amount of messages make it hard to catch other information.

How can I make NetworkManager be less verbose?

Thanks,

Alexander

---

