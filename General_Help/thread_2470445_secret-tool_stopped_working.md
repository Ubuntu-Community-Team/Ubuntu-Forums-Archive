---
title: "secret-tool stopped working"
date: 2021-12-30
forum: General Help
---

### Post by enboig on 2021-12-30
I enabled keepassxc (updated from ppa) to be used as keyring. Then started using "secret-tool" (from "libsecret-tools") to use my passwords in my scripts. All worked ok until some days ago, now *secret-tool* can store new credentials (so keepassxc is working ok), but retriving passwords return nothing, and deleting them crash with a "segmentation fault".
I tryied reinstalling the package, but the problem continues.

I don't know how or where to report this bug. Can somebody help me?

Thanks

---

### Post by schragge on 2021-12-30
> **enboig said:**
> deleting them crash with a "segmentation fault"
Does [issue #69]("https://gitlab.gnome.org/GNOME/libsecret/-/issues/69") correctly describe your situation? Or rather [issue #56](https://gitlab.gnome.org/GNOME/libsecret/-/issues/56) does?

In the latter case, does **secret-tool search --unlock** work as expected? Then [this]("https://github.com/keepassxreboot/keepassxc/issues/4443#issuecomment-599653832") may be the reason.

---

