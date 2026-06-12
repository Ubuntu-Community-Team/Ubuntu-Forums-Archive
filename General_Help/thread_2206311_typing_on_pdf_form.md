---
title: "typing on pdf form"
date: 2014-02-18
forum: General Help
---

### Post by satimis on 2014-02-18
Hi all,

What will be the simple way to type on pdf form without Adobe Acrobat typewriter?  What will be its equivalent on Linux?

Thanks

Rgds
satimis

---

### Post by jp734 on 2014-02-18
I use LibreOffice Draw (Microsoft Visio) a lot to open PDF files and export them back to PDF. I haven't tried LibreOffice Writer (Microsoft Word) yet.

---

### Post by VMC on 2014-02-18
[pdfedit]("http://pdfedit.cz/en/index.html")

---

### Post by satimis on 2014-02-18
> **jp734 said:**
> I use LibreOffice Draw (Microsoft Visio) a lot to open PDF files and export them back to PDF. 

I tried before only codes displayed.  The pdf file is a form.  I need to fill in the content

> 
I haven't tried LibreOffice Writer (Microsoft Word) yet.
Currently I'm using copy/paste method on Writer
- copy the form on Writer
- type the answer on gedit
- use screenshot selecting/copying the answer on gedit
- paste it on Writer and move the same to the item.

It works.  But there is lot of work

satimis

---

### Post by monkeybrain20122 on 2014-02-18
I think a recent enough Okular (and libpoppler) would work, but only for forms that don't have embedded scripts. I don't know the exact version but only remember the version in Ubuntu 12.04 is too old. Also after you fill it out you have to use 'print' or 'save as' for it to be visible to others (save or export won't work) I don't have Okular now so can't be more precise.

Unfortunately no free (open source and costs 0) pdf editor/reader in Linux supports pdf forms that have scripts,--like tax forms that would add up the columns,-- as far as I know.

So the simplest method to handle forms would be running pdf-xchange viewer in Wine. It is very light weight and works perfectly (they claim they test it on wine so there is no need for releasing a Linux native version) Normally I would prefer a native Linux solution but in this case this is the cheapest ($0) and simplest. There is pdf studio which I heard is quite capable and runs natively in linux but costs $$$. To use pdf-xchange viewer you need to install cups-pdf and print the form after filling it. It will be saved in a folder called PDF in your home directory. There was a bug in pdf-xchange viewer that 'save' didn't work. It is probably fixed by now, but it is safer to just print it.

P.S. Someone suggested pdfedit. I don't know if anyone who recommends it has actually used it. I confess I cannot make head or tail from the interface or the manual.

Edited: there are also some web based pdf form fillers, they are OS agnostic. You may try them if you are comfortable with filling forms online.

---

### Post by satimis on 2014-02-19
> **monkeybrain20122 said:**
> - snip -

Edited: there are also some web based pdf form fillers, they are OS agnostic. You may try them if you are comfortable with filling forms online.
Hi,

Thanks for your detail advice.

I'm aware of those online filling form service.  I never tried them before because of following reasons;
- security (if I have to filling in credit card info, bank account, etc.)
- signature

The method mentioned on my previous posting works for me for several years.  For signature I use scanner converting it as image.  It needs some..

satimis

---

### Post by sudodus on 2014-02-19
You can also try ***xournal***, that can be installed from the repositories. It gives you a possibility to export the edited result to a [new] pdf file (or to print it). The xournal editing is saved in a xournal file.

---

### Post by satimis on 2014-02-19
> **sudodus said:**
> You can also try ***xournal***, that can be installed from the repositories. It gives you a possibility to export the edited result to a [new] pdf file (or to print it). The xournal editing is saved in a xournal file.
Hi,

Thanks for your advice.

My workaround - to type on pdf form and put signature/chop on it:- 

1) install xournal

2) open the form on xournal

2) type text

3) export the doc as pdf file

4) install imagemagick

5) convert file.pdf file.png

6) open file.png on LibreWriter

7) paste signature/chop on it

8) export the document as pdf file again


Better solution would be appreciated.  Thanks


Rgds
satimis

---

