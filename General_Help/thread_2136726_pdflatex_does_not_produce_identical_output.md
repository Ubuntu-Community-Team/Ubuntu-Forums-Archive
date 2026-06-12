---
title: "pdflatex does not produce identical output"
date: 2013-04-18
forum: General Help
---

### Post by hwttdz on 2013-04-18
I've noticed that running pdflatex on the same file twice produces two files which differ in terms of md5sum, does anyone happen to know why this is the case? or better yet if there is a way to get it to produce the same output each time?

---

### Post by Impavidus on 2013-04-18
The creation time and date are hidden somewhere in the pdf. The visible contents are the same.

```

$ cat hello.tex
\documentclass{article}
\begin{document}
Hello world!
\end{document}
$ pdflatex hello
...
$ mv hello.pdf hello2.pdf
$ pdflatex hello
...
$ diff -a hello.pdf hello2.pdf 
109,110c109,110
< /CreationDate (D:20130418191554Z)
< /ModDate (D:20130418191554Z)
---
> /CreationDate (D:20130418191530Z)
> /ModDate (D:20130418191530Z)
131c131
< /ID [<7042DC44D58E605583690E5A59B90A01> <7042DC44D58E605583690E5A59B90A01>] >>
---
> /ID [<BEE687CFFEE88AC23B4208BC614483FB> <BEE687CFFEE88AC23B4208BC614483FB>] >>

```

---

### Post by hwttdz on 2013-04-18
> **Impavidus said:**
> The creation time and date are hidden somewhere in the pdf. The visible contents are the same.

Thanks, a simple:
```
	perl -pi -e "s/.*?ModDate.*/\/ModDate (D:20130418152511-04'00')/" $(BASENAME).pdf
	perl -pi -e "s/.*?CreationDate.*/\/CreationDate (D:20130418152541-04'00')/" $(BASENAME).pdf
	perl -pi -e "s/.*?\/ID.*/\/ID [<0535B734E397B655F1D0DD37FD8A8CF9> <0535B734E397B655F1D0DD37FD8A8CF9>]/" $(BASENAME).pdf
```

added to my makefile is enough to ensure that identical input produces identical output.

---

