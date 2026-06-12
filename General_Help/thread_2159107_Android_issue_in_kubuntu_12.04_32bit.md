---
title: "Android issue in kubuntu 12.04 32bit"
date: 2013-07-01
forum: General Help
---

### Post by i8086 on 2013-07-01
I want to download android 4.2.2 source in kubuntu 12.04. The os was installed inside vmware 9.0 with host os Win7 64bit.

I do the following to download:
cd ~/android
curl [https://dl-ssl.google.com/dl/googlesource/git-repo/repo](https://dl-ssl.google.com/dl/googlesource/git-repo/repo) > ./repo
chmod a+x ./repo
./repo init -u [https://android.googlesource.com/platform/manifest](https://android.googlesource.com/platform/manifest) -b android-4.2.2_r1
./repo sync

After I tried many times 'repo sync' cmd, the source code is nearly download completed.
The final message is:
...
Fetching projects: 99% (325/328)

No more message appear after a long wait. The cmd seems deadlock.

According to google suggestion, I run '[COLOR=#006600][FONT=monospace]sysctl -w net.ipv4.tcp_window_scaling=0[/FONT][/COLOR]' before run 'repo sync' again. But the same problem exists.

---

### Post by i8086 on 2013-07-01
This problem is fixed. It's not a problem actually.

Finally sync success after a long wait.

---

