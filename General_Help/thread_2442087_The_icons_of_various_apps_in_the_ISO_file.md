---
title: "The icons of various apps in the ISO file"
date: 2020-04-29
forum: General Help
---

### Post by hariks0 on 2020-04-29
Hi,

I installed Ubuntu 20.04 two days back. I instantly fell in love with the ***Install Ubuntu*** icon at the desktop while installing.

Where can I get it from the ISO file or forums for using somewhere else?

Thanks in advance.

---

### Post by ActionParsnip on 2020-04-29
If you open a terminal in the live CD and run:
```

cd ~/Desktop; grep -i icon ./*

```

You can see the icon file name. If it doesn't give you the absolute path then run:

```

sudo updatedb; locate filename.png

```

Obviously change filename.png for the actual name of the file. This should do it

---

### Post by hariks0 on 2020-04-29
> **ActionParsnip said:**
> If you open a terminal in the live CD and run:
```

cd ~/Desktop; grep -i icon ./*

```

You can see the icon file name. If it doesn't give you the absolute path then run:

```

sudo updatedb; locate filename.png

```

Obviously change filename.png for the actual name of the file. This should do it

Thank you very much for the help. I found the icon files in the following locations:
/rofs/usr/share/icons/Yaru/256x256@2x/apps
/snap/gtk-common-themes/1506/share/icons/Yaru/256x256@2x/apps

The icon file name is ubiquity and is attached for anyone who may need it to customise the Activities button.

[ATTACH=CONFIG]285680[/ATTACH]

Thank you once again.

---

