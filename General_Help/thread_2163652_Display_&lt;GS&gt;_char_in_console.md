---
title: "Display &lt;GS&gt; char in console"
date: 2013-07-19
forum: General Help
---

### Post by jo138 on 2013-07-19
I hava a barcode reader connected through USB.
The barcode I read had a invisible character : ascii 29 - GS
If I scan the barcode on a windows pc in the command prompt I get : 255541433800009312345^]39001
If I scan the barcode on a ubuntu console I get : 255541433800009312345$39001

Somebody knows to get the escape code and not the dollar sign ? I need this to decode the barcode in a java program.

---

### Post by dino99 on 2013-07-19
is your system using utf-8 ? (it should)

---

### Post by brentcarter on 2013-12-15
This barcode reading and decoding library may be helpful to you. It supports muntiple linear and 2D barcodes (such as [[COLOR=#000000]Identcode[/COLOR]]("http://www.rasteredge.com/how-to/vb-net-imaging/barcode-reading-identcode/"), [[COLOR=#000000]UPC-A[/COLOR]]("http://www.rasteredge.com/how-to/vb-net-imaging/barcode-reading-upca/"), QR Code and PDF-417) reading in an easy way.

---

