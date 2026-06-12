---
title: "ibus bug? + support for traditional chinese?"
date: 2013-06-28
forum: General Help
---

### Post by LudoTW on 2013-06-28
On a freshly installed 13.04, after updating languages and adding chinese and Japanese, ibus doesn't work anymore. That is in a terminal or in a text editor, pressing ctrl space do switch to another input language but with no effect on the typing: the foreign language input icon changes back to the keyboard.
I get this message in the consol:
```
IBUS-WARNING **: Process Key Event failed: GDBus.Error:org.gtk.GDBus.UnmappedGError.Quark._g_2dio_2derror_2dquark.Code18: The connection is closed.

```

Should I unsinstal ibus, or?

Also, how to get bopomofo to input tradtional chinese?

---

### Post by dino99 on 2013-06-28
are you using ubuntukylin ?  [https://wiki.ubuntu.com/UbuntuKylin](https://wiki.ubuntu.com/UbuntuKylin)
and ibus-pinyin should be used (ibus-pinyin is a IBus based IM engine for Chinese.)

[http://www.pinyinjoe.com/linux/ubuntu-10-chinese-input-pinyin-chewing.htm](http://www.pinyinjoe.com/linux/ubuntu-10-chinese-input-pinyin-chewing.htm)

---

### Post by LudoTW on 2013-07-01
Thanks dino99 for some info. But I don't want only chinese input, nor do I want China specific information. o while I didn't know about ubuntukylin but it doesn't seem it fits my need. I'm not a mandarin native speaker but need mandarin and japanese input from time to time (more often than not).

My problem with ibus not inputing any mandarin (or japanese) in a text editor still remain, I suspect it to be a crash.

---

