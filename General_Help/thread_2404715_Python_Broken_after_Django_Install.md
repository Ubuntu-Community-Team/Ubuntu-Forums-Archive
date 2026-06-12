---
title: "Python Broken after Django Install"
date: 2018-10-27
forum: General Help
---

### Post by jnabasny on 2018-10-27
I installed django on my Xubuntu 18.04 and changed my default python version from 2 to 3. I later read that 18.04 doesn't support python3. I tried switching it back, but must've did something wrong and now I can't install or remove any packages. I've tried remove python altogether and reinstalling it, but I can't even do that. This is the most common error I get:

```
dpkg: warning: old update-manager package pre-removal script subprocess returned error exit status 127

```
This is the output when I try **sudo apt autoremove**:[ https://pastebin.com/sjhiDSsP]("https://pastebin.com/sjhiDSsP")

I tried deleting the three .deb files listed at the end of that output, but there was no change and it still lists them when I run the command again. All I want to do is get python (and APT) functional again.

---

### Post by jnabasny on 2018-10-28
I wiped my harddrive and installed Bodhi.

---

