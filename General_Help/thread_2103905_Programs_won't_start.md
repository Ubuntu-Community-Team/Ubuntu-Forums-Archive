---
title: "Programs won't start"
date: 2013-01-11
forum: General Help
---

### Post by Typhon on 2013-01-11
About an hour ago most of the programs on my Xubuntu 12.10 suddenly stopped working. The "funny" thing is I didn't do anything to cause this, because before everything had worked just fine. Even XFCE won't start. I use Openbox so this isn't such a problem. 

If I run programs in terminal, most of the time I get a segmentation fault error, or a fontconfig warning:
```
Fontconfig warning: "/etc/fonts/conf.d/50-user.conf", line 9: reading configurations from ~/.fonts.conf
Fontconfig warning: "msfonts-rules.conf", line 23: Having multiple values in <test> isn't supported and may not work as expected.
```

Some of the programs that **won't start**: Firefox, PCmanFM file manager, Thunar, most of the XFCE apps, Deluge, etc.

Some of the programs that **work**: Opera, Libre Office, Blender, Wine apps, Xterm ...

I have no idea how to solve this. Any help will be appreciated!

---

### Post by weryl on 2013-01-11
Could you try deactivating your ~/.fonts.conf:

```
mv ~/.fonts.conf ~/.fonts.conf.old
```

...and try opening thunar?

---

### Post by Typhon on 2013-01-11
It doesn't help. I still get a segmentation fault error. I also tried deactivating "/etc/fonts/conf.d/50-user.conf" and "msfonts-rules.conf" and it still didn't work.

---

