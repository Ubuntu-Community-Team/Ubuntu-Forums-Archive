---
title: "Inkscape freezes after render LaTeX formula"
date: 2008-01-17
forum: General Help
---

### Post by LeastCriminal on 2008-01-17
I am trying to use the Effects:Render:LaTeX formula feature in Inkscape under Ubuntu 7.10.  Inkscape locks up complete after I click Ok, no matter what I type.  It even freezes if I use the default formula.

Has anyone else got this to work?

I'd be grateful if so.  If this feature worked it would save me a lot of time.

Thanks.

---

### Post by hugmenot on 2008-01-18
The helper program pstoedit is broken. You can use this extension instead:

[http://www.elisanet.fi/ptvirtan/software/textext/index.html](http://www.elisanet.fi/ptvirtan/software/textext/index.html)

There's a note about the breakage and a fix. I use pdf2svg, and the result are good.

---

### Post by LeastCriminal on 2008-01-21
Thanks! I have the textext extension working.

Here are directions to replicate what I did, in case someone else encounters the same problem:

Verify that the "pdflatex" package is installed.

Install pdf2svg from source ( [http://www.cityinthesky.co.uk/pdf2svg.html](http://www.cityinthesky.co.uk/pdf2svg.html) ), or copy the precompiled binary ( [http://www.elisanet.fi/ptvirtan/software/textext/pdf2svg](http://www.elisanet.fi/ptvirtan/software/textext/pdf2svg) ) into /usr/local/bin and make it executable (chmod 755).

Download the textext source tarball ( [http://www.elisanet.fi/ptvirtan/software/textext/textext-0.3.3.tar.gz](http://www.elisanet.fi/ptvirtan/software/textext/textext-0.3.3.tar.gz) ).  Make sure the directory ~/.inkscape/extensions exists, then unpack the contents of textext/textext-0.3.3.tar.gz into the extensions directory.

(Re)start inkscape and test the "Effects::Tex Text" menu item.

---

### Post by ChAoS.ct on 2008-03-13
You can install the fixed package for ps2toedit:
[http://gambitchess.org/moin.py/InkscapeLaTeXFix](http://gambitchess.org/moin.py/InkscapeLaTeXFix)

Then it works

---

