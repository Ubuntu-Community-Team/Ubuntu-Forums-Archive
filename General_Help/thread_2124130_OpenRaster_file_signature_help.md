---
title: "OpenRaster file signature help"
date: 2013-03-09
forum: General Help
---

### Post by monkeyPlanet on 2013-03-09
Hi,
I am trying to recover some deleted .ora files and cant seem to figure out the file signature needed for Photorec or Scalpel.
I have made some .ora files with MyPaint and some with Krita both 8 bit and 16 bit. I am posting the top of the files as seen in Okteta. 
As you can see the files made by both apps look a bit different. Do I need to write different signatures in photorec.sig for MyPaint and Krita .ora files ?

Any help in figuring out the signature would be great.

```
**MyPaint**
0000:0000 | 50 4B 03 04  14 00 00 00  00 00 00 00  21 00 C7 9A | PK..........!.Ç.
0000:0010 | F0 8C 10 00  00 00 10 00  00 00 08 00  00 00 6D 69 | ð.............mi
0000:0020 | 6D 65 74 79  70 65 69 6D  61 67 65 2F  6F 70 65 6E | metypeimage/open
0000:0030 | 72 61 73 74  65 72 50 4B  03 04 14 00  00 00 00 00 | rasterPK........
0000:0040 | 44 41 6A 42  1B EE 33 56  79 89 02 00  79 89 02 00 | DAjB.î3Vy...y...
0000:0050 | 11 00 00 00  64 61 74 61  2F 6C 61 79  65 72 30 30 | ....data/layer00
0000:0060 | 30 2E 70 6E  67 89 50 4E  47 0D 0A 1A  0A 00 00 00 | 0.png.PNG.......


**MyPaint**
0000:0000 | 50 4B 03 04  14 00 00 00  00 00 00 00  21 00 C7 9A | PK..........!.Ç.
0000:0010 | F0 8C 10 00  00 00 10 00  00 00 08 00  00 00 6D 69 | ð.............mi
0000:0020 | 6D 65 74 79  70 65 69 6D  61 67 65 2F  6F 70 65 6E | metypeimage/open
0000:0030 | 72 61 73 74  65 72 50 4B  03 04 14 00  00 00 00 00 | rasterPK........
0000:0040 | 58 41 6A 42  50 D0 C1 59  4D 97 01 00  4D 97 01 00 | XAjBPÐÁYM...M...
0000:0050 | 11 00 00 00  64 61 74 61  2F 6C 61 79  65 72 30 30 | ....data/layer00
0000:0060 | 30 2E 70 6E  67 89 50 4E  47 0D 0A 1A  0A 00 00 00 | 0.png.PNG.......


**Krita**
0000:0000 | 50 4B 03 04  14 00 00 00  00 00 47 5F  47 FC C7 9A | PK........G_GüÇ.
0000:0010 | F0 8C 10 00  00 00 10 00  00 00 08 00  00 00 6D 69 | ð.............mi
0000:0020 | 6D 65 74 79  70 65 69 6D  61 67 65 2F  6F 70 65 6E | metypeimage/open
0000:0030 | 72 61 73 74  65 72 50 4B  03 04 14 00  00 00 08 00 | rasterPK........
0000:0040 | 47 5F 47 FC  18 A4 3C 2E  64 4E 00 00  8F 65 75 00 | G_Gü.¤<.dN...eu.
0000:0050 | 0F 00 00 00  64 61 74 61  2F 6C 61 79  65 72 30 2E | ....data/layer0.
0000:0060 | 70 6E 67 EC  DD 7B FC 97  F3 FD C7 F1  6F A4 48 A9 | pngìÝ{ü.óýÇño¤H©


**Krita**
0000:0000 | 50 4B 03 04  14 00 00 00  00 00 47 5F  47 FC C7 9A | PK........G_GüÇ.
0000:0010 | F0 8C 10 00  00 00 10 00  00 00 08 00  00 00 6D 69 | ð.............mi
0000:0020 | 6D 65 74 79  70 65 69 6D  61 67 65 2F  6F 70 65 6E | metypeimage/open
0000:0030 | 72 61 73 74  65 72 50 4B  03 04 14 00  00 00 08 00 | rasterPK........
0000:0040 | 47 5F 47 FC  AD 90 B2 59  02 CC 08 00  19 C6 EA 00 | G_Gü*.²Y.Ì...Æê.
0000:0050 | 0F 00 00 00  64 61 74 61  2F 6C 61 79  65 72 30 2E | ....data/layer0.
0000:0060 | 70 6E 67 EC  DD 07 94 95  D5 D9 36 E0  E7 4C A7 63 | pngìÝ...ÕÙ6àçL§c
```

---

