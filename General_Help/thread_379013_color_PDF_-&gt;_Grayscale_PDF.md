---
title: "color PDF -&gt; Grayscale PDF"
date: 2007-03-08
forum: General Help
---

### Post by rlgc79 on 2007-03-08
Hello, 

Is there a way to convert a color PDF file to a grayscale PDF file with Linux? 

I've been trying to use KPDF  with the option "print to PDF file". When I choose grayscale  in the properties menu of the printer, two problems happen
1) The orientation of file is landscape and the resulting file becomes portrait, thus cutting part of my slide.
2) The conversion from color  to grayscale does not work. The resulting file has colors!

Is it a bug? Are there alternatives?

I've already tried evince but this program does not give me option to choose grayscale...

Best,

---

### Post by rlgc79 on 2007-03-08
Answering myself.

I found a solution. Two commands:

1) pdf2ps -sDEVICE=psgray <filename>
2) ps2pdf <filename>

<filename> is now grayscale :)

To see a list of available devices (-sDEVICE), type
gs -h

Cheers

---

