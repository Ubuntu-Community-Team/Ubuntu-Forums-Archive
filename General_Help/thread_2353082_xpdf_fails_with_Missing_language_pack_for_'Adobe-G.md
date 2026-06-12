---
title: "xpdf fails with Missing language pack for 'Adobe-GB1' mapping"
date: 2017-02-18
forum: General Help
---

### Post by u._newbie on 2017-02-18
The command
  $ xpdf chinese_file.pdf
fails with
  Syntax Error: Missing language pack for 'Adobe-GB1' mapping
  Syntax Error: Unknown font tag 'C2_0'
  Syntax Error (6256466): No font in show

On the other hand, evince works well on this file.
An strace shows that xpdf opens /nameToUnicode, /cidToUnicode,
/unicodeMap, /cMap, which sounds like a bug. Probably some prefix
is NULL here and should have been /usr/share/poppler.
This is xenial. Is this a xenial bug? Is the prefix set in some configuration file?

As an aside, /usr/share/xpdf/xpdfrc-chinese-simplified contains the line
fontFileCC      Adobe-GB1       /usr/share/fonts/truetype/wqy/wqy-zenhei.ttc
while no wqy-zenhei.ttc was installed. However, installing that font does not help.
In fact the strace of xpdf does not show any font file access.

---

