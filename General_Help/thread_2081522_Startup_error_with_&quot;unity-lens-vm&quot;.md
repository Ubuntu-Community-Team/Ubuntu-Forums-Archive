---
title: "Startup error with &quot;unity-lens-vm&quot;"
date: 2012-11-07
forum: General Help
---

### Post by qrwe on 2012-11-07
Hi!
Every time I boot up my Ubuntu installation, a dialog appears because of an "internal error", with the option to send an error report. Error information is:
```

/opt/extras.ubuntu.com/unity-lens-vm/unity-lens-vm
Traceback (most recent call last):
  File "unity-lens-vm", line 41, in <module>
    from unity_lens_vm import UnityLensVmLens
ImportError: cannot import name UnityLensVmLens

```
...where unity-lens-vm seems to be some python script that runs at startup time. Does anybody know what this script does and what to do about the missing module, e.g. if there's something that could be installed? Thanks!

---

### Post by cwayne18 on 2012-12-09
This has been fixed in the latest version, now in the extras repo

---

### Post by qrwe on 2012-12-10
Awesome!

---

