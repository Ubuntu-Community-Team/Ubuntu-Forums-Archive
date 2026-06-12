---
title: "Tesseract language add"
date: 2022-09-01
forum: General Help
---

### Post by Joe_Linux on 2022-09-01
Will someone please help me add English to Tesseract. I need a step by step if possible . 
I included a screenshot of the error. I also am trying to use Gimagereadr as a front end for Tesseract.
Thank you

---

### Post by grahammechanical on 2022-09-01
According to the tesseract man page English is the default.

> **-l** *LANG*
**-l** *SCRIPT*
 The language or script to use. If none is specified, eng (English) is assumed. Multiple languages may be specified, separated by plus characters. Tesseract uses 3-character ISO 639-2 language codes (see [**LANGUAGES AND SCRIPTS**]("https://github.com/tesseract-ocr/tesseract/blob/main/doc/tesseract.1.asc#LANGUAGES")).

 

See Lanuages and Scripts

> To recognize some text with Tesseract, it is normally necessary to specify the language(s) or script(s) of the text (unless it is English text which is supported by default) using **-l** *LANG* or **-l** *SCRIPT*.

[https://github.com/tesseract-ocr/tesseract/blob/main/doc/tesseract.1.asc#languages](https://github.com/tesseract-ocr/tesseract/blob/main/doc/tesseract.1.asc#languages)


Regards

---

### Post by Joe_Linux on 2022-09-01
First thank you for responding. I wonder why I am getting the error message.

---

### Post by dragonfly41 on 2022-09-02
Probably the issue is with the frontend you are using rather than Tesseract.

---

### Post by Joe_Linux on 2022-09-02
dragonfly41
Is there a way to correct this ? My reason for using Gimagereader  command line interface skills could be better.
Are you able to suggest another (GUI) frontend for Tesseract or a way to correct this ? Thank you

---

### Post by dragonfly41 on 2022-09-02
Tesseract is the backend engine for a number of tools (depending on what you are trying to achieve).

[https://nanonets.com/blog/ocr-with-tesseract/](https://nanonets.com/blog/ocr-with-tesseract/)

A simple GUI I use for various custom automation tasks is Actiona.

But Python3 might be more general for you.

---

