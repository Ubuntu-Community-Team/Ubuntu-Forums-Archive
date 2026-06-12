---
title: "libgnomeprint: Scrambled/encrpyted text when copying from PDF file"
date: 2007-06-27
forum: General Help
---

### Post by sc00ter on 2007-06-27
This is a strange problem, which I hope there is a very easy/straight forward solution. I've trawled the net, but have not found any obvious hits.

Basically, when I create a PDF file from either Open Office or Abiword (as an example - this is system-wide), I can copy the text from the PDF file, but when I attempt to paste the copied text into a document or an editor, it is scrambled/encrypted.
[B]
For example:[/B]

Attached is a .zip file of the test PDF file, created from AbiWord and using the "File / Save Copy ..." option (the very same results can also  be achieved by printing to a PDF file).

Open the newly created PDF file (I've used both Evince and Adobe Reader and both give exactly the same results), which contains the following text in decreasing point sizes:

```

The quick brown fox jumped over the lazy dog. 
The quick brown fox jumped over the lazy dog. 
The quick brown fox jumped over the lazy dog. 
The quick brown fox jumped over the lazy dog. 
The quick brown fox jumped over the lazy dog.
```

I then hit CTRL+A (Select All) and CTRL+C (copy) to get the text in the clipboard. Then open GEDIT (or AbiWord/OpenOffice) and CTRL+V to paste the selected text from the clipboard.

I then get the following **SCRAMBLED/ENCRYPTED** text pasted into the document/editor window:

```
8LI UYMGO FVS[R JS\ NYQTIH SZIV XLI PE^] HSK
8LI UYMGO FVS[R JS\ NYQTIH SZIV XLI PE^] HSK
8LI UYMGO FVS[R JS\ NYQTIH SZIV XLI PE^] HSK
8LI UYMGO FVS[R JS\ NYQTIH SZIV XLI PE^] HSK
8LI UYMGO FVS[R JS\ NYQTIH SZIV XLI PE^] HSK
```

All PDF files are created using **libgnomeprint** Version **2.18.0**.

Anyone got any idea how to turn off the **SCRAMBLING/ENCRYPTION** of the underlying text within  the generated PDF file?

---

