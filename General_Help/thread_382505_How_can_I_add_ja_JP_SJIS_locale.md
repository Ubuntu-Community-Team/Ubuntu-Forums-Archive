---
title: "How can I add ja_JP SJIS locale?"
date: 2007-03-12
forum: General Help
---

### Post by D-- on 2007-03-12
Hi, I've read some guides and had no luck.

```

d@cinnamon:~$ cat /usr/share/i18n/SUPPORTED | grep ja
ja_JP.EUC-JP EUC-JP
ja_JP.UTF-8 UTF-8

```

According to that, the SJIS locale is not supported. EUC is. I tried running:

```

d@cinnamon:~$ sudo dpkg-reconfigure locales
Generating locales...
  en_AU.UTF-8... up-to-date
  en_BW.UTF-8... up-to-date
  en_CA.UTF-8... up-to-date
  en_DK.UTF-8... up-to-date
  en_GB.UTF-8... up-to-date
  en_HK.UTF-8... up-to-date
  en_IE.UTF-8... up-to-date
  en_IN.UTF-8... up-to-date
  en_NZ.UTF-8... up-to-date
  en_PH.UTF-8... up-to-date
  en_SG.UTF-8... up-to-date
  en_US.UTF-8... up-to-date
  en_ZA.UTF-8... up-to-date
  en_ZW.UTF-8... up-to-date
  ja_JP.UTF-8... up-to-date
  zh_CN.GB18030... up-to-date
  zh_CN.GB2312... up-to-date
  zh_CN.GBK... up-to-date
  zh_CN.UTF-8... up-to-date
  zh_HK.Big5... up-to-date
  zh_HK.UTF-8... up-to-date
  zh_SG.UTF-8... up-to-date
  zh_TW.Big5... up-to-date
  zh_TW.UTF-8... up-to-date
Generation complete.

```

As you can see, ja_JP SJIS is unavailable there too.

How can I add this locale to my Ubuntu system? I haven't found a clear guide anywhere. I tried running localepurge but it's not in there either.

Thanks!

**Edit:** I answered my own question (wow, that's happening for every single thread I post in lately) and extrapolated on it to make a whole CJK wine launcher.

If you need to add SJIS or other locales you are missing, follow Step 1 of my Wine CJK HowTo. [http://ubuntuforums.org/showthread.php?t=383628](http://ubuntuforums.org/showthread.php?t=383628)

---

### Post by johnraff on 2007-06-11
Hi, I didn't want to mess up the wine thread so I've posted my noobish question here:
do I need to "add a ja_JP SJIS locale" in order to edit files with SJIS encoding (Japanese web pages) or is it just a question of finding the right editor?

(SciTE will *display* sjis OK but editing is a ghastly mess. Right now I have to type the content into a UTF-8 page and copy-and-paste it into the SJIS page.)

---

### Post by D-- on 2007-06-12
Good question! And the answer is ........... I have absolutely no idea :(

I think in Gedit, when you open a file, you can manually enter a locale in the drop-down box. Punch in Shift-JIS and see if it works. If it doesn't, then try adding the locale and see what happens.

---

### Post by johnraff on 2007-06-13
Aah that means installing Gedit, which I think might bring a lot of Gnome stuff into this old Xubuntu box...

It might well work OK though, because I've now found that Leafpad will edit SJIS OK if you call it up with an encoding option:
```
 leafpad --codeset=SJIS *filename* 
```

I've tried a whole slew of editors in the last 24 hours but none of them really appealed, and most of them didn't (appear to) support SJIS. Leafpad will do for now, though I'd prefer a bit more sophistication really: multitabs, highlighting etc.

Still, times when I'm editing the *content*, and need SJIS, tend to be different from when I'm playing with the *code*, for which SciTE will work fine as it *displays* the SJIS OK.

Thanks for your suggestion: I might well try installing Gedit anyway. :)
btw does the system make any distinction between SJIS, sjis, Shift_JIS and Shift-JIS ???

(Eager to hear if anyone has found the ideal editor for Japanese web pages, css, php etc. ... )

---

### Post by johnraff on 2007-06-13
Yeh Gedit works without having to add a sjis locale. (It was a 30MB install though...)
The "open" dialogue box has a "character encoding" selection at the bottom and I could add "Japanese (SHIFT_JIS)" to the options with "add or remove". Supports tabs and other things I wanted too so might turn out to be the one to use. :)

---

