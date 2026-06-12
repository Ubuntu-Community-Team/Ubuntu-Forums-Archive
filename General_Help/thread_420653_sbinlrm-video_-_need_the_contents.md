---
title: "/sbin/lrm-video - need the contents"
date: 2007-04-23
forum: General Help
---

### Post by skd5aner on 2007-04-23
Can someone please post what is in this file: /sbin/lrm-video

I don't have it, and it's causing me some headaches with the nvidia driver.

Thanks!

---

### Post by skd5aner on 2007-04-23
Actually, I found it myself by re-installing the linux-restricted-modules temporarily:

```
 more /sbin/lrm-video
#!/bin/sh

PATH=/sbin:/bin

MODULE="$1"
shift

if [ "$MODULE" = "nvidia" ]; then
        if [ -e /lib/linux-restricted-modules/.nvidia_legacy_installed ]; then
                MODULE="nvidia_legacy"
        fi
        if [ -e /lib/linux-restricted-modules/.nvidia_new_installed ]; then
                MODULE="nvidia_new"
        fi
        XORG="nvidia";
elif [ "$MODULE" = "nvidia_legacy" -o "$MODULE" = "nvidia_new" ]; then
        XORG="nvidia";
elif [ "$MODULE" = "fglrx" ]; then
        XORG="fglrx";
fi

if cat /etc/X11/xorg.conf 2>/dev/null | \
  sed -n -e '/^[ \t]*section[ \\t]*"device"/I,/^[ \t]*endsection/I{/^[ \t]*driver[ \t]*/I{s/^[ \t]*driver[ \t]*"*//I;s/"*[ \t]*$//
;p}}' | \
  grep -q -w $XORG; then
        modprobe --ignore-install -Qb $@ $MODULE
else
        echo "Not loading $MODULE module; not used in /etc/X11/xorg.conf" 1>&2
fi

```

Maybe this will help some other people, as I've seen several posts around google referencing this issue when trying to get their nvidia drivers working correctly.

---

