---
title: "I found tesseract4.0 crashed when I use Intel i7-8700 CPU with Ubuntu 18.04."
date: 2018-07-03
forum: General Help
---

### Post by drproy2k on 2018-07-03
[COLOR=#3D3D3D][FONT=intel-clear]Hi,[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]I found tesseract4.0 crashed when I use Intel i7-8700 CPU with Ubuntu 18.04.[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]tesseract4.0 is a OCR open source. ( [GitHub - tesseract-ocr/tesseract: Tesseract Open Source OCR Engine (main repository)]("https://communities.intel.com/external-link.jspa?url=https%3A%2F%2Fgithub.com%2Ftesseract-ocr%2Ftesseract")  )[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]I used pyocr for wrapping lib for tesseract.[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]Here is the way I use. ( [PyOCR | python Tutorial]("https://communities.intel.com/external-link.jspa?url=http%3A%2F%2Fwww.riptutorial.com%2Fpython%2Fexample%2F28811%2Fpyocr"), [http://www.riptutorial.com/python/example/28811/pyocr](http://www.riptutorial.com/python/example/28811/pyocr) )[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]When I call below function several times, it is OK.[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]txt = tool.image_to_string(
  Image.open('test.png'),
  lang=lang,
  builder=pyocr.builders.TextBuilder()
)[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]But, when I call it over one hundred times, crash happens and my desk-top PC is reboot.[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]By the way,[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]when I use i5-8400 CPU, sometimes error message is shown, but no crash happens.[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]And, one more thing,[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]Tesseract uses AVX and SSE, and when I disable them and re-test it, everything is fine. Never crash happens. No error message is shown.[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]But, you know, running speed is not good.[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]I think i7-8700 CPU has something with AVX and SSE function which is different from those of i5-8400.[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]Is there anybody who has a similar experience to me?[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]Is there any solution I can use tesseract with i7-8700K CPU turning on AVX and SSE.[/FONT][/COLOR]

---

