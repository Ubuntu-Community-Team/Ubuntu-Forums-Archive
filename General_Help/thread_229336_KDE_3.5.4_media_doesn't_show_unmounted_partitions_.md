---
title: "KDE 3.5.4 media:/ doesn't show unmounted partitions when mounted"
date: 2006-08-04
forum: General Help
---

### Post by Jucato on 2006-08-04
I know my title sounds a bit weird, but that's just exactly what I've noticed. After successfully upgrading to KDE 3.5.4, the media:/ KIO slave no longer shows unmounted media initially. Only those media that are mounted at boot are visible.

However, once you do mount those other unmounted partitions, they still do not appear in media:/, even if they do appear in the /media/ directory.

Removable media (CDs, USBs, etc.), on the other hand, still behave normally.

Is anyone having a similar problem?

---

### Post by fdoving on 2006-08-06
Yes, I have the same problem. KDE 3.5.4 on edgy.

- Frode / uniq @ freenode

---

### Post by fdoving on 2006-08-06
I think I have found a workaround for our problem.

It seems to be a HAL policy issue now that KDE fully use HAL for all media stuff.

Edit this file:
/usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi

This is what i've changed:

I duplicated this line, uncommented the original, and set it to 'true'.
```

    <merge key="storage.policy.should_mount" type="bool">true</merge>
<!-- DEFAULT    <merge key="storage.policy.should_mount" type="bool">false</merge> -->

```

Here is the whole section, after i've done my modification, with a comment from HAL packagers why this is set to false by default. 

```

  <!-- Dont want to mount non-hotpluggable fixed disks since ideraid
       detection isnt complete as hald wrongly detects e.g. partitions
       from some IDE RAID controllers -->
  <device>
    <match key="storage.hotpluggable" bool="false">
      <match key="storage.removable" bool="false">
    <merge key="storage.policy.should_mount" type="bool">true</merge>
<!-- DEFAULT    <merge key="storage.policy.should_mount" type="bool">false</merge> -->
      </match>
    </match>
  </device>

  <device>
    <match key="storage.media_check_enabled" bool="true">
      <append key="info.addons" type="strlist">hald-addon-storage</append>
    </match>
  </device>

```



Hope this helps you.

- Frode / uniq @ freenode.

---

### Post by Jucato on 2006-08-06
Hi uniq!

Didn't seem to work.

The only way I can work around this is to have all partitions mounted at boot. It seems that if a partition was not mounted at boot, it will not display in media:/...

---

