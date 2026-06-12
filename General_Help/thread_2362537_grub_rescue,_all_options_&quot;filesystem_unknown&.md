---
title: "grub rescue, all options &quot;filesystem unknown&quot;"
date: 2017-05-30
forum: General Help
---

### Post by xretrox on 2017-05-30
I left my computer with family for a weekend, and it turns out they forced off the machine via power button.

I now get "error: no such device xxxxxxx" with a grub rescue prompt. Using ls I checked I the filesystem of all partitions, and all returned "unknown filesystem"

I can't boot off any partitions, what steps do I take next? Is there any hope?

Thanks

---

### Post by cariboo on 2017-05-30
try to boot in recovery mode, and select root from the menu, once at the prompt type:

```
fsck /dev/sdaX
```

where /dev/sdaX is the partition you have Ubuntu installed on.

---

