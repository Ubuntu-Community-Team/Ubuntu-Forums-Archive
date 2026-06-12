---
title: "vlc error"
date: 2006-10-19
forum: General Help
---

### Post by vaskark on 2006-10-19
I'm getting this error when starting vlc:

VLC media player 0.9.0-svn Grishenko
[00000001] main libvlc error: no memcpy module matched "any"
[00000007] main access error: no access2 module matched "file"
[00000006] main input error: no suitable access module for `file/xspf-open:///home/vaskark/.vlc/ml.xsp'
[00000011] main interface error: no interface module matched "xosd,none"
[00000011] main interface error: no suitable interface module
[00000001] main libvlc error: interface "xosd,none" initialization failed
[00000012] main interface error: no interface module matched "hotkeys,none"
[00000012] main interface error: no suitable interface module
[00000001] main libvlc error: interface "hotkeys,none" initialization failed
[00000013] main interface error: no interface module matched "screensaver,none"
[00000013] main interface error: no suitable interface module
[00000001] main libvlc error: interface "screensaver,none" initialization failed
[00000014] main interface error: no interface module matched "any"
[00000014] main interface error: no suitable interface module
[00000001] main libvlc error: interface "(null)" initialization failed
[00000005] main playlist: saving Media Library to file /home/vaskark/.vlc/ml.xsp
[00000005] main playlist error: no playlist export module matched "export-xspf"
[00000005] main playlist error: cannot delete object (5, (null)) with children

Anyone else seeing this?

---

### Post by ATAQ on 2006-10-19
I dunno, strange, it looks to me like VLC is looking for root access, as in not allowed delete and stuff.
maybe just maybe try sudo vlc, as a test, terminate after that

---

