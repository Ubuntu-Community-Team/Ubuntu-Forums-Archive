---
title: "suspicious &quot;open action&quot; in LibreOffice created PDF"
date: 2016-10-20
forum: General Help
---

### Post by Buntu Bunny on 2016-10-20
I just had a LO-created PDF scanned at [VirusTotal]("https://www.virustotal.com/"). The results came back 

> This PDF file contains an open action to be performed when the document is viewed. Malicious PDF documents with JavaScript very often use open actions to launch the JavaScript without user interaction. 

I wrote the original document and didn't knowingly add JavaScript. Does anyone know how to detect exactly where the problem is so I can eliminate it?

---

### Post by vasa1 on 2016-10-20
I googled for "PDF file contains an open action" and got quite a few hits:
[http://www.techsupportforum.com/forums/f112/is-this-a-virus-942633.html](http://www.techsupportforum.com/forums/f112/is-this-a-virus-942633.html) >>> possibly a false alarm
[https://blog.didierstevens.com/programs/pdf-tools/](https://blog.didierstevens.com/programs/pdf-tools/) >>> quite technical

But do you have this with all pdf files created by LibreOffice? Which version of LibreOffice?

Can anyone upload a file to check at virustotal? I've never tried.

BTW, could you post more of the output?

Did yours look like> PDFiD information
This PDF file contains an open action to be performed when the document is viewed. Malicious PDF documents with JavaScript very often use open actions to launch the JavaScript without user interaction.
This PDF document has 4 pages, please note that most malicious PDFs have only one page.
This PDF document has 29 object start declarations and 29 object end declarations.
This PDF document has 9 stream object start declarations and 9 stream object end declarations.
This PDF document has a cross reference table (xref).
This PDF document has a pointer to the cross reference table (startxref).
This PDF document has a trailer dictionary containing entries allowing the cross reference table, and thus the file objects, to be read.


or like this> PDFiD information
**This PDF file contains 1 JavaScript block.** Malicious PDF documents often contain JavaScript to exploit JavaScript vulnerabilities and/or to execute heap sprays. Please note you can also find JavaScript in PDFs without malicious intent.
This PDF file contains an open action to be performed when the document is viewed. Malicious PDF documents with JavaScript very often use open actions to launch the JavaScript without user interaction.
This PDF file contains an automatic action to be performed when a given page of the document is viewed. Malicious PDF documents with JavaScript very often use an automatic action to launch the JavaScript without user interaction.
**The combination of automatic actions and JavaScript makes this PDF document suspicious.**


I uploaded a test pdf file created by opening a text file in LibreOffice and saving it as a pdf file. So no javascript. This is what I got:

---

### Post by Buntu Bunny on 2016-10-20
vasa1, thank you for taking the time to help me. 

Output for the file I'm asking about (created in LO 5.1.4.2):

> PDFiD information
This PDF file contains an open action to be performed when the document is viewed. Malicious PDF documents with JavaScript very often use open actions to launch the JavaScript without user interaction.
This PDF document has 37 pages, please note that most malicious PDFs have only one page.
This PDF document has 303 object start declarations and 303 object end declarations.
This PDF document has 61 stream object start declarations and 61 stream object end declarations.
This PDF document has a cross reference table (xref).
This PDF document has a pointer to the cross reference table (startxref).
This PDF document has a trailer dictionary containing entries allowing the cross reference table, and thus the file objects, to be read.


I had to dig around for a pdf made with an earlier version of LO (3.5). It returned this:

> PDFiD information
This PDF file contains an automatic action to be performed when a given page of the document is viewed. Malicious PDF documents with JavaScript very often use an automatic action to launch the JavaScript without user interaction.
This PDF document has 101 pages, please note that most malicious PDFs have only one page.
This PDF document has 345 object start declarations and 345 object end declarations.
This PDF document has 190 stream object start declarations and 190 stream object end declarations.
This PDF document has a cross reference table (xref).
This PDF document has a pointer to the cross reference table (startxref).
This PDF document has a trailer dictionary containing entries allowing the cross reference table, and thus the file objects, to be read.

So one contains an open action, the other an automatic action. Both documents contain internal and external links, but to different places. 

Anyone can upload a file to VirusTotal. If you try it, I'd be interested in what you get.

---

### Post by vasa1 on 2016-10-20
I updated my post! See the part I "bolded".

And here's the output of a pdf receipt not produced by LibreOffice:> The file being studied is a PDF document! The document's header reveals it is using the following file format specification: %PDF-1.6.
 PDFiD information
 This PDF document has 1 page, please note that most malicious PDFs have only one page.
 This PDF document has 11 object start declarations and 11 object end declarations.
 This PDF document has 1 stream object start declaration and 1 stream object end declaration.
 This PDF document has a cross reference table (xref).
 This PDF document has a pointer to the cross reference table (startxref).
 This PDF document has a trailer dictionary containing entries allowing the cross reference table, and thus the file objects, to be read.
 ExifTool file metadata
MIMETypeapplication/pdf
ProducerOracle BI Publisher 11.1.1.5.0
PageCount1
PDFVersion1.6
FileTypePDF
LinearizedNo
FileTypeExtensionpdf
TypeInfo

---

### Post by Buntu Bunny on 2016-10-20
> **vasa1 said:**
> I updated my post! See the part I "bolded".

Okay, so yours had an open action as well. Could this have something to do with LibreOffice? I did not get output as in your second example (with bolded statements), only what I posted. 

For myself, I'm not concerned since I know I'm not trying to do anything malicious. My problem is that this particular PDF is to be submitted to be part of a group eBook bundle. I'm supposed to include a screenshot showing a green "pass" symbol. Mine is neither pass nor fail. My only alternative would be to remove all the hyperlinks and submit the PDF without them. :neutral:

---

### Post by vasa1 on 2016-10-20
I wonder if *any* pdf file gets a "green" :confused:

I wonder if hyperlinks have anything to do with green/red status.

IIRC, TheFu is quite knowledgeable about the insides of a pdf file and may drop in here!

---

### Post by ajgreeny on 2016-10-20
Try disabling java in LO in the Options dialogue, if you have it enabled at present, to see if a pdf produced by LO minus java overcomes this apparent risk.

Do you export the file to pdf in the File menu of LO or do you print to file and choose pdf? That also might make a difference to the problem.

---

### Post by vasa1 on 2016-10-20
> **ajgreeny said:**
> Try disabling java in LO in the Options dialogue, if you have it enabled at present, to see if a pdf produced by LO minus java overcomes this apparent risk.

Do you export the file to pdf in the File menu of LO or do you print to file and choose pdf? That also might make a difference to the problem.No java on my system. And I use export to pdf. 

++++

Okay, my starting file is a markdown file (= plain text). I opened it in Geany and chose print > print to file > pdf and that's a winner with virustotal! So seems it's something LibreOffice does that gets virustotal upset.

---

### Post by Buntu Bunny on 2016-10-20
ajgreeny, thank you for your help.

> **ajgreeny said:**
> Try disabling java in LO in the Options dialogue, if you have it enabled at present, to see if a pdf produced by LO minus java overcomes this apparent risk.

I disabled java but it made no change in the scan, i.e. I still have an "open action" 

> Do you export the file to pdf in the File menu of LO or do you print to file and choose pdf? That also might make a difference to the problem.

With the file menu. I tried to print to file but had no PDF option. It will only do this as a postscript file.

---

### Post by vasa1 on 2016-10-20
> **Buntu Bunny said:**
> ...
With the file menu. I tried to print to file but had no PDF option. It will only do this as a postscript file.
I'm not seeing that.

Let's say I have an odt file open. Then, File > Print > Print to file gives me a Save as window with **pdf as the only option** but the result still has an Open action and so doesn't get a green pass :(

This is with LibreOffice Version: 5.2.2.2 on Lubuntu 16.04.

+++++++++++++++++++++

I have an .odt file. Instead of opening it with LibreOffice, I open it with Abiword. Abiword can "save as" a pdf file.

That gets a green pass (on limited testing; it's my bedtime).

---

### Post by J_Me on 2016-10-20
@Buntu Bunny
I think LO sets the zoom level of the pdf by using Open Action.

> To open at 200% zoom onto the current page:

theDoc.SetInfo(theDoc.Root, "/OpenAction", "[ " + theDoc.Page.ToString() +" 0 R /XYZ null null 2 ]")

To fit the document width onto the current page:

theDoc.SetInfo(theDoc.Root, "/OpenAction", "[ " + theDoc.Page.ToString() + " 0 R /FitH " + theDoc.MediaBox.Height.ToString() + " ]")[URL="http://www.websupergoo.com/helppdfnet/source/5-abcpdf/doc/1-methods/setinfo.htm"]Here
[/URL]

---

### Post by Buntu Bunny on 2016-10-20
Wow, vasa1, your save as is totally different from mine (Xubuntu 16.04). I don't get to choose pdf as a save option. I have to export to pdf. 

I did find [this webpage]("http://www.aspose.com/docs/display/pdfnet/Add+and+Get+Hyperlink#AddandGetHyperlink-RemoveDocumentOpenActionfromaPDFFile") about open action, but it didn't help me with LO. I did discern that it has something to do with internal links, so I removed all the internal links in my document. VirusTotal still says it contains an open action. :(

---

### Post by Buntu Bunny on 2016-10-20
> **J_Me said:**
> @Buntu Bunny
I think LO sets the zoom level of the pdf by using Open Action.

[URL="http://www.websupergoo.com/helppdfnet/source/5-abcpdf/doc/1-methods/setinfo.htm"]Here
[/URL]

J_Me, if that's the case then there is probably no way to turn it off and get my document to clear. The folks requesting the VirusTotal scan are concerned about links. It would seem that even with no links it will still use open action, but with no links I don't suppose they'd care about the scan.

---

### Post by J_Me on 2016-10-20
I think your right, this is why I don't like these office suites as they always seem to 'do stuff' which I don't want.

---

### Post by Buntu Bunny on 2016-10-20
> **J_Me said:**
> I think your right, this is why I don't like these office suites as they always seem to 'do stuff' which I don't want.

Well, I have to agree with you there. I do most of my writing with gedit. It's plain, simple, has a spell check, word count, can alphabetize lists, and doesn't have that annoying pop-up to tell me what page I'm on. For print books I use Scribus and export in PDF. Ebooks, though, are a different ballgame. They are usually uploaded as .doc for which I only have LibreOffice. Since the file I want to use is already in LO, it makes sense to export it as a PDF from there, but you see the difficulties.

---

### Post by vasa1 on 2016-10-20
So did you try Abiword?

---

### Post by Buntu Bunny on 2016-10-20
Actually, no. LibreOffice replaced Abiword as of Xubuntu 15.10, but I hadn't thought to install it. It had it's own issues so I rarely used it in 12.04. It might be interesting to see what it can do now.

---

### Post by vasa1 on 2016-10-20
The reason I tried Abiword which, [for me]("https://ubuntuforums.org/showthread.php?t=2321942&p=13514069#post13514069"), displays well only with the Adwaita theme, was to see if it did the pdf thing differently. And apparently it does and its pdf files seem okay with virustotal.

I don't need to share stuff with Windows users, but if I did have to, I could still use LibreOffice for the heavy lifting and then later use Abiword to generate the Win-friendly pdf file from the odt.

---

### Post by ajgreeny on 2016-10-21
Abiword in 12.04 was terrible as you say, but a ppa allowed a previous version to be installed, and now in both 14.04 and 16.04 it is very reliable, in my opinion, so well worth trying in place of LO writer.

Incidentally, gnumeric is also very good and much faster than LO calc.

---

### Post by Buntu Bunny on 2016-10-21
> **vasa1 said:**
>  ...<snip> ... its pdf files seem okay with virustotal.

Well of course when you said that, of course I had to give it a try! The pdf it created was stripped of all images and all internal links. The links I can do without but really want the images, so I didn't even run the file through VirtualTotal.

> **ajgreeny said:**
> Abiword in 12.04 was terrible as you say, but a ppa allowed a previous version to be installed, and now in both 14.04 and 16.04 it is very reliable, in my opinion, so well worth trying in place of LO writer.

Hmm. Except I got the same flickering mentioned by the OP in the thread vasa1 linked to. And maybe because I opened an odt file (tried doc too) the formatting looked all wrong. I did not start from scratch, but if Abiword strips the pdfs of images (which I recall from previous usage) that is not a plus.

I downloaded from Software Center, does that make a difference?

> Incidentally, gnumeric is also very good and much faster than LO calc.

Definitely agree with you on that one.

---

### Post by vasa1 on 2016-10-21
Oops! That's a major problem. Assuming we're talking about an odt file created by LibreOffice Writer, were the images actually part of the document or links to images somewhere (or computer or elsewhere)? Files with the former option are much bigger but self-contained.

My Abiword is from the standard repo. I did mention using Adwaita helps get round the flickering.

---

### Post by Buntu Bunny on 2016-10-21
I think the thing to do would be to start working with Abiword for a fresh project, especially since there's a workaround for the flickering. Trying to jump in with it for something already in the works probably isn't a fair trial, although I seem to recall that the Abiword version in 12.04 always opened pdfs without images.

---

### Post by vasa1 on 2016-10-21
I made a small Writer file with an image incorporated. Exported it to pdf using LibreOffice. Image is included as expected.

Opened the same Writer file with Abiword. Saved as pdf. Image is included. I haven't used Abiword in 12.04 and so can't comment.

---

### Post by Buntu Bunny on 2016-10-21
I tried an Abiword test pdf, which I made by simply copying the ebook from LO and pasting into Abiword. It kept some of the images but not others. The worst part was that it totally skewed the formatting. But it did pass the TotalVirus scan with flying colors. 

My conundrum is whether to continue stripping links from the LO copy, or try to reformat the Abiword copy (but I'd also have to figure out how to not lose the photos). Either way will be a bit of work. I just wish I wasn't working on a rapidly approaching deadline.

---

### Post by vasa1 on 2016-10-21
What about online services? There seem to be several though I've not used any.

---

### Post by Buntu Bunny on 2016-10-21
I tried three of them. The first also used open action. The second was in continual conversion mode, and the third couldn't convert for some reason or another, but they'd be happy to sell me their program to download to my computer. :roll:

So right now I'm working with Abiword. I copied the original text and purged the LO metadata by pasting into gedit before copying and pasting into Abiword. I'm adding the images by hand and will do the links next. It isn't taking as long as I thought, but Abiword isn't intuitive for me so I feel like I'm stumbling around a bit when it doesn't do what I want.

---

### Post by vasa1 on 2016-10-22
Well, all the best and if that fails find someone with MS Windows and Adobe's software installed. I think Adobe's software may allow you to select/delete actions but, again, I have no personal knowledge of this :(

---

### Post by Buntu Bunny on 2016-10-22
I hadn't thought about Adobe software, but I suspect that's what most folks do. I'm going to have someone try it by converting to pdf with Word, but I recall that docx files created in LO end up with extra spaces when Word gets ahold of them. 

I'm liking quite a few things about Abiword, but it's doing some quirky things (like rearranging formatting when I opened the file this morning.) Maybe I'll work with it more once I get this project behind me.

I'll follow-up with what finally worked, for anyone who comes along later looking for an answer to the same problem. Likewise if I ever find out anything more about LibreOffice.

---

### Post by Buntu Bunny on 2016-10-26
This is a follow-up to my problem, for which I have found workarounds but not a solution. 

The only other place I knew to ask was at the LibreOffice forum, but I've had no replies so I guess no one over there knows either. I'm guessing this is just the way LO is and that's that.

*Workarounds:*

Abiword's pdf did indeed pass the scan, but I had to rebuild the document, i.e. I couldn't simply import my LO document into Abiword without some difficulties in the pdf conversion.

Word also created a pdf that passed the scan. Because I had a deadline that's what I ended up doing - sending the file as docx to someone with Word and having them convert it for me.

Anyway, I appreciate all the responses and help I received here (my go-to whenever I have a computer related problem). At the very least I've found Abiword to be much improved than several versions ago, and for some things preferable to LO. That is something good to walk away with.

---

### Post by vasa1 on 2016-10-26
> **Buntu Bunny said:**
> ... I'm guessing this is just the way LO is and that's that.

...
Maybe file a bug?

---

### Post by Buntu Bunny on 2016-10-26
But I don't think it's a bug. It appears to be Java script added to determine how the document is opened in a pdf viewer ("[PDF Open Action]("http://www.hiqpdf.com/documentation/html/28e00c7d-bb5b-4d35-a00a-57a2b2b03304.htm")").

I did find a web article, "[Remove Document Open Action from a PDF file]("http://www.aspose.com/docs/display/pdfjava/Remove+Document+Open+Action+from+a+PDF+file")," but it's way over my head.

---

### Post by vasa1 on 2016-10-26
If not a bug, it could be a feature request. I'm not sure anyone has pointed out to the devs that their method of generating a pdf file makes their pdf files seem suspicious as far as virustotal is concerned.

---

### Post by Buntu Bunny on 2016-10-26
That's an excellent idea. Where would I go to make a feature request?

---

### Post by vasa1 on 2016-10-26
According to [https://wiki.documentfoundation.org/QA/BugReport](https://wiki.documentfoundation.org/QA/BugReport), > At a certain point what look like bugs are actually more like feature requests, where we know how the software should work in an ideal world, even though the feature we want hasn't been built yet. Fortunately, you don't have to worry that much about separating bugs from feature requests. If it's something that interferes with normal, valid use of the application, report it as a bug.
So I'm guessing that page would be a good starting point.

---

### Post by Buntu Bunny on 2016-10-31
Okay, finally jumped through the hoops to do that. We'll see what happens.

---

### Post by vasa1 on 2016-10-31
> **Buntu Bunny said:**
> Okay, finally jumped through the hoops to do that. We'll see what happens.
Great!

---

