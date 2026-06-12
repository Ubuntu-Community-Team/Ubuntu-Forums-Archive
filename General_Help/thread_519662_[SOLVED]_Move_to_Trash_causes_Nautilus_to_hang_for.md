---
title: "[SOLVED] Move to Trash causes Nautilus to hang for ~15sec"
date: 2007-08-07
forum: General Help
---

### Post by neurosis on 2007-08-07
Whenever I 'Move To Trash' any file via Nautilus, I get a 15-20 second pause wherein Nautilus stops responding. 'dmesg' outputs the following:

[1215181.005898] smb_add_request: request [e58de080, mid=13491] timed out!
[1227236.288639] smb_add_request: request [d1b35d80, mid=13493] timed out!
[1227236.295058] smb_add_request: request [d1b35c80, mid=13492] timed out!
[1314761.910579] smb_add_request: request [e3c2cd80, mid=13494] timed out!
[1314807.691121] smb_add_request: request [c9edbe80, mid=13495] timed out!
[1315095.478272] smb_add_request: request [e8f36e80, mid=13496] timed out!
[1498847.182840] smb_add_request: request [dd4aae80, mid=13497] timed out!
[1498973.251030] smb_add_request: request [db304e80, mid=13498] timed out!
[1501595.237588] smb_add_request: request [efd95e80, mid=13499] timed out!
[1501774.827967] smb_add_request: request [da6cde80, mid=13500] timed out!

The file is local - not sure where Samba is coming into play here. Any ideas?

---

### Post by neurosis on 2007-08-07
Oddly enough, this seems to have disappeared after I killed a dead 'apt-get -qq update', re-ran the update, and upgraded several packages.

---

