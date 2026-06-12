---
title: "Redact PDFs"
date: 2020-03-28
forum: General Help
---

### Post by UncleMonty on 2020-03-28
Is there any software available in ubuntu which can be used to redact pdf documents?

---

### Post by SeijiSensei on 2020-03-28
You can import PDFs into the GIMP.  Then you should be able to black out the redacted area with the drawing and painting tools and re-export the PDF.

---

### Post by coffeecat on 2020-03-28
*Thread moved to **General Help**.*

---

### Post by deadflowr on 2020-03-29
You can do ad-hoc redacts with evince for the version used in Ubuntu 19.10.
(Unfortunately it doesn't seem to be an option in earlier versions like what comes with Ubuntu 18.04,
though you can install either the snap or flatpak versions which are newer)

But in 19.10, simply highlight the section you want to redact then right click and select Highlight Selected Text.
Then right click on the highlighted section again and select Annotation Properties.
Then click on the color selection to open the color picker window and choose black.
Close the color picker window and select Apply in the Annotations Properties window.
It should show the highlighted section now blacked out.
Closing the PDF should prompt you to save the edited document. (Save a Copy, which can save as overwrite or a new document if you want).

Edit: if the pdf is a scanned document then you probably need something like gimp as stated above.

---

### Post by HermanAB on 2020-03-29
I would use Xournal.  It is very easy to use.  It normally edits non-destructively by making an overlay.  Once you are done, export the file to a new PDF.

---

### Post by David_Wright on 2020-03-29
I assume that you already know this, given that you asked a question about redaction, but I don't think that the answers above will work - the underlying text will still be there and visible either via a simple copy or by looking at the source.

Software that *will* do redaction is Master PDF Editor, although I don't think it is in the repositories and therefore you will have to download a deb to install.

---

### Post by TheFu on 2020-03-29
The problem w/ redacting PDFs is that the underlying document still contains the data you don't  want seen, ever.  The only way around that is to re-author the document without the data, otherwise you risk having some slightly smart person, not a genius at all, disabling the annotations, thus being able to see all the data.

if you cannot re-author using the source, then the next best way would be to print the document, take a black marker and block out the sensitive parts, then use a scanner to recreate the doc as an image.  This will break all sorts of great things about PDFs like searches, copy/paste, etc.

it's a tough situation.  Anything so sensitive that needs to be redacted cannot afford to be leaked. No way, no how. There have been leaks like this in the business world with PR stuff that haunted companies for years.  Leaks by Govts have been even worse.  Anyone working with medical data needs to be extra careful, since those leaks are probably illegal with fines for each separate datum leaked.

IF you don't use the analog method, be certain to validate that whatever method is used ACTUALLY does remove the underlying data.  Don't leave it as a layer in gimp or as part of the base document when using any PDF-aware tool.  Trouble lies in trusting those methods.

---

### Post by Impavidus on 2020-03-30
Gimp won't handle multiple pages and will convert the pdf to raster graphics (if it isn't already), reducing quality and making it harder to edit the file later. But pdf was never meant to be editable anyway.

If it's a vector pdf, you can put a black bar over the text to make it disappear, but it's just as easy to remove that black bar again if you distribute the document electronically. If you want to print the document and hand it to its recipient that way, it may be OK (although not very secure if it's a proportional font).

A pdf file with vector text consists of boxes with one glyph (a graphical representation of a character or ligature) each and a displacement to the next box, interspersed with small displacements used as kerns and spaces. There may be tools that can replace these boxes and displacements (or better, a long sequence of them at once) by black boxes, so that the glyphs are really gone. But even then, assuming it's a proportional font, the widths of the boxes make it easy to find out which glyphs used to be there.

In the days of the typewriter black bars were effective. The bars were physically put on the paper with black marker, then photocopied, and fonts were fixed-width, so the only clue left for the reader was the number of characters.

---

### Post by deadflowr on 2020-03-30
I really only did a quick look at this issue earlier and so decided to look into it more and found LibreOffice 6.3+ has a redact function now.
[https://wiki.documentfoundation.org/ReleaseNotes/6.3#New_Feature:_Redaction]("https://wiki.documentfoundation.org/ReleaseNotes/6.3#New_Feature:_Redaction")

Now, only LibreOffice Writer actually has the feature in it's toolbar settings by default, but you can add it to all LibreOffice programs by adding it using the Tools > Customize utility.
(adding it to Draw makes it easier since LibreOffice opens PDFs in Draw)

There is also an apt package in the repos (for 18.04+) called pdf-redact-tools.
I think the github page for it explains how it works,
[https://github.com/firstlookmedia/pdf-redact-tools#how-to-use]("https://github.com/firstlookmedia/pdf-redact-tools#how-to-use")

---

### Post by HermanAB on 2020-03-30
Journal export to PDF makes the changes permanent - nothing underneath the redactions.  I actually checked that some years ago.

---

### Post by TheFu on 2020-04-10
Redaction failure w/ PDF:
[https://arstechnica.com/tech-policy/2020/04/frontier-botches-redaction-reveals-952000-potential-network-problems/](https://arstechnica.com/tech-policy/2020/04/frontier-botches-redaction-reveals-952000-potential-network-problems/)

---

### Post by Artim on 2020-04-10
I use [COLOR=#0000cd]**Xournal**[/COLOR] for all my pdf editing.  It's super simple and great for other tasks as well.  Easy note-taking app too.  When I'm ready to save an edited pdf, I can either *print-to-file* or save-as "newname.pdf"

---

