---
title: "Making a booklet with a publishing program (Scribus?)"
date: 2007-01-28
forum: General Help
---

### Post by Jeff Gavett on 2007-01-28
I am trying to make a booklet right now for a recital I am going to sing. My hope is that I can design it myself on Ubuntu, and make a pdf or ps or some other compatible format to bring to Kinkos to be put together nicely.

I have Scribus, but I can't figure out how to make it format the way I was thinking. I would like to use plain letter sized paper folded over hamburger style and nested within itself to make a booklet. Hence, if I had 8 halfpages to work with, I would end up printing 2 pages of doublesided paper, the first having 1 and 8, with 2 and 7 facing on the back, then 3 and 6 with 4 and 5 facing on the back. So far, doublesided on Scribus seems to yield just normal pages, and I have no idea how I would get the kind of split formatting I need.

Is there a program better suited to this, or anything I'm completely missing in Scribus?

---

### Post by Jeff Gavett on 2007-01-28
Bump?

---

### Post by rvergara on 2007-01-28
I have used Inkscape with some success.

Another alternative is to use OpenOffice which is quite capable.

Hope this helps.

Regards

Ramiro

---

### Post by Jeff Gavett on 2007-01-28
> **rvergara said:**
> I have used Inkscape with some success.

Another alternative is to use OpenOffice which is quite capable.

Hope this helps.

Regards

Ramiro

Exactly how did you get openoffice to do what I mentioned? I can't seem to find any formatting options that will make it possible without being stupidly labor intensive.

---

### Post by xmastree on 2007-01-29
Can't help, but I'm watching with interest as I need the same thing.

I have done it once though. I was making 100 copies of a booklet and I managed it  by printing the original 16 pages full size, single sided. I then produced the actual booklets on a photocopier by arranging each pair of pages on the machine and reducing A3 > A4

A diagram helps, so that you know which pair to put on the other side of which, and which way round. they go.

---

### Post by Jeff Gavett on 2007-02-01
Desperation bump? Right now it seems like I'm going to end up making all my pages letter sized, then going to a kinkos or something and having them resize and put them two on a side.

---

### Post by xmastree on 2007-02-01
That's what I did last time.
How many are you making? You could, at a pinch, create an A5 page size, produce the document, then copy and paste each page into an A4 landscape document split into two columns. In the right order.

---

### Post by garybrlow on 2007-02-01
Desperation bump? he he he ) :P 

OpenOffice.org is capable of back to back printing but still no booklet type printing. I would like to see mirrored output (multiple single page printing on one paper - business card style) and simpler booklet creation in Scribus/Inkscape. Something similar to MSPublisher and the like.That is why I still can't let go of MSPublisher and other similar proprietary software. 

If anyone can point us to a solution that would be great. :)

By the way, has anyone tried it using Xara Extreme for Linux?

Cheers!!!

GaryBrlow :biggrin:

---

### Post by WW on 2007-02-01
If you can output your document as postscript, you can use the command **psbook**, possibly combined with **psnup**.

These commands are in the **psutils** package.

---

### Post by Jagermaster on 2007-02-01
> **garybrlow said:**
> Desperation bump? he he he ) :P 

OpenOffice.org is capable of back to back printing but still no booklet type printing. I would like to see mirrored output (multiple single page printing on one paper - business card style) and simpler booklet creation in Scribus/Inkscape. Something similar to MSPublisher and the like.That is why I still can't let go of MSPublisher and other similar proprietary software. 

If anyone can point us to a solution that would be great. :)

By the way, has anyone tried it using Xara Extreme for Linux?

Cheers!!!

GaryBrlow :biggrin:

I cant say that OO.o is quite ready to replace Publisher ...yet. In fact I remember them saying in their forums that they had "no intention" of going into desktop publishing. Thats a shame because they are SOOOOOO close to it anyways.

BUT... I can personally attest to the fact that I was able to copy and paste all of my "Publisher" contents in OO.o "**Draw**" and use it pretty much the same way as Publisher. (You have to ungroup after pasting)
In fact, I just finished my band's press kits from scratch as a new project in "Draw" and they came out great! So look in that direction possibly as a substitute to Publisher.

The benefit that seals the deal in Draw is that you can add as many blank pages as you need and edit each one without affecting the others...as opposed to to typical word processor behavior. Draw has most of the other behaviors of publishing programs already...Arrange, Align, move forward, Move to back etc...so like I said..it's doable :) 

OO.o lacks fancy borders though so you'll have to limit yourself to solid lines or dots and dashes around pictures . No biggie.

:guitar:

---

### Post by Jeff Gavett on 2007-02-02
Turns out that the file I originally made in Scribus, with full A4 pages formatted as 'double sided' with right as the first page can be made into a pdf that acrobat reader can print as a booklet quite easily.

Who'd a thunk, Acrobat Reader did something useful!

---

### Post by xmastree on 2007-02-11
Not sure if this is useful now, but I was using open office just now, and I came across this:
> You can print a Writer document as a brochure or a booklet. That is, Writer prints two pages on each side of the paper, so that when you fold the paper, you can read the document as a book.
When you create a document that you want to print as a brochure, use portrait orientation for the pages. Writer applies the brochure layout when you print the document.

Find more in the help, under **booklet printing**

---

### Post by pestilence4hr on 2007-05-03
> **WW said:**
> If you can output your document as postscript, you can use the command **psbook**, possibly combined with **psnup**.

These commands are in the **psutils** package.

You can output any document as postscript if you can print it.  Just click "print to file", the resulting file is postscript.  Therefore psbook can solve this problem universally.

---

### Post by hal8000 on 2007-05-03
Well you are in luck, if you do want to use Open Office 2.  I have created a template for Open Office Writer which works with A4 sized paper (very similar to US Letter size) you will be able to edit the template.

The paper is folded in half so that 2 full sheets will give you 8 pages, 3 full sheets will give you 12 pages, etc. What I so is pre-label the half sheets so that I can see the beginning and end of each page. Obviously as I type the page numbering will move so I compensate for this by using the backspace key.

I can send you my 8 page or 12 page template just pm me  and I will email you (or anyone else who wants a copy). Its probably not the best or easiest way of making a booklet but it works and in open Office Writer you can see the outline of each page.  You can include images, equations, etc but as already been stated may lack some features of an advanced Desktop Publisher program. 

When producing your work, remember to print out and use short edge flip, ( if you have a two sided printer) this way, the booklet is ready to read, just needs folding.

Hope that helps.

---

