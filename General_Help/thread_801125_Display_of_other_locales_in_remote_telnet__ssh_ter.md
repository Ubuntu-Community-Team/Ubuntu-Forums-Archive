---
title: "Display of other locales in remote telnet / ssh terminal"
date: 2008-05-20
forum: General Help
---

### Post by snowbug on 2008-05-20
I searched and searched but didn't find the answer. All the posts I found deal with displaying other locales in the graphic environment.

My Ubuntu Hardy server is in English locale. I added Chinese locales after the installation:
```

alan@cupid:~$ cat /var/lib/locales/supported.d/local
en_US.UTF-8 UTF-8
zh_CN.UTF-8 UTF-8
zh_CN.GB18030 GB18030
zh_CN.GBK GBK
zh_CN GB2312
zh_HK.UTF-8 UTF-8
zh_HK BIG5-HKSCS
zh_SG.UTF-8 UTF-8
zh_SG.GBK GBK
zh_SG GB2312
zh_TW.UTF-8 UTF-8
zh_TW BIG5
zh_TW.EUC-TW EUC-TW
```

```

alan@cupid:~$ sudo dpkg-reconfigure locales
Generating locales...
  en_US.UTF-8... up-to-date
  zh_CN.GB18030... up-to-date
  zh_CN.GB2312... up-to-date
  zh_CN.GBK... up-to-date
  zh_CN.UTF-8... up-to-date
  zh_HK.BIG5-HKSCS... up-to-date
  zh_HK.UTF-8... up-to-date
  zh_SG.GB2312... up-to-date
  zh_SG.GBK... up-to-date
  zh_SG.UTF-8... up-to-date
  zh_TW.BIG5... up-to-date
  zh_TW.EUC-TW... up-to-date
  zh_TW.UTF-8... up-to-date
Generation complete.
```

I don't have any graphic desktop installed since this is a server box. I have some music files using Chinese names and I'd like to be able to at least display them correctly when I telnet / ssh in. I don't really need the ability to enter Chinese. But with above locales installed, I still just see "?" for all the Chinese characters.

Does anyone know what else I need to do to solve this?

Thanks!

---

### Post by snowbug on 2008-05-23
Shameless self bump.

---

