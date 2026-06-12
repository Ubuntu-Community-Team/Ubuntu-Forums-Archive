---
title: "Finding broken, damaged, and otherwise unusuable fonts"
date: 2014-12-12
forum: General Help
---

### Post by amber_lux on 2014-12-12
I backed up my fonts.
I restored some fonts, and discovered that some of the "restored" fonts were broken, damaged, or otherwise unusable.

FontMatrix tells me that the fonts are broken, but does not appear to generate a list of broken fonts.
Fontforge will tell me if a font is broken, but that requires loading fonts individually.

Are there are any command line tools that can process a directory of files, and spit out a list of broken, damaged, or otherwise unusable fonts?

---

### Post by bobthebaritone on 2014-12-12
Hi amber_lux,

The immediate tool that comes to mind is to generate a checksum of the good font file and compare it with a checksum of the restored file.
Eg - good font files:
/usr/share/fonts/X11/Type1$ ls -1 c0* | xargs md5sum 
7a48fc6eb89ffc1cad047dd1f9702b6d  c0419bt_.afm
2a8db45b9f7c4b1c05a8e1b4a756b122  c0419bt_.pfb
ccef7a973a16d30de51baefdbed86c70  c0582bt_.afm
42184efc1f64d6f7e46f8987d220eb84  c0582bt_.pfb
7b5121994788e0849dec8b1f054084ac  c0583bt_.afm
a762838c0153fae181c763fed3f1a4c3  c0583bt_.pfb
4586f76d7eb5264c78d82e09e38523c7  c0611bt_.afm
74b17f2bf869baa3c5952e8707984db5  c0611bt_.pfb
488f57dddd05a3372258e8cad860473d  c0632bt_.afm
6c8c18c1e1a138641a52c29f0b878445  c0632bt_.pfb
92831556e6415734e42497fbcc72fa9a  c0633bt_.afm
7f969820a9c1085027a23beb06f6f457  c0633bt_.pfb
bc2710b6ff258b700222ebcb805d7b54  c0648bt_.afm
539b6fed90ef630e9049bc13079bc598  c0648bt_.pfb
1d8d8528c6d260b76c5f5361626bd541  c0649bt_.afm
12369bddf1a14581d11fcdbf86619250  c0649bt_.pfb

Cheers,

Bob

---

### Post by amber_lux on 2014-12-14
Trouble is, I don't have a set of good font files.

---

### Post by schragge on 2014-12-14
I don't know a command-line tool that could check *any* type of font, but there are [t1lint]("http://manpages.ubuntu.com/manpages/utopic/en/man1/t1lint.1.html") for Type 1 fonts, maybe other commands from the same package **lcdf-typetools** for OTF, *ftlint* in the package **freetype2-demos** (lacks documentation, but invoking without parameters gives some information), other commands from that package like *ftvalid*, *ftdump*, *ftview*, *ttdebug* for TTF, *otfdump*, *otfview*, *otflist* from the package **libotf-bin** for OTF (they also lack documentation), [otfinfo](http://manpages.ubuntu.com/manpages/utopic/en/man1/otfinfo.1.html) and other OTF-related command-line tools in the package **otf-trace** (conflict with **lcdf-typetools** and **libotf-bin**), some font-related tools like [ttfdump](http://manpages.ubuntu.com/manpages/utopic/man1/ttfdump.1.html) in the package **texlive-binaries**.

To give you an example:
```

[color=green]$ [/color]ftlint 16 /usr/share/fonts/truetype/droid/*
[color=green]/usr/share/fonts/truetype/droid/DroidKufi-Bold.ttf: OK.
/usr/share/fonts/truetype/droid/DroidKufi-Regular.ttf: OK.
/usr/share/fonts/truetype/droid/DroidNaskh-Bold.ttf: OK.
/usr/share/fonts/truetype/droid/DroidNaskh-Regular.ttf: OK.
/usr/share/fonts/truetype/droid/DroidNaskhUI-Regular.ttf: OK.
/usr/share/fonts/truetype/droid/DroidSansArabic.ttf: OK.
/usr/share/fonts/truetype/droid/DroidSansArmenian.ttf: OK.
/usr/share/fonts/truetype/droid/DroidSans-Bold.ttf: OK.
/usr/share/fonts/truetype/droid/DroidSansEthiopic-Bold.ttf: OK.
/usr/share/fonts/truetype/droid/DroidSansEthiopic-Regular.ttf: OK.
/usr/share/fonts/truetype/droid/DroidSansFallbackFull.ttf: OK.
/usr/share/fonts/truetype/droid/DroidSansGeorgian.ttf: OK.
/usr/share/fonts/truetype/droid/DroidSansHebrew-Bold.ttf: OK.
/usr/share/fonts/truetype/droid/DroidSansHebrew-Regular.ttf: OK.
/usr/share/fonts/truetype/droid/DroidSansJapanese.ttf: OK.
/usr/share/fonts/truetype/droid/DroidSansMono.ttf: OK.
/usr/share/fonts/truetype/droid/DroidSans.ttf: OK.
/usr/share/fonts/truetype/droid/DroidSerif-BoldItalic.ttf: OK.
/usr/share/fonts/truetype/droid/DroidSerif-Bold.ttf: OK.
/usr/share/fonts/truetype/droid/DroidSerif-Italic.ttf: OK.
/usr/share/fonts/truetype/droid/DroidSerif-Regular.ttf: OK.[/color]

```

---

