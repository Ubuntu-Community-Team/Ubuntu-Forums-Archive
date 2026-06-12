---
title: "Problem with purge-old-kernels script on UEFI systems and fix"
date: 2017-02-03
forum: General Help
---

### Post by Keith_Helms on 2017-02-03
I built a new PC back in November and installed Xubuntu 16.04 on it in UEFI mode.  I noticed I was up to 7 kernel versions after the latest update, so I ran the purge-old-kernels script which I had set to keep the last 3 versions.  It deleted all the kernels except the live one.  I investigated what went wrong and found that on UEFI systems, two vmlinuz files get created for each kernel version.  
```

/boot/vmlinuz-4.4.0-62-generic  /boot/vmlinuz-4.4.0-62-generic.efi.signed

```

The result was each kernel got counted as 2 kernels in the purge script and keeping 3 really meant keeping 1 1/2 which meant that the latest kernel was kept, the -1 kernel was deleted once, and older kernels were deleted twice (just to make sure!).

The offending line in the purge-old-kernels script is
```

CANDIDATES=$(ls -tr /boot/vmlinuz-* | head -n -${KEEP} | grep -v "$(uname -r)$" | cut -d- -f2-3 | awk '{print "linux-image-" $0 "-generic linux-headers-" $0 "-generic linux-headers-" $0}' )

```
My fix to make it work correctly was to add a grep to that line to filter out the efi.signed kernel images:
```

CANDIDATES=$(ls -tr /boot/vmlinuz-* | grep -v 'efi.signed' | head -n -${KEEP} | grep -v "$(uname -r)$" | cut -d- -f2-3 | awk '{print "linux-image-" $0 "-generic linux-headers-" $0 "-generic linux-headers-" $0}' )

```

---

