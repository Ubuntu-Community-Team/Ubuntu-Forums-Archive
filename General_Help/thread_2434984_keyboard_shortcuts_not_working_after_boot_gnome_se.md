---
title: "keyboard shortcuts not working after boot: gnome settings daemon error"
date: 2020-01-14
forum: General Help
---

### Post by Pandanus on 2020-01-14
After a fresh boot keyboard shortcuts involving ctrl + alt are not working.
When logging out (not shutting down) and back in they work as expected.
This is reproducible / happens about 90% of the time.

when trying to open a terminal with 'ctrl + alt + t' (which fails) and looking at the journal (journalctl -r | head) I get:

```
gsd-media-keys[1321]: Could not find accelerator for accel id 134
```

which I think is the culprit, but don't know how to proceed...

System:
Ubuntu (Budgie) 18.04.3

any ideas where/how I could start debugging this would be greatly appreciated!

For anyone having a similar issue:
I did some more research and found that this is a known bug in gnome-settings-daemon 3.28,
which seems to be fixed in 3.29:

[https://github.com/GNOME/gnome-settings-daemon/commit/05f168842f4754fa409029651842e9333f75fe05](https://github.com/GNOME/gnome-settings-daemon/commit/05f168842f4754fa409029651842e9333f75fe05)

Ubuntu 18.04 unfortunately is still on 3.28 (dpkg -l gnome-settings-daemon):
```

ii  gnome-settings-daemon 3.28.1-0ubuntu1.3 amd64        daemon handling the GNOME session settings

```

---

### Post by davidmohammed on 2020-01-16
If you enable our backports PPA (budgie-welcome - recommendations) - you will get both budgie-desktop v10.5 and it includes a fix that we are testing for this issue.

---

### Post by Pandanus on 2020-01-20
@davidmohammed, thanks a lot for this information!
I enabled the backports, and all seems to be working fine now (difficult to be 100% sure, as only happened 3 out of 4 times before, but it's looking good).

---

