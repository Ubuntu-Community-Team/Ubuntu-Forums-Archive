---
title: "Under the hood: Linux 2.6.20.15??"
date: 2007-04-22
forum: General Help
---

### Post by nixclusive on 2007-04-22
Hello everybody, the latest kernel version (as of 23 Apr-07) offered at the [linux kernel archives](http://kernel.org/) is 2.6.20.7. But the [release notes for xubuntu fiesty fawn](https://wiki.ubuntu.com/Xubuntu/ReleaseNotes/FeistyFawn) document the availability of kernel version 2.6.20.15. What? is that a BIG typo or do you guys really have a time machine out there?

Just a thought... any replies?

---

### Post by hikaricore on 2007-04-22
I'm running 2.6.20-15 on my media server right now.

I believe it's a typo on the release notes page.

---

### Post by vigleik on 2007-04-22
This doesn't make it completely clear to me, because I haven't studied how the numbering works in details. and 2.6.20.15 and 2.6.20-15 doesn't look that different to me. So...2.6.20-15 is the 15th iteration of the ubuntu-tweaks to kernel 2.6.20, aka 2.6.20.0? Would 2.6.20.0-15 be an equally appropriate name?

---

### Post by engla on 2007-04-22
Simply, the .7 and -15 subversions have no relationship!

Ubuntu uses the 2.6.20.* kernel as baseline for its kernel, then it merges things from 2.6.20.*-releases as they happen, and they also merge in stuff that is not in the mainline (say from 2.6.21-rc and such). This is a tradition like any other, -20 is just a distro version of a kernel, and you can't tell how far it is on the .0 to .7 road..

---

### Post by nixclusive on 2007-04-23
Now that explains.. its 2.6.20**-15** Probably a typo... alright thanks everyone. Doesn't really matter that much as I compile a kernel specific to my machine anyway. ;-)

---

