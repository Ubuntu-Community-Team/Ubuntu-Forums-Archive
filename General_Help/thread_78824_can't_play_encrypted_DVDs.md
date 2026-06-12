---
title: "can't play encrypted DVDs"
date: 2005-10-19
forum: General Help
---

### Post by meonkeys on 2005-10-19
Whenever I try to play an encrypted DVD, I see tons of messages in /var/log/messages like this:

```

Oct 18 20:36:25 compost kernel: [4329449.771000] hdd: command error: status=0x51 { DriveReady SeekComplete Error }
Oct 18 20:36:25 compost kernel: [4329449.771000] hdd: command error: error=0x50 { LastFailedSense=0x05 }
Oct 18 20:36:25 compost kernel: [4329449.771000] ide: failed opcode was: unknown
Oct 18 20:36:25 compost kernel: [4329449.771000] end_request: I/O error, dev hdd, sector 10232

```

Yes, I ran that little script to install the css stuff as suggested whenever mplayer/ogle/etc. was used to try playing an encrypted DVD, but no, it doesn't work. Unencrypted DVDs play fine in Totem, Mplayer, Ogle, and Xine.

Any ideas what might be causing this? Encrypted DVDs play fine using Fedora Core 4.

---

### Post by dukeinlondon on 2005-10-19
You seem to get problems before anything is actually read. Any luck with data DVDs ?

---

### Post by meonkeys on 2005-10-19
Data DVDs work fine.

---

