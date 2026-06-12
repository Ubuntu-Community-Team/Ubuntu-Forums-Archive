---
title: "repeating message in terminal"
date: 2007-07-26
forum: General Help
---

### Post by scandune on 2007-07-26
i get this message that repeats in terminal

message from syslogd@scandune-desktop at (the current date) .....
scandune-desktop kernal [numbers] EDAC MC0: UE page 0x2000, offset 0x0, grain 4096, row 0, labels ":": i82875p UE

i am also trying to get sound from adobe that is why i need to get in terminal

also i have 2 monitors is there a way that i can extend it like in windows

---

### Post by scandune on 2007-07-26
just a quick note the numbers change after kernel as well as the page i have left it on for some time and it keeps on repeating

Message from syslogd@scandune-desktop at Thu Jul 26 15:36:38 2007 ...
scandune-desktop kernel: [241425.804629] EDAC MC0: UE page 0x201b, offset 0x0, grain 4096, row 0, labels ":": i82875p UE

Message from syslogd@scandune-desktop at Thu Jul 26 15:36:39 2007 ...
scandune-desktop kernel: [241426.803563] EDAC MC0: UE page 0x1f8ba, offset 0x0, grain 4096, row 0, labels ":": i82875p UE

Message from syslogd@scandune-desktop at Thu Jul 26 15:36:40 2007 ...
scandune-desktop kernel: [241427.802498] EDAC MC0: UE page 0x2020, offset 0x0, grain 4096, row 0, labels ":": i82875p UE

Message from syslogd@scandune-desktop at Thu Jul 26 15:36:41 2007 ...
scandune-desktop kernel: [241428.801434] EDAC MC0: UE page 0x201b, offset 0x0, grain 4096, row 0, labels ":": i82875p UE

Message from syslogd@scandune-desktop at Thu Jul 26 15:36:42 2007 ...
scandune-desktop kernel: [241429.800368] EDAC MC0: UE page 0x2000, offset 0x0, grain 4096, row 0, labels ":": i82875p UE

---

### Post by tbroderick on 2007-07-26
It's a bug with the EDAC module. You could try sudo rmod edac, but I don't know how that would effect your setup.

[https://bugs.launchpad.net/ubuntu/+bug/113793](https://bugs.launchpad.net/ubuntu/+bug/113793)

---

### Post by scandune on 2007-07-26
k thanks now for any of the other 2?

---

