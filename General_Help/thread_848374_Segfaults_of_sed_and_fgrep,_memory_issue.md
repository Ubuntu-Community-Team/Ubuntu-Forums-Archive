---
title: "Segfaults of sed and fgrep, memory issue?"
date: 2008-07-03
forum: General Help
---

### Post by rocktorrentz on 2008-07-03
For a while now on my Ubuntu 8.04 server (upgraded from 7.10) I've been getting segfaults in my dmesg, although have noticed no issues caused by them. It was built from untested parts I've had lying around for a while so the motherboard, cpu or ram could have issues although it's never crashed in the few months I've been using it. Here is a snippet from my current dmesg:
```
[306599.674637] sed[31775]: segfault at 0000004c eip b7ee62e6 esp bf8032d8 error 6
[306609.317770] fgrep[32122]: segfault at 0000004c eip b7efe2e6 esp bfac4c58 error 6
[306609.461753] fgrep[32153]: segfault at 0000004c eip b7efe2e6 esp bfed5058 error 6
[349746.741886] fgrep[7703]: segfault at 0000004c eip b7f3e2e6 esp bfff31b8 error 6
[400099.125917] fgrep[17719]: segfault at 0000004c eip b7ef92e6 esp bfc375d8 error 6
[673386.906198] sed[3246]: segfault at 0000004c eip b7f262e6 esp bfccb788 error 6
```

Is it worth bringing down my server and running memtest off a live cd? It has 3 sticks of ram (each 256mb) and I could definitely live without one or more of them (it's just a file server running samba, nfs and rtorrent).

Thanks in advance

---

### Post by rocktorrentz on 2008-07-05
Bump...nobody has any kind of opinion on this?

---

