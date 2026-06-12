---
title: "Cannot write or display IPA (international phonetic alphabet) on libreoffice 6"
date: 2019-03-13
forum: General Help
---

### Post by Karolina.K on 2019-03-13
Hello, 

I am currently studying linguistics, and last semester I studied phonetics. I have so far been handwriting all my phonetics, but my next task requires me to write it on computer. 
I have followed numerous guides online on how to install IPA and write it, but none of it works for me.. I cannot even display IPA correctly when I open a document containing IPA.

I would very much appreciate some help.
Thanks in advance.

My system is Dell xps 9360 Ubuntu 18.10
(in the future I plan to use LaTex but it seems to be quite a learning curve..)

/Karolina

---

### Post by The Cog on 2019-03-13
If you can find an application called Character Map, this is really the go-to place for characterset info. I see there is a unicode block called IPA Extensions which may hold the characters you want. You can double-click a character and it then goes into the text box at the bottom, where you can copy into the paste buffer. 

You can also see the unicode value, and knowing that value, you can directly enter the character into LibreOffice, so for example, a latin letter glottal stop is code 0294 and you can enter this by pressing the keys: Ctrl-Shift-U, 2, 9, 4, Enter.

If there's an easier way, I don't know it.

---

### Post by Karolina.K on 2019-03-13
aha okay thanks, I will try it :) but I also have a problem that it doesn't display IPA from other documents, when I open a document containing IPA it is either squares or turns it into Japanese which is not correct.. can I somehow upload a document with IPA here so others can try it as well? I will show example with pictures, first one is in pdf, how it should look. Next one is how it looks in libreoffice. [https://imgur.com/SqtnZo0](https://imgur.com/SqtnZo0) [https://imgur.com/iffoO8G](https://imgur.com/iffoO8G) [https://imgur.com/CwuBEQi](https://imgur.com/CwuBEQi) As you can see it is not very successful.. :(

---

### Post by Impavidus on 2019-03-13
If you already plan to use LaTeX in the future, I think it's best you switch to that right away. It's not very hard to learn. You only need the very basics to be able to write a decent document. I heard that LaTeX is popular in linguistics, like it is in physics, mathematics, computer sciences and some related fields. You must be able to find someone around you who can teach you the basics.
```
sudo apt install texlive tipa tipa-doc texlive-lang-european
```That will install the basic latex packages, support for IPA, documentation for IPA and support for some European languages like swedish. A complete manual for IPA will be installed in /usr/share/doc/tipa-doc/tipaman.pdf. There are several packages in the Ubuntu repositories with bundles of LaTeX packages.
```
\documentclass{article}
\usepackage{tipa}
\begin{document}
Hello world!

\textipa{/hE"l@U w3:ld/}
\end{document}

```

---

