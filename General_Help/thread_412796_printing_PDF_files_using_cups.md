---
title: "printing PDF files using cups"
date: 2007-04-18
forum: General Help
---

### Post by Tahir on 2007-04-18
Hello,

I am having problems with printing with printing this VIM pdf file:

tnerual.eriogerg.free.fr/vimqrc.pdf

I first used the command

lp vimqrc.pdf

and it printed wrongly and then I used 

lp -o landscape vimqrc.pdf

and it STILL printed it wrongly (but differently).

Can someone please figure something out for me because this is making me feel bad :-{  
Thanks.  Please try these commands on your own printer and see if it works.

---

### Post by Tahir on 2007-04-18
That landscape pdf file was causing me problems I must say.  The answer given to me by some nice person on the CUPS forum is that I 

1/ install xpdf

2/ xpdf comes with pdftops which I use to convert the pdf to a ps file and then print as usual.

---

