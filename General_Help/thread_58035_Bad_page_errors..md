---
title: "Bad page errors."
date: 2005-08-18
forum: General Help
---

### Post by audax321 on 2005-08-18
I was looking at the output from dmesg and noticed this just a few moments ago. Any idea why this is coming up. I have been experiencing a lot of system freezes/lock-ups lately for no apparant reason... I mean the damn thing just sits there with nothing running and just locks.. really annoying because my windows-zealot brother is always looking over and saying maybe you should switch back to windows. Of course, he's formatted his computer 3 times in the past week  [-X 

Here is the output from dmesg:

```

Bad page state at free_hot_cold_page (in process 'totem', page c14432a0)
flags:0x20000000 mapping:00000000 mapcount:0 count:-16777216
Backtrace:
 [<c013e9d7>] bad_page+0x78/0xab
 [<c013f0c9>] free_hot_cold_page+0x71/0x11d
 [<f8855cf5>] unix_poll+0x2b/0xa2 [unix]
 [<c016b8e1>] poll_freewait+0x38/0x40
 [<c016bc4d>] do_select+0x1be/0x2c6
 [<c016b8e9>] __pollwait+0x0/0xc7
 [<c016c02d>] sys_select+0x2b3/0x4c6
 [<c0158f2f>] vfs_read+0x12e/0x13a
 [<c0102f1d>] sysenter_past_esp+0x52/0x75
Trying to fix it up, but a reboot is needed
Bad page state at free_hot_cold_page (in process 'perl', page c1443280)
flags:0x20000000 mapping:00000000 mapcount:0 count:-16777216
Backtrace:
 [<c013e9d7>] bad_page+0x78/0xab
 [<c013f0c9>] free_hot_cold_page+0x71/0x11d
 [<c016b8e1>] poll_freewait+0x38/0x40
 [<c016bc4d>] do_select+0x1be/0x2c6
 [<c016b8e9>] __pollwait+0x0/0xc7
 [<c016c02d>] sys_select+0x2b3/0x4c6
 [<c0102f1d>] sysenter_past_esp+0x52/0x75
Trying to fix it up, but a reboot is needed

```

---