### Post by sudodus on 2014-02-19
I can see that you don't want to use use three softwares: xournal and imagemagick and libreoffice for this task.

But a signature image file has no legal value in such cases. Use ***gpg*** to sign it electronically instead :-)

Another option might be to really sign it (writing your name with the mouse or (easier to make it look well) with a Wacom pad and or stylus in xournal. This way you really sign the document with your hand-writing (not copy a standard signature file).

-o-

Anyway, I'm also looking forward to further tips about suitable tools for your tasks: typing in a pdf-file and adding a signature

---

### Post by satimis on 2014-02-19
> **sudodus said:**
>  -snip-

Another option might be to really sign it (writing your name with the mouse or (easier to make it look well) with a Wacom pad and or stylus in xournal. This way you really sign the document with your hand-writing (not copy a standard signature file)
I'm looking for a solution on real signature.

I have a Wacom pad with stylus which I haven't used for several years.  It is now resting on shelves.  I have to digging it out.  I have no idea whether it works on Ubuntu?

How about the company chop?  Unless I treat it as image?

Thanks

Rgds
satimis

---

### Post by alvalee327hotmail on 2014-02-19
> **satimis said:**
> Hi all,

What will be the simple way to [[COLOR=#272727]type text on pdf[/COLOR]]("http://www.rasteredge.com/how-to/vb-net-imaging/pdf-annotating/") form without Adobe Acrobat [[COLOR=#272727]PDF[/COLOR]]("http://www.rasteredge.com/how-to/vb-net-imaging/pdf-reading/") typewriter?  What will be its equivalent on Linux?

Thanks

Rgds
satimis

Even without using Adobe product, you have to use other external PDF processing SDK for achieving this task. Or just you can also convert PDF to editable document format and then convert it back. Or you can try the text annotating method.

---

### Post by sudodus on 2014-02-20
> **satimis said:**
> I'm looking for a solution on real signature.

I have a Wacom pad with stylus which I haven't used for several years.  It is now resting on shelves.  I have to digging it out.  I have no idea whether it works on Ubuntu?

My Wacom Bamboo One (a simple model) works in Ubuntu 12.04 LTS, and I  can use it for hand-writing including a manual signature with Xournal. I  just tested it to be 100% sure before posting this reply.
> 

How about the company chop?  Unless I treat it as image?

Thanks

Rgds
satimis

I found this in Wikipedia, Hong-Kong English: "A 'chop' is a seal or stamp, e.g. a "*Company chop*" is the seal or stamp".

I see your point, and I don't know the legal value. Probably it varies between countries. In Sweden (I am rather sure) a cut and pasted image of the company chop has no legal value, it should be put onto a paper using the stamping tool, and combined with a manual signature. A copy of such a document (scanned or otherwise copied) is valid if signed by two persons that validate that the copying is correct.

Electronic signature can replace hand-writing, when the receiver can manage and accepts the method. Internet banking is a typical example, where electronic signature is replacing hand-writing.

---

### Post by satimis on 2014-02-20
> **sudodus said:**
> My Wacom Bamboo One (a simple model) works in Ubuntu 12.04 LTS, and I  can use it for hand-writing including a manual signature with Xournal. I  just tested it to be 100% sure before posting this reply.
Thanks for your advice.

I'll find my Wacom and test it.

> 
- snip -
Internet banking is a typical example, where electronic signature is replacing hand-writing.
I'm going to sign a pdf form for subscribing broadband connection only, not banking document.  On the said form chop is required.

Rgds
satimis

---

### Post by sudodus on 2014-02-20
In this case I would fill in the form with xournal, print it to paper, sign it with a ball-point pen and put the company chop onto the paper manually and send the paper with snail-mail.

Unless, of course, the internet service provider is happy with a copied image of the company chop, so that you can send the filled in and signed form electronically - ask them!

---

### Post by justin-w-elam on 2014-02-23
a signature can be /s/ =0, an X, a stamp, etc. - it just depends on what the parties agree to 
 one party could request an 'original signature in blue ink pen to be mailed and a copy faxed or emailed to them at time of execution' 
 or just a signed copy .... it all just 'depends' ... have 'fun'

---

