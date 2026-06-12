---
title: "every 10 minutes a 30s freeze while video play"
date: 2007-10-17
forum: General Help
---

### Post by eaz2 on 2007-10-17
every 10 minutes, my system freezes for 30 seconds, and than resumes as normal. 
I suspect the cifs mount on the NAS, as this does not happen when i copy the avi file to the local disk.

the energy save things have been switched off, as is the screensaver.

I mounted the nas with cifs in fstab. 
Is there anything like a timeout or something?

---

### Post by eaz2 on 2007-10-17
this is in the log file:

Oct 16 20:41:33 mediac kernel: [  691.269713]  CIFS VFS: server not responding
Oct 16 20:41:33 mediac kernel: [  691.269723]  CIFS VFS: No response to cmd 46 mid 16588
Oct 16 20:41:33 mediac kernel: [  691.269732]  CIFS VFS: Send error in read = -11
Oct 16 20:41:33 mediac kernel: [  691.269743]  CIFS VFS: No response for cmd 50 mid 16589
Oct 16 20:41:35 mediac kernel: [  692.147422]  CIFS VFS: Send error in read = -9
Oct 16 20:53:18 mediac kernel: [ 1028.963816]  CIFS VFS: server not responding
Oct 16 20:53:18 mediac kernel: [ 1028.963825]  CIFS VFS: No response to cmd 46 mid 26259
Oct 16 20:53:18 mediac kernel: [ 1028.963834]  CIFS VFS: Send error in read = -11
Oct 16 20:53:18 mediac kernel: [ 1028.963846]  CIFS VFS: No response for cmd 50 mid 26260
Oct 16 20:53:20 mediac kernel: [ 1029.741844]  CIFS VFS: Send error in read = -9
Oct 16 21:03:48 mediac kernel: [ 1375.335086]  CIFS VFS: server not responding
Oct 16 21:03:48 mediac kernel: [ 1375.335093]  CIFS VFS: No response to cmd 46 mid 36463
Oct 16 21:03:48 mediac kernel: [ 1375.335099]  CIFS VFS: Send error in read = -11
Oct 16 21:03:48 mediac kernel: [ 1375.335919]  CIFS VFS: No response for cmd 50 mid 36464
Oct 16 21:03:55 mediac kernel: [ 1378.762151]  CIFS VFS: Send error in read = -9
Oct 16 21:17:48 mediac kernel: [ 1780.474649]  CIFS VFS: server not responding
Oct 16 21:17:48 mediac kernel: [ 1780.474658]  CIFS VFS: No response to cmd 46 mid 49678
Oct 16 21:17:48 mediac kernel: [ 1780.474665]  CIFS VFS: Send error in read = -11
Oct 16 21:17:48 mediac kernel: [ 1780.474675]  CIFS VFS: No response for cmd 50 mid 49679
Oct 16 21:18:39 mediac kernel: [ 1805.343428]  CIFS VFS: Send error in Close = -9
Oct 16 21:18:39 mediac kernel: [ 1805.347431]  CIFS VFS: Send error in Close = -9
Oct 16 21:32:33 mediac kernel: [ 2231.490608]  CIFS VFS: server not responding
Oct 16 21:32:33 mediac kernel: [ 2231.490617]  CIFS VFS: No response for cmd 50 mid 56223
Oct 16 21:44:33 mediac kernel: [ 2592.176610]  CIFS VFS: server not responding
Oct 16 21:44:33 mediac kernel: [ 2592.176620]  CIFS VFS: No response to cmd 46 mid 62278
Oct 16 21:44:33 mediac kernel: [ 2592.176629]  CIFS VFS: Send error in read = -11
Oct 16 21:54:03 mediac kernel: [ 2874.574293]  CIFS VFS: server not responding
Oct 16 21:54:03 mediac kernel: [ 2874.574301]  CIFS VFS: No response to cmd 46 mid 922
Oct 16 21:54:03 mediac kernel: [ 2874.574308]  CIFS VFS: Send error in read = -11

---

