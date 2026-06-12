---
title: "Frozen/Black screen after suspend"
date: 2016-03-09
forum: General Help
---

### Post by jorge31 on 2016-03-09
Hi,

I have a HP Spectre laptop with 14.04 installed. After suspend (closing and opening the lid) I first saw vertical colored lines. I did a bit of searching and change my /etc/grub/default to include
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
```

This removed the vertical lines but instead replaced them with a black screen (my keyboard caps lock would respond to toggles) but my screen never came up. I then again changed grub default to
```
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"
```

After this change my computer will sometimes come back up after a suspend but not always. It also takes a few seconds to come up which seems like it may be a bit long. Any ideas as to what I can do as a permanent solution?

Thanks,

Below is some graphics card info.
```
$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Sky Lake Integrated Graphics (rev 07)


```

---

