---
title: "HOWTO: batch convert ODT to PDF while retaining modification times"
date: 2019-03-20
forum: General Help
---

### Post by mattdawolf on 2019-03-20
I have no idea where to put this...

What is the best way, either in shell script or external conversion service, how to batch convert ODT to PDF while retaining the modification times of the ODT file?

---

### Post by Impavidus on 2019-03-21
I don't know about exporting odt to pdf, but you can fix modification or access times with touch. Assuming you keep the original odt alongside the pdf, what I would recommend anyway, use```
touch --reference=file.odt file.pdf
```

I use the word "exporting" instead of "converting" and recommend to keep the original, because odt and pdf are very different file formats. odt contains the logical structure of the document, pdf only the visual formatting. Where odt says```
blah blah blah.<end paragraph>
<begin header>This is a header<end header>
<begin paragraph>Blah blah blah
```pdf says```
blah blah blah.
<insert 16 points of vertical whitespace>
<change font to size 16>
This is a header
<insert 12 points of vertical whitespace>
<change font size to 10>
Blah blah blah
```(I omitted the instructions for horizontal spacing.)

Having said that, odt can contain visual formatting instructions as well and many people use those, which leads to better round trip conversions to pdf, but also less consistent typesetting.

---

