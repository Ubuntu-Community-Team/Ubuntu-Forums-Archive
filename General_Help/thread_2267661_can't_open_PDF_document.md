---
title: "can't open PDF document"
date: 2015-03-03
forum: General Help
---

### Post by al.adab on 2015-03-03
hello there,

can someone plz help - kind of going insane: 

- i need to download plus open [http://www.cic.gc.ca/english/pdf/kits/forms/IMM0008ENU_2D.pdf](http://www.cic.gc.ca/english/pdf/kits/forms/IMM0008ENU_2D.pdf), 
- here's the message I get upon opening it in Firefox 36.0 (Ubuntu 14.04) - the same message appears as the main body of the pdf document if i download it and open it (no matter with what application: i have acroread, evince, xpdf, etc): 

[I]Please wait...
If this message is not eventually replaced by the proper contents of the document, your PDF
viewer may not be able to display this type of document.
You can upgrade to the latest version of Adobe Reader for Windows®, Mac, or Linux® by
visiting [http://www.adobe.com/go/reader_download](http://www.adobe.com/go/reader_download).
For more assistance with Adobe Reader visit [http://www.adobe.com/go/acrreader](http://www.adobe.com/go/acrreader).
Windows is either a registered trademark or a trademark of Microsoft Corporation in the United States and/or other countries. Mac is a trademark
of Apple Inc., registered in the United States and other countries. Linux is the registered trademark of Linus Torvalds in the U.S. and other
countries[/I]

i'm using pdf docs on a daily basis and have never come across this problem. Any idea? thanks.

---

### Post by Bucky Ball on 2015-03-03
I'm getting exactly the same message when I try to open that pdf in Firefox or Document Viewer (Evince). Not a problem at your end, I wouldn't think. Everything is working fine re. PDFs on my machine and this is the first time I've ever seen this error. 

The document does contain forms and that could be the issue, although I can open documents containing forms apart from this one. :-k

---

### Post by al.adab on 2015-03-03
I too can open pdfs that contain forms...usually, that is. will i have to find a PC with Windows to get around this? i really need that form...

---

### Post by dino99 on 2015-03-03
maybe a firefox setting issue: are you sure it is using evince ? check it from the firefox "about : config"
popler-utils can help to grab info about your pdf

---

### Post by al.adab on 2015-03-03
good idea, i was using acrobat reader. just changed to evince, unfortunately to no avail...i've also tried to open the page on chrome - on a couple of pdf viewer extensions - unsuccessfully, though...
can anyone open that pdf link on their firefox/ubuntu 14.04? i have no chance to try my luck on a windows-powered machine - for a few days, at least, and just wanted to make sure there's no problem at the source, ie, the link is broken or the like.

---

### Post by Bucky Ball on 2015-03-03
> **9d9 said:**
> maybe a firefox setting issue: are you sure it is using evince ? 

I'm using Evince and get exactly the same behaviour. Why I said in my last post I suspect it may be at their end. ;)

I might boot into Windows and give it a shot there.

---

### Post by billrbilly on 2015-03-03
I right clicked on your link and saved the file 
Shared the file with a version of windows 7 in Virtualbox and it opened it fine with Foxit Reader
Thought I would give foxit a try with Wine install and I can still open the downloaded file in Ubuntu
All 5 pages of the application form are viewable and fields are interactive and can be filled in

---

### Post by al.adab on 2015-03-03
many thanks for the suggestion billrbilly! i've installed a "free" version (hoping it's free as in "free"...) and run it under Wine. I'm now able to open + edit the pdf. all is well :) hope that's ok if i mark this post as "solved".

---

### Post by al.adab on 2015-03-03
if i may also add that - for some reason - after installing FoxitReader (settings: main pdf reader = no, ability to read pdfs in browswer = yes) I'm able to open, read, and edit the pdf document in question directly on firefox! great!

---

