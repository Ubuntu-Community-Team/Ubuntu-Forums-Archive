---
title: "PDFs &gt; Generating OCR text &gt; Creating / merging back into PDFs &gt;"
date: 2022-10-04
forum: General Help
---

### Post by GeordieJedi on 2022-10-04
Hi there guys.

I was hoping that you could help me with a project that I'm working on.

**Background:**
I have a large number of old magazines that are PDFs however they are mainly
just scanned images of the magazines themseleves.

What I was interested in doing is -

1. Scan these PDFs/magazines with an OCR tool, to obtain the text from the 
pages/images.

2. Then I'd like to either -
2.1. Create a new PDF with the image and the OCR'd text contained in it
2.2. Or merge the OCR'd text back into the original PDF's

This is to make the PDFs, text searchable.


**Questions:**

1. What are the best tool(s) that will allow me to do this

2. Is there anything else that I need to be aware of when doing this project.
(Anything to watch out for, or to trip up on ?)

TIA for any help or advice.

---

### Post by TheFu on 2022-10-05
I use 'gscantopdf'  for this.  Basically, the OCR puts ASCII text on the correct page, but "under" the image.  The quality of the OCR is highly dependent on the font and scan clarity.  About the best that I've seen is 90%.

I had a number of technical periodicals on paper. Rather than attempt the scan+OCR, I just found those same magazines online where they were published directly to PDF by the vendor.  Sometimes they charged $20 for the last 10 yrs of full magazines and sometimes they were posted for free downloads.  If the publisher has the source material, they can print directly to PDF, which results in PDF-Text and no need for OCR at all, unless type-3 fonts are used.  PDFs are searchable by most PDF viewers and by indexing+search tools like Recoll using helper programs.  Image-based PDFs are to be avoided.

I have to say, that $20 I spent was well worth saving me even 1 hour of effort for perfect, scalable, PDF files.

---

### Post by dragonfly41 on 2022-10-05
> [COLOR=#000000]What are the best tool(s) that will allow me to do this?
[/COLOR]

Best is subjective .. but for professional corpus analysis I would use a tool to dump PDF into text (Pandoc does this) then apply AntConc for corpus analysis of text files. Search AntConc.

---

### Post by GeordieJedi on 2022-10-05
Thanks very much for the replies and advice.
I'll check out those tools.

Much appreciated

---

### Post by TheFu on 2022-10-05
> **dragonfly41 said:**
> Best is subjective .. but for professional corpus analysis I would use a tool to dump PDF into text (Pandoc does this) then apply AntConc for corpus analysis of text files. Search AntConc.

I love pandoc, but when it dumps image-based PDF pages, they are just images and need OCR processing like any other image. AntConc seems to be for text, not images.  Any scanned image will need OCR, if the scanning just dumped the images into PDF containers.

I figure I have to be missing something with this suggestion.  Seems much later in the process - post-OCR. Of course, that could be extremely helpful too.

---

### Post by dragonfly41 on 2022-10-06
It is true that AntConc applies only to text corpora but I was suggesting a two stage workflow. There is another tool in the Professor Ant library to first extract text from PDF and create a text only corpus. Yet another tool is for tagging.

As I mentioned AntConc is a professional tool with some considerable learning curve. But once the art of corpus linguistics is mastered it can be very useful to analyse large corpora.

If you are just searching for a text pattern within PDF library then a simpler tool is here for CLI use.

[https://itsfoss.com/ripgrep-all/](https://itsfoss.com/ripgrep-all/)

Of course you could use both and apply [ripgrep-all]("https://itsfoss.com/ripgrep-all/") to shortlist PDF's containing a text pattern, then progress to create a text corpus of this pre-processed subset of PDF's.  There are other tools for writing such workflows and I often apply Actiona (in the Ubuntu repo, uses Actionscript2 from Flash days, very dated, developer has moved on -  but useful nonetheless) which has OpenCV built in.

Discussions on using Pandoc are here ..

[https://groups.google.com/g/pandoc-discuss/c/8qm82cPRGnU?pli=1](https://groups.google.com/g/pandoc-discuss/c/8qm82cPRGnU?pli=1)

There are online PDF > Text converters but I prefer to control the process at desktop.

---

