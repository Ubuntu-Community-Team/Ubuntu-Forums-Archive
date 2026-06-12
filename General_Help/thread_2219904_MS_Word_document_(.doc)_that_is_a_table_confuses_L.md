---
title: "MS Word document (*.doc) that is a table confuses Libreoffice writer"
date: 2014-04-25
forum: General Help
---

### Post by cigtoxdoc on 2014-04-25
One of my clients sent me a MS Word document (*.doc) that only contains a table (13 inches wide by 50+ inches long, no apparent page breaks).  File was attached to an e-mail received with Evolution 3.2.3.  I opened the attachment with Libreoffice Writer (4.2.3.3).  The document opened and appeared to be correct, but then I found that pp 2-29 were all the same.  I used the Preview in Web Browser, and found that there were 11 distinct papges, but there appeared to be no way to deal with the issue.  I e-mailed the person who sent it to me and he confirmed 9 pages.  I sent the document to one of my webmails, rebooted PC into Win XP Pro SP3, retrieved the document, and opened it with MS Word 2007.  Nine pages, legal size.  I changed the page size to letter, saved it, and printed it out so I would have a copy for a meeting I need to attend.  I went back into Ubuntu and pulled the document from the ntfs partition with Libreoffice writer, and it is still a mess.  Quite frankly, I I had not kept the ntfs partition inclduing OS and Office 2007, and set the PC for dual-boot when I installed Ubuntu, I would be in deep trouble.  I have checked around on the Internet, and there does not appear to be a Ubuntu-based solution to this.

What am I missing.

John

---

### Post by amanchesterman on 2014-04-26
This issue (exchanging and editing documents between MS Office and Libre Office) is a constant problem, as you've probably discovered from your search on the net.

The clearest summary I have found is here: [http://en.libreofficeforum.org/node/7505](http://en.libreofficeforum.org/node/7505) . As it says, the MS Word .doc format is not and probably never will be completely compatible with LO Writer. In my experience it's usually OK if the Word document is fairly straightforward (just headings, paragraphs of text etc.), but anything long and complex (e.g. with embedded fields, forms, graphs etc.) is likely to be problematic.

In the situation you describe (where, as I understand it, your client has sent you a document that you don't need to edit, just for information) then the best solution by far is for them to send it to you as a pdf. That's why it's called *Portable* Document Format: it's designed to look the same on your computer as it does on theirs, whatever operating systems are being used. I believe that MS Word can export a document as a pdf (LO Writer certainly can).

If you are sent a .doc file that you need to edit, then in addition to LO you could try SoftMaker Office. There is a free version (you pay for extra features) and I have found it runs happily on various Ubuntu-based distros. Sometimes it seems better than LO at displaying some aspects of MS Word documents, but in my experience it's not perfect.

A third solution which I have adopted for occasional use is to create an email account with Hotmail. I use it purely for the office applications: like Google mail, it comes with free online storage for documents and files, and anything you upload to storage you can then open and edit with MS Office online. Apart from the fuss of having to upload the documents, I've found it works perfectly, and of course it copes with the latest MS Word formats as well as the older ones. And it's free. :)

I hope that helps.
John

---

### Post by cigtoxdoc on 2014-04-26
Thank you for your suggestion.  First, in my business (scientific consulting) the client's format is always the correct format.  Second, opening document in LibreOffice and exporting as PDF produced 29 pages of junk.  Forwarding the client's e-mail to backup Ubuntu with Kingsoft Office on it solved the problem.  Kingsoft writer opened file correctly the first time.  I don't like to use Kingsoft on a regular basis because it does not spot repeated words and lacks a grammar checker.  I have yet  to try Softmaker.

John

---

### Post by amanchesterman on 2014-04-26
I haven't tried Kingsoft Office for Linux yet, but I installed it the other day on my Windows PC and I like the look of it: since you find that it works OK on Ubuntu I will give it a try.

If you feel that your query has now been solved please mark this thread as such.

Good wishes
John

---

