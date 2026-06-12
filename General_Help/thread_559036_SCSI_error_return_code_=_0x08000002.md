---
title: "SCSI error: return code = 0x08000002"
date: 2007-09-24
forum: General Help
---

### Post by cccc on 2007-09-24
hi everyone

I have feisty installed:```
$ uname -a
Linux ania 2.6.20-16-386 #2 Fri Aug 31 00:51:58 UTC 2007 i686 GNU/Linux

``` and during the restart I get a lot of these errors:```

Sep 24 23:20:01 localhost kernel: [   50.555109] sr 1:0:0:0: SCSI error: return code = 0x08000002
Sep 24 23:20:01 localhost kernel: [   50.555115] sr0: Current: sense key: Medium Error
Sep 24 23:20:01 localhost kernel: [   50.555119]     Additional sense: Unable to recover table-of-contents
Sep 24 23:20:01 localhost kernel: [   50.555129] end_request: I/O error, dev sr0, sector 0
Sep 24 23:20:01 localhost kernel: [   50.556582] sr 1:0:0:0: SCSI error: return code = 0x08000002
Sep 24 23:20:01 localhost kernel: [   50.556585] sr0: Current: sense key: Medium Error
Sep 24 23:20:01 localhost kernel: [   50.556588]     Additional sense: Unable to recover table-of-contents
Sep 24 23:20:01 localhost kernel: [   50.556595] end_request: I/O error, dev sr0, sector 0
Sep 24 23:20:01 localhost kernel: [   50.558005] sr 1:0:0:0: SCSI error: return code = 0x08000002
Sep 24 23:20:01 localhost kernel: [   50.558009] sr0: Current: sense key: Medium Error
Sep 24 23:20:01 localhost kernel: [   50.558012]     Additional sense: Unable to recover table-of-contents
Sep 24 23:20:01 localhost kernel: [   50.558021] end_request: I/O error, dev sr0, sector 0
Sep 24 23:20:01 localhost kernel: [   50.582278] sr 1:0:0:0: SCSI error: return code = 0x08000002
Sep 24 23:20:01 localhost kernel: [   50.582283] sr0: Current: sense key: Medium Error
Sep 24 23:20:01 localhost kernel: [   50.582285]     Additional sense: Unable to recover table-of-contents
Sep 24 23:20:01 localhost kernel: [   50.582293] end_request: I/O error, dev sr0, sector 0
```
knows someone what's wrong and howto solve this problem ?

---

### Post by por100pre1 on 2007-09-24
Not sure about it, but it looks like an issue with your hdd or other hardware... :-k

Try using a LiveCD to see if it works.

---

