---
title: "pdfgrep - Need better scanning quality"
date: 2022-06-09
forum: General Help
---

### Post by oygle on 2022-06-09
When I use 'pdfgrep' on a sample PDF ( e.g. from [https://thejoywithin.org/wp-content/uploads/2020/05/Neville-Goddard-Awakened-Imagination-PDF-Ebook.pdf](https://thejoywithin.org/wp-content/uploads/2020/05/Neville-Goddard-Awakened-Imagination-PDF-Ebook.pdf)  ) ..

pdfgrep "imagine" Neville-Goddard-Awakened-Imagination-PDF-Ebook.pdf 

the results are fine. When I try pdfgrep on some other stored PDF's, the results are often nothing (should be some results) or partial. Never as good as a nice clear/clean PDF.

The printer I'm using is a HP - Photosmart-Prem-C310-series. The software installed is HPLIP , version 3.22.4

I have asked for help on the HP forums and the 'hplip' forums; no replies.

I'm simply needing the scanning quality to improve. The scans are hazy, like a blue/grey lines in the background. Definitely not a nice white background and clear text. Have tried cleaning the glass; no change.

The scanning tools tried so far are:

    Document Scanner
    Skanlite
    gscan2pdf
    XSane
    
Have used 300 and 600 dpi, color and black/white, but really, no changes. It still results in 'pdfgrep' being unsuccessful at finding words that I know are in the PDF's.

The other tools I have been testing with, mostly focused on the OCR side of things - tesseract and pdftotext. Have had very good results with tesseract, it can only search through images though, not PDF's. The 'pdfinfo' tool is handy also.

Have just come across 'ocrmypdf' ( see [https://github.com/ocrmypdf/OCRmyPDF](https://github.com/ocrmypdf/OCRmyPDF) ) and about to test that. Hopefully it will be able to change the 'dirty' scanned PDF's to a much 'cleaner' PDF.  There is also 'img2pdf' to have a look at.

Some resources I have found helpful:

[https://askubuntu.com/questions/16268/whats-the-best-simplest-ocr-solution](https://askubuntu.com/questions/16268/whats-the-best-simplest-ocr-solution)
[https://duckduckgo.com/?t=ffab&q=ubuntu+ocr+scanning&atb=v322-1&ia=web](https://duckduckgo.com/?t=ffab&q=ubuntu+ocr+scanning&atb=v322-1&ia=web)

Also wondering if tesseract can search a PDF, rather than an image ? - [https://duckduckgo.com/?t=ffab&q=can+tesseract+search+a+pdf&atb=v322-1&ia=web](https://duckduckgo.com/?t=ffab&q=can+tesseract+search+a+pdf&atb=v322-1&ia=web)

A post about using 'ocrmypdf' to create searchable PDF's - [https://medium.com/@treyharris/converting-a-scanned-document-into-a-compressed-searchable-pdf-with-redactions-63f61c34fe4c](https://medium.com/@treyharris/converting-a-scanned-document-into-a-compressed-searchable-pdf-with-redactions-63f61c34fe4c)

May have a look at 'recoll' - [https://www.xmodulo.com/how-to-search-multiple-pdf-documents-for-words-on-linux.html](https://www.xmodulo.com/how-to-search-multiple-pdf-documents-for-words-on-linux.html)

Possibly you have some tips on how to improve the scanning quality ?

---

### Post by mIk3_08 on 2022-06-09
> **oygle said:**
> 
the results are often nothing (should be some results) or partial. Never as good as a nice clear/clean PDF.
I'm simply needing the scanning quality to improve. The scans are hazy, like a blue/grey lines in the background. Definitely not a nice white background and clear text. Have tried cleaning the glass; no change.
The scanning tools tried so far are:

    Document Scanner
    Skanlite
    gscan2pdf
    XSane
    
Have used 300 and 600 dpi, color and black/white, but really, no changes. It still results in 'pdfgrep' being unsuccessful at finding words that I know are in the PDF's.
The other tools I have been testing with, mostly focused on the OCR side of things - tesseract and pdftotext. Have had very good results with tesseract, it can only search through images though, not PDF's. The 'pdfinfo' tool is handy also.
Have just come across 'ocrmypdf' ( see [https://github.com/ocrmypdf/OCRmyPDF](https://github.com/ocrmypdf/OCRmyPDF) ) and about to test that. Hopefully it will be able to change the 'dirty' scanned PDF's to a much 'cleaner' PDF.  There is also 'img2pdf' to have a look at.

Some resources I have found helpful:

[https://askubuntu.com/questions/16268/whats-the-best-simplest-ocr-solution](https://askubuntu.com/questions/16268/whats-the-best-simplest-ocr-solution)
[https://duckduckgo.com/?t=ffab&q=ubuntu+ocr+scanning&atb=v322-1&ia=web](https://duckduckgo.com/?t=ffab&q=ubuntu+ocr+scanning&atb=v322-1&ia=web)

Also wondering if tesseract can search a PDF, rather than an image ? - [https://duckduckgo.com/?t=ffab&q=can+tesseract+search+a+pdf&atb=v322-1&ia=web](https://duckduckgo.com/?t=ffab&q=can+tesseract+search+a+pdf&atb=v322-1&ia=web)
A post about using 'ocrmypdf' to create searchable PDF's - [https://medium.com/@treyharris/converting-a-scanned-document-into-a-compressed-searchable-pdf-with-redactions-63f61c34fe4c](https://medium.com/@treyharris/converting-a-scanned-document-into-a-compressed-searchable-pdf-with-redactions-63f61c34fe4c)
May have a look at 'recoll' - [https://www.xmodulo.com/how-to-search-multiple-pdf-documents-for-words-on-linux.html](https://www.xmodulo.com/how-to-search-multiple-pdf-documents-for-words-on-linux.html)

Possibly you have some tips on how to improve the scanning quality ?

Scanned file are always not perfect. If you want perfect image then go to photo editor application. Their are lots of them. You can edit your scanned file images to make it better. Because if you only depend on your scanner machine it will take you too long to have a perfect scanned. Because most of the image via scanner machine, even the small tiny part like dust are captured. so, If you have a clean photo then you decide to scan it don't expect that you have clean image photo result. I'm sure their is a tiny parts capture by your scanner and to clean it you need to use photo editor application for that. Professional Publisher uses a Photo Editor for their works to publish. They don't depend on the scanning application tool only.  Scanning application tool can only give you a high resolution quality images good for photo editing. So Good Luck. Regards and Cheers.

---

### Post by oygle on 2022-06-09
@mIk3_08 - Thanks for your reply. Yes, some sort of editor can no doubt remove the 'dust', etc. Yet I'm not concerned about scanning images, I only really want the text, so that 'pdfgrep' can then search the PDF and find the search terms I'm looking for.

---

### Post by mIk3_08 on 2022-06-09
> **oygle said:**
> @mIk3_08 - Thanks for your reply. Yes, some sort of editor can no doubt remove the 'dust', etc. Yet I'm not concerned about scanning images, I only really want the text, so that 'pdfgrep' can then search the PDF and find the search terms I'm looking for.
I think you might need a text converter for this. scanned documents is automatically be rendered as image file format. Im not so expert of this but you need application for this. pdf file is a form of image file format or one of the compress document. They uses pdf format so that their text file won't be scattered when they decided to deliver it digitally. If you want your document to be scanned as is.... as text document... Their are scanner for this... I think they called it overhead scanner... I don't know. Just try search around.

---

### Post by oygle on 2022-06-10
Thanks @mIk3_08   - possibly this is what you have described ? - [https://support.hp.com/us-en/document/c06301053](https://support.hp.com/us-en/document/c06301053)

---

### Post by dragonfly41 on 2022-06-10
Another suggestion .. try OpenCV / PyTesseract ..

[https://towardsdatascience.com/extracting-text-from-scanned-pdf-using-pytesseract-open-cv-cd670ee38052](https://towardsdatascience.com/extracting-text-from-scanned-pdf-using-pytesseract-open-cv-cd670ee38052)

---

### Post by Holger_Gehrke on 2022-06-10
pdf is at it's heart a vector graphics format that can also store bitmaps and text. pdf files generated by scanning are often just bitmaps of the pages, no way for pdfgrep to find text in that.

I guess what mlk3_08 meant by text converter is an OCR (optical character recognition) program. There are several (tesseract, gocr, cuneiform, ...) but AFAIK those are command line tools which for ease of use might need a graphical front end like gimagereader. For good scans the error rate is on the order of 1% or less (which still means you get several mistakes per paragraph and don't get me started on the hilarious results you get if the program tries to 'read' a picture in the scanned page). 

If you open a pdf in a viewer and the cursor changes to a text cursor (vertical bar) and you can mark text for cut-and-paste then there is text in the pdf and programs like pdfgrep can find that text. There are a few useful tools in the package 'poppler-utils', especially pdftotext which will extract the text-content of a pdf. If a pdf-file contains only images this is the easiest way to find out; 'pdftotext filename.pdf -' will print nothing or a few empty lines in that case.

Holger

---

### Post by Impavidus on 2022-06-10
Pdf is a file format designed to control printers. It can have multiple pages of vector graphics, consisting of elements placed on a page. Those elements can be letters, raster images or other primitives. Letters themselves are defined in a font as Bezier curves or raster images. In a scanned pdf, each pages contains just a single element, being a raster image. pdfgrep doesn't handle raster images.

Pdfs with text, including most pdfs that aren't scans, are easier. With a bit of luck the text uses a sensible encoding vector (ligatures can be tricky, as they're created by font designers and only present in font encoding, not in text encoding, and are certainly not standardised), with some more luck the tool can see the difference between a kern and a space; it may be able to see which line comes after which; maybe your tool can filter out header, footer and margin texts and if really everything goes well, your tool may be able to merge hyphenated words back into a single word – which requires language-specific code.[SUP]1[/SUP] Just to say that this is a hard problem, but it can be done.

In your case, you have to run an OCR tool on your pdfs and hope for the best. There are OCR tools that can embed the recovered text in the pdf file invisibly, and then pdfgrep can deal with it. You could also use an OCR tool to turn the file into something that isn't pdf at all. It appears that HP has made a scanning tool that has an OCR tool built-in, but at best that will save you a few mouse clicks. You can also take a stand-alone scanning tool and a stand-alone OCR tool and take the best of each.

[SUP]1[/SUP]: Looking at my native language, Dutch, lat-je must be de-hyphenated as latje, but la-tje must be de-hyphenated as laatje, so we need a rule for doubling vowels. And IIRC in German until 1996, there was a special rule for dealing with ck.

---

### Post by oygle on 2022-06-10
> **dragonfly41 said:**
> Another suggestion .. try OpenCV / PyTesseract ..

[https://towardsdatascience.com/extracting-text-from-scanned-pdf-using-pytesseract-open-cv-cd670ee38052](https://towardsdatascience.com/extracting-text-from-scanned-pdf-using-pytesseract-open-cv-cd670ee38052)

I have been testing with tesseract and found it to be very accurate. I see OpenCV is at [https://duckduckgo.com/?t=ffab&q=opencv+for+ocr&atb=v322-1&ia=web](https://duckduckgo.com/?t=ffab&q=opencv+for+ocr&atb=v322-1&ia=web) ; it is installed by deafault, as I have many 'opencv' hits when doing a 'locate' on 'opencv'. It may have been the tool I used last year to extract words from a video. The images were extracted from the video and then the words from the videos. Whatever tool it was, it was also very accurate.

> **Holger_Gehrke said:**
> pdf is at it's heart a vector graphics format that can also store bitmaps and text. pdf files generated by scanning are often just bitmaps of the pages, no way for pdfgrep to find text in that.

Thanks. Yes, I have been reading up a bit on PDF files, and where there is a 'searchable PDF' (like the ebook example), I think there is a text overlay.

> **Holger_Gehrke said:**
> I guess what mlk3_08 meant by text converter is an OCR (optical character recognition) program. There are several (tesseract, gocr, cuneiform, ...) but AFAIK those are command line tools which for ease of use might need a graphical front end like gimagereader. For good scans the error rate is on the order of 1% or less (which still means you get several mistakes per paragraph and don't get me started on the hilarious results you get if the program tries to 'read' a picture in the scanned page).

Haven't heard of cuneiform ; it seems to be at [https://launchpad.net/cuneiform-linux](https://launchpad.net/cuneiform-linux) . Hadn't heard of gimagereader ( [https://github.com/manisandro/gImageReader](https://github.com/manisandro/gImageReader) ) ; there are so many tools.

> **Holger_Gehrke said:**
> If you open a pdf in a viewer and the cursor changes to a text cursor (vertical bar) and you can mark text for cut-and-paste then there is text in the pdf and programs like pdfgrep can find that text. There are a few useful tools in the package 'poppler-utils', especially pdftotext which will extract the text-content of a pdf. If a pdf-file contains only images this is the easiest way to find out; 'pdftotext filename.pdf -' will print nothing or a few empty lines in that case.

Thanks for the tip to check in a PDF for text. I have been noticing in Ocular, that I cannot select the text from docs I have scanned, yet can select text from that ebook (link in first post). 

> **Impavidus said:**
> Pdf is a file format designed to control printers. It can have multiple pages of vector graphics, consisting of elements placed on a page. Those elements can be letters, raster images or other primitives. Letters themselves are defined in a font as Bezier curves or raster images. In a scanned pdf, each pages contains just a single element, being a raster image. pdfgrep doesn't handle raster images.

Thanks, and hence the reason for the little or no success rate in using 'pdfgrep'. It wasn't the tool so much, it was probably that the PDF had no text overlay.

> **Impavidus said:**
> Pdfs with text, including most pdfs that aren't scans, are easier. With a bit of luck the text uses a sensible encoding vector (ligatures can be tricky, as they're created by font designers and only present in font encoding, not in text encoding, and are certainly not standardised), with some more luck the tool can see the difference between a kern and a space; it may be able to see which line comes after which; maybe your tool can filter out header, footer and margin texts and if really everything goes well, your tool may be able to merge hyphenated words back into a single word – which requires language-specific code.[SUP]1[/SUP] Just to say that this is a hard problem, but it can be done.

So, the ebook at [https://thejoywithin.org/wp-content/uploads/2020/05/Neville-Goddard-Awakened-Imagination-PDF-Ebook.pdf](https://thejoywithin.org/wp-content/uploads/2020/05/Neville-Goddard-Awakened-Imagination-PDF-Ebook.pdf) and the Firefox "print to PDF" using [https://askubuntu.com/questions/16268/whats-the-best-simplest-ocr-solution](https://askubuntu.com/questions/16268/whats-the-best-simplest-ocr-solution) are "PDF's with text", and **NOT** scans, so the results were good from 'pdfgrep'

> **Impavidus said:**
> In your case, you have to run an OCR tool on your pdfs and hope for the best. There are OCR tools that can embed the recovered text in the pdf file invisibly, and then pdfgrep can deal with it. You could also use an OCR tool to turn the file into something that isn't pdf at all. It appears that HP has made a scanning tool that has an OCR tool built-in, but at best that will save you a few mouse clicks. You can also take a stand-alone scanning tool and a stand-alone OCR tool and take the best of each.

Yes, it does seem it will be better to focus any testing on OCR tools, and _NOT_ getting the 'scanning' side of things better quality. In a nutshell, the scanning quality is what it is, and the effort required may not be worht it, when there are so many good/accurate OCR tools. I will also be better to simply scan to an image so that tools like 'tesseract', etc can work with that. In a nutshell, the primary goal is to have searchable files.

---

### Post by mIk3_08 on 2022-06-11
> **oygle said:**
> Thanks @mIk3_08   - possibly this is what you have described ? - [https://support.hp.com/us-en/document/c06301053](https://support.hp.com/us-en/document/c06301053)
> **Holger_Gehrke said:**
> pdf is at it's heart a vector graphics format that can also store bitmaps and text. pdf files generated by scanning are often just bitmaps of the pages, no way for pdfgrep to find text in that.

I guess what mlk3_08 meant by text converter is an OCR (optical character recognition) program. There are several (tesseract, gocr, cuneiform, ...) but AFAIK those are command line tools which for ease of use might need a graphical front end like gimagereader. For good scans the error rate is on the order of 1% or less (which still means you get several mistakes per paragraph and don't get me started on the hilarious results you get if the program tries to 'read' a picture in the scanned page).

If you open a pdf in a viewer and the cursor changes to a text cursor (vertical bar) and you can mark text for cut-and-paste then there is text in the pdf and programs like pdfgrep can find that text. There are a few useful tools in the package 'poppler-utils', especially pdftotext which will extract the text-content of a pdf. If a pdf-file contains only images this is the easiest way to find out; 'pdftotext filename.pdf -' will print nothing or a few empty lines in that case.

Holger
Yeah. the OCR thing. And I agree with Holger_Gehrke with his statement below;
> **Holger_Gehrke said:**
> 
If you open a pdf in a viewer and the cursor changes to a text cursor (vertical bar) and you can mark text for cut-and-paste then there is text in the pdf and programs like pdfgrep can find that text.

If you want your scanned pdf text document be find during search be sure if you view your document via pdf viewer you can highlight your text which is ideal for copy and paste pdf document text file. Regards and Cheers.

---

### Post by oygle on 2022-06-11
> **mIk3_08 said:**
> Yeah. the OCR thing. And I agree with Holger_Gehrke with his statement below;

If you want your scanned pdf text document be find during search be sure if you view your document via pdf viewer you can highlight your text which is ideal for copy and paste pdf document text file. Regards and Cheers.

Yes, I have noticed that the PDF's that are not 'searchable' by 'pdfgrep' are the ones where I _cannot _highlight the text. So it is some sort of gauge as to whether PDF searching is possible or not. I have tried the code at [https://towardsdatascience.com/extracting-text-from-scanned-pdf-using-pytesseract-open-cv-cd670ee38052](https://towardsdatascience.com/extracting-text-from-scanned-pdf-using-pytesseract-open-cv-cd670ee38052) , and run it against a PDF that isn't searchable and it outputs a number of images from the PDF. Will then try "tesseract" or similar, as I feel trying to improve the scanning quality may be a waste of time.

---

### Post by oygle on 2022-06-11
Have run a test on one of the PDF's that was **completely** unsearchable, and used "ocrmypdf" ( see [https://www.linuxlinks.com/excellent-utilities-ocrmypdf-add-ocr-text-layer-scanned-pdfs/2/](https://www.linuxlinks.com/excellent-utilities-ocrmypdf-add-ocr-text-layer-scanned-pdfs/2/) ). Nice handy tool, now 'pdfgrep' can find search items.

---

### Post by mIk3_08 on 2022-06-11
I don't know if this can help. Just try this link. 
[Link 1]("https://www.linux.com/training-tutorials/how-scan-and-ocr-pro-open-source-tools/")
[Link 2]("https://linuxhint.com/ocr-apps-linux/")
Regards and Cheers.

---

### Post by oygle on 2022-06-11
> **mIk3_08 said:**
> I don't know if this can help. Just try this link. 
[Link 1]("https://www.linux.com/training-tutorials/how-scan-and-ocr-pro-open-source-tools/")
[Link 2]("https://linuxhint.com/ocr-apps-linux/")


Thanks, yes I have found tesseract to be very accurate.

---

