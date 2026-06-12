---
title: "PDF viewers show &quot;leaky&quot; letters"
date: 2023-08-19
forum: General Help
---

### Post by Paddy Landau on 2023-08-19
I received a PDF from a company, and it shows letters that look "leaky" (I don't know how else to describe it). It affects all letters that are **in bold**.

See the screenshot of an example; notice the first two words in bold.
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292611&stc=1[/IMG]
This shows not only on the main screen but also horribly badly in the thumbnails in the left panel, as shown here:
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292614&stc=1[/IMG]
This document was originally created with LibreOffice and exported as PDF, and which the company then modified.

The original PDF doesn't show this problem, but the company's modified PDF does. I've included the properties for both PDFs below.

PDF properties for the **original PDF**, which doesn't show this problem:
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292612&stc=1[/IMG]
PDF properties for the **company's revised PDF**, which does show this problem:
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292613&stc=1[/IMG]
Some points to try to nail down what's happening.

[LIST]
[*]This is the first time that I've seen this problem.
[*]Only the letters **in bold** show this problem.
[*]If I increase Evince's zoom to over 100%, the problem goes away. It shows only when the zoom is 100% or lower.
[*]In Xournal++ I get the same results.
[*]In Adobe's Acroread DC, this problem doesn't happen.
[*]If I print the document from Evince, it works perfectly, so the leakiness is only on screen.
[/LIST]
So, I'm reasonably sure that this is a problem with my machine's font rendering on screen (not the printer), rather than with the PDF itself. Bear in mind that Acroread DC uses WINE, so it has its own set of font rendering.

Do you know what could be causing this strange result? And, how could I fix it?

More information:

[LIST]
[*]Ubuntu 22.04
[*]Evince: All of the following show the same result.
[LIST]
[*]The default (standard repositories) version 42.3
[*]The snap version 44.1
[*]The flatpak version 44.3
[/LIST]

[*]Adobe's Acroread DC installed via snap
[*]Xournal++ installed via flatpak
[/LIST]
Thank you

---

### Post by dragonfly41 on 2023-08-19
I play around with document restructuring in my workflows and this "leakiness" which you describe does look like either an anti-aliasing effect or possibly some text in SVG format embedded into the PDF. At least it is a theory since I see such anti-aliasing in other documents.


 
> This document was originally created with LibreOffice and exported as PDF, and which the company then modified.
The original PDF doesn't show this problem, but the company's modified PDF does.
 I don't understand why you need a third party company to modify your creation. I would keep it all inhouse. What special services do they offer that cannot be done on your desktop? That would be a good start.
 
 
 
 
Search thread
 
 [https://duckduckgo.com/?q=font+anti+aliasing+in+pdf+printing&t=canonical&ia=web](https://duckduckgo.com/?q=font+anti+aliasing+in+pdf+printing&t=canonical&ia=web)

---

### Post by Impavidus on 2023-08-19
Standard comment: pdf was never intended for further processing; it's only meant for viewing, printing or embedding in another pdf file. When creating a document, conversion to pdf is always the last step. But I know that many don't understand this and force us to hand in pdfs for further processing.

Have you tried gv too? Most pdf readers depend on either libpoppler or ghostscript as a backend. Evince, xpdf and okular all use libpoppler; gv depends on ghostscript.

---

### Post by dragonfly41 on 2023-08-19
A bit of detective work answers my earlier question.
It appears that you are aiming to outline PDF content through an online service.
With an index to inner parts.
There are methods of keeping content inhouse. Particularly for security.


One approach which I use is to write content in Markdown (open *.md doc in Zettlr.com) then publish in different formats.  PDF, HTML, Presentation slides. Pandoc is used for this conversion.
Let me also introduce CherryTree which is found here.
[https://www.giuspen.net/cherrytree/](https://www.giuspen.net/cherrytree/)
This is a very elegant editor which follows a tree structure.
You start by creating a node which holds the content of your end PDF document. Let us call that node Project-1.
Now under Project-1 node you create child nodes representing the content of each of your indexed chapters. Sub-nodes can be created to any depth.
You can embed images in any rich text node.
Now to create a Table of Contents (equivalent to your Outline).
Open the empty Project-1 node and go to toolbar and choose Insert > Insert TOC and choose all subnodes.  This creates an index structure.
At this point you can go to toolbar > File > Export >
with options PDF, HTML and choose the Project-1 node (if you adopt CherryTree you will have many nodes in one CherryTree instance and indeed many CherryTree documents on different workflows).



[P.S.] If your content is already in PDF mode then reverse this process by exporting PDF to HTML (if you have images) using any PDF to HTML or TXT converter process. Pandoc is good for this But you can use LibreOffice or Master PDF Editor.

Then from this base content _start again_ by copying into Cherrytree nodes and/or Zettlr. Sometimes both are handy. To then export your indexed PDF. Basically reengineering content. All inhouse. 

  You might also use Scribus. The nice touch in Scribus is using ScribusGenerator3 python plugin to customise your exported documents by using data in an csv file and PHP Vars embedded in main document.  You can try this without installing on your desktop  on RollApp.com since I expressly asked for ScribusGenerator to be added. I use this for experimenting but a Virtual desktop would be safer when sensitive content is required. But it is a good vehicle for proof of concept and training.

---

### Post by Paddy Landau on 2023-08-19
To answer those asking why the PDF isn't kept in-house: It's a community magazine (no security required, as it's intended for public distribution). The company that we send it to is the Printer, who uses the PDF to create a proof. Once we've approved the proof, that proof is printed to create the magazine.

We have been using this method for many years, and this is the very first time that the proof has shown this problem. I included the PDF properties in the OP, because I thought that maybe it was a newer PDF structure; I don't know how these things work.

We don't have an alternative to this process. The magazine is entirely volunteer-driven, so we depend on the volunteers for technical skills; no salaries are paid; and money is tight, as it's a non-profit organisation for the benefit of the local community.
> **dragonfly41 said:**
> I play around with document restructuring in my workflows and this "leakiness" which you describe does look like either an anti-aliasing effect or possibly some text in SVG format embedded into the PDF. At least it is a theory since I see such anti-aliasing in other documents.
Thanks. I would suspect some anti-aliasing effect or other font-rendering problem, as it would seem strange to replace text with SVG.
> **Impavidus said:**
> Have you tried gv too?
That's the first that I've heard of gv. I've just installed it. It is worse, because even the original PDF is displayed with "leakiness" in its text. This reinforces the idea that it's something to do with the rendering of fonts, though I can't think why.

I might have to just accept this as "one of those mysteries", which is, in this case, fortunately harmless.

---

### Post by dragonfly41 on 2023-08-19
Sounds like an ideal match for Scribus (see above) which sends content to printers.

---

### Post by Paddy Landau on 2023-08-19
> **dragonfly41 said:**
> Sounds like an ideal match for Scribus (see above) which sends content to printers.
I hear you, but it would mean asking an already-busy volunteer to learn a new product, convert the existing LibreOffice template to Scribus, and start using that.

That's the thing with volunteers — they're already busy people.

---

### Post by dragonfly41 on 2023-08-19
Volunteer can stay with LibreOffice and simply inport *.odt into Scribus. The point is that printers can relate easier with Scribus which is expressly designed for that purpose.

---

### Post by Paddy Landau on 2023-08-20
> **dragonfly41 said:**
> Volunteer can stay with LibreOffice and simply inport *.odt into Scribus. The point is that printers can relate easier with Scribus which is expressly designed for that purpose.
Thank you. I'll test that.

---

### Post by Paddy Landau on 2023-08-20
> **dragonfly41 said:**
> … stay with LibreOffice and simply inport *.odt into Scribus.
I've installed Scribus (version 1.5.8), and I can't find a way to import .odt. I can import .pdf no problem.

Never mind. I'll leave it as is, because the process at least works.

---

### Post by dragonfly41 on 2023-08-20
Just for the record .. [here is the link in docs referring to import *.odt]("https://wiki.scribus.net/canvas/Help:Manual_Importodt").

The trick is you need to create a TextFrame first in new Scribus instance (which might extend over many pages over length of document) then right click on TextFrame and follow instructions.

Images are imported separately into ImageFrames.

Therefore you can buid up content in a front end toolchain. I mentioned CherryTree and Zettlr earlier or in your case LibreOffice then pipe content (which might flow from one or several human sub-editors in a team (as in newspaper or magazine production)  to Scribus which in turn pipes content to chosen print shop.  The print shop will explain what settings are needed for the magazine printer. Check with print shops if they are Scribus compatible.

Since Scribus *.sla is XML format you can further refine format using Python and Plugins.

---

### Post by Paddy Landau on 2023-08-20
> **dragonfly41 said:**
> Just for the record…
Thanks, but this is getting too complicated. The current method works fine: The Producer creates the ODT document in LibreOffice (from a template), exports it to PDF, and sends the PDF to the Printer. The Printer sends a proof for confirmation.

Adding in Scribus with those extra steps is going to be a hassle.

But thank you for the idea.

---

### Post by dragonfly41 on 2023-08-20
Understood.

---

