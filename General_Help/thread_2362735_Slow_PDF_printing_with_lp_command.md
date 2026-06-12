---
title: "Slow PDF printing with lp command"
date: 2017-06-01
forum: General Help
---

### Post by varjla on 2017-06-01
Hello all:

This is my first post, so hope I'm not wrong posting my question in General Help.


After few working around, I was able to print normal text files with "lp" command. I was able to print selecting some options (double sided print, media size, paper tray input, etc.)
I got the linux drivers for my machines here (PPD files): [https://www.openprinting.org/download/PPD/](https://www.openprinting.org/download/PPD/)
Now I have a little problem: When I send a .pdf file to the printer (Ricoh MP Aficio 1106 EX connected by TCP-IP), the print goes slow, getting +30 seconds to send the file to the printer. The .txt files print at the moment I send them. Do you have any idea how to solve it?
I tryied change the socket of the machine to 9100 port, but that only generates errors. I used wireshark, but got zero aditional info, because the packages started to send at same time I execute lp command.


IMPORTANT NOTE TO NEWBIE: [COLOR=#ff0000]NEVER USE[/COLOR]:
 ```
[COLOR=#ff0000]lp -o raw /absolute/path/to/file.pdf[/COLOR]
```
It prints +400 pages with only ONE line printed in each page...

FIRST STEP:
I tryied using LPR command, instead LP:
```
lpr -sPrinterIP /absolute/path/to/file.pdf
```
But works slowly too.


SECOND STEP:
I installed qz-tray, a kind of print server/API. When I try PDF demo, it prints slow too.


THIRD STEP:

 I tryied now with default PDF viewer (EVINCE) because I though I have a lack of memory and printed the same file. It worked well, at normal speed.


FORTH STEP:

 I tryied some other drivers (generic and recomended by the printer maker ones), same speed.


I think is a problem processing the file, transforming .pdf to print order, but I'm really unfamiliar with .PDF printing. Hope you can help me. Thanks a lot.

FIFTH STEP:

I tryied to compress the 145236Bytes(145KB) pdf file with pdftk:
```
pdftk Binder1copia.pdf output fixed.pdf
```

The result, slower than before... because the file now weigths 164909bytes (164KB)?


I tryed to compress the file with qpdf:

```
qpdf --linearize Binder1copia.pdf output.pdf
```

Same result as pdftk option. I guess compressing is not the solution. (the PDF only gets more bytes doing this)





SIXTH STEP: CUPS filtering

I found this link: [https://en.opensuse.org/SDB:Using_Your_Own_Filters_to_Print_with_CUPS](https://en.opensuse.org/SDB:Using_Your_Own_Filters_to_Print_with_CUPS). I think is part of my problem, but cannot confirm it. Could anyone explain me (for newbies) what the heck is filtering? Thanks again.


SEVENTH STEP: driver check and ghostcript issue

After so much work around this problem (and infinite paper loss). I checked next trial: When I print a text-only-pdf file, the printing goes as fast as printer can (+-8secs). But when I send a file with images, lp printing got about 30seconds to process file before send packages to printer (checked with wireshark)

I readed the recomended-by-Ricoh PPD driver file(PXL driver, because my machine didn't have postcript), and the only thing I guess can do that is this line:


*%========== Ghostscript Command line ==========


*FoomaticRIPCommandLine: "(printf &apos;\033%%-12345X@PJL\n@PJL JOB\n@PJL SET COPIES=&copies;\n&apos;%G|perl -p -e &quot;s/\x26copies\x3b/1/&quot;);
(gs -q -dBATCH -dPARANOIDSAFER -dNOPAUSE -dNOMEDIAATTRS -dNOINTERPOLATE %B%A%C %D%E | perl -p -e &quot;s/^\x1b\x25-12345X//&quot; | perl -p -e &quot;s/\xc1\x01\x00\xf8\x31\x44/\x44/g&quot;);
(printf &apos;@PJL\n@PJL EOJ\n\033%%-12345X&apos;)"
*End

About this problem I just found this article: [https://lists.linuxfoundation.org/pipermail/printing-foomatic/2012/002791.html](https://lists.linuxfoundation.org/pipermail/printing-foomatic/2012/002791.html) This confirms my idea: PPD file is rendering all files with Ghostcript.

Any Idea?

---

### Post by varjla on 2017-06-09
Found a solution: Change the RICOH recomended driver (PPD not optimized) to a GutenPrint Driver, that is much more efficient.

Hope this helps to anyone ;)

---

