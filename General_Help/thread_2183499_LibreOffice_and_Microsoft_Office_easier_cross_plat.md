---
title: "LibreOffice and Microsoft Office easier cross platform reading?"
date: 2013-10-25
forum: General Help
---

### Post by mithen2 on 2013-10-25
One thing that annoys me about using Ubuntu and LibreOffice is that when I have to open my LibreOffice .odf files in Windows, for example doing a presentation on University Windows PC's. The format gets completley wrecked. Things like the wording format, bullet point indentation all have to be corrected. Is there some kind of addon or package for LibreOffice that will make whatever work I do on LibreOffice in Ubuntu to display identically to Microsoft Word?

---

### Post by Lars Noodén on 2013-10-25
You could be running in to font problems.  Are the same typefaces available on both machines?  That will give you problems even between Windows machines.  There's not a way to force MS to use better fonts, but you can retrofit your Ubuntu machine to use some of the MS fonts using the package msttcorefonts.  Try that and then make a presentation using only the fonts from that package.

---

### Post by Bucky Ball on 2013-10-25
Extremely simple solution (if it is not the font conflict): don't save 'em as .odt files! When starting a project, open a new file, immediately name it and 'save as' a .doc file or whatever you need to use at uni. Obvious. I had no idea MS Office had any idea what an .odt file was in the first place. ;)

You do not need to work in .odt in Libreoffice. No brainer. I'm not sure why you're not at least saving them as .doc files to use on a Win machine in the first place.

---

### Post by mithen2 on 2013-10-25
OMG I'm such a noob! Yes that would be the most logical and simplist solution haha! I would save it just as a .doc file or .docx?

---

### Post by Impavidus on 2013-10-25
Apart from the fonts, you can try using libreoffice on Windows (I guess since the computer isn't yours you'd have to ask the administrator to install it). You can also make you presentations in pdf with embedded fonts, which nearly always works. It's what I always do. The bulleted lists still work, but you won't have those well-known PowerPoint animations. In principle they are now supported in pdf, but few applications can handle them. But in my opinion these animations are worthless anyway.

---

### Post by Lars Noodén on 2013-10-25
+1 for using LibreOffice on Windows

There is a [portable LibreOffice](http://portableapps.com/apps/office/libreoffice_portable) which can be run from USB stick or other portable device.

Sorry.  I missed the reference in the original post to ODF.  MS really demonstrates a hate for ODF going back to its beginning.  It even tried to make a competing standard, OOXML, but no one uses that not even MS itself.  So MS products don't actually work with ODF even if some papers might claim otherwise.  They break ODF files so whatever you do don't open an ODF file in MS Office and then save it.  You will lose something.  The new MS Office format(s), docx, is still a work in progress, so if you go between MSO and LO, try one of the .doc formats.  

One way around all that is to avoid MS Office and stick with LibreOffice or OpenOffice.org.  You might be able to get LibreOffice installed on the University computers, for ODF sake, if you know the right people.  But if you can't you can install portable LO on your USB stick or in your home directory on the University's file sharing and launch it from there.

---

### Post by Bucky Ball on 2013-10-25
> **mithen2 said:**
> OMG I'm such a noob! Yes that would be the most logical and simplist solution haha! I would save it just as a .doc file or .docx?

Yes! .doc or .docx or whatever format is required at the other end. ;)

Using Libreoffice on the machine at the other end is fine if it's do-able (although that is not the solution to, nor has it anything to do with, the quite specific question you asked about working on a document in Libreoffice and then needing to use it on MS Office), but I think I know your situation. You're rolling up at college/uni/school and having to bring up documents on machines at random, machines you may never use again, or not next time, anyhow, and not your machine anyhow.

---

### Post by Impavidus on 2013-10-25
At my university the student's associations for physics, mathematics and computer science managed to convince the science faculty to install Linux (Fedora) on about 20% of the computers, despite an official university-wide policy to install only Windows on every computer not managed by individual departments. That would be the ideal long-term solution. But for the time being, use the advice given in the previous posts.

---

### Post by PeterRJG on 2013-10-25
You would need to use .docx if you plan on inserting any equations or complex maths symbols into your documents. Pre 2007 .doc won't cut it. The actual interoperability between LO and MS Office 2007+ when it comes to .docx isn't that bad. I use LO at home and my uni does things in .docx (and .xlsx, .pptx, etc). Apart from things mentioned like font differences - which are easily dealt with - in my experience, it's line spacing, particularly between paragraphs. LO has a tendency to crunch the spacing between paragraphs created by MS. But the interoperability is getting better, so long, as others have said, you avoid .odt.

---

### Post by Vaphell on 2013-10-26
another option is to export to pdf in case the file doesn't have to be editable.
With docs there is never a guarantee you will get the same effect, because even a different printer installed in the system can somehow make a difference big enough to distort original layout here and there.

---

