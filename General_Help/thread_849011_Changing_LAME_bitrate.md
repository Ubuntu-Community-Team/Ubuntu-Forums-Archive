---
title: "Changing LAME bitrate"
date: 2008-07-04
forum: General Help
---

### Post by skipsbro on 2008-07-04
How do you change the importing bitrate on LAME?

---

### Post by nikgare on 2008-07-04
```
lame --help

OPTIONS:
    -b bitrate      set the bitrate, default 128 kbps
    -h              higher quality, but a little slower.  Recommended.
    -f              fast mode (lower quality)
    -V n            quality setting for VBR.  default n=4
                    0=high quality,bigger files. 9=smaller files
    --preset type   type must be "medium", "standard", "extreme", "insane",
                    or a value for an average desired bitrate and depending
                    on the value specified, appropriate quality settings will
                    be used.
                    "--preset help" gives more info on these

```

---

