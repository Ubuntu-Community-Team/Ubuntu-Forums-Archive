---
title: "Trying to get an OCR solution to work"
date: 2020-01-17
forum: General Help
---

### Post by ivotkl on 2020-01-17
Greetings and happy 2020 everyone.

I've been trying to get a server (Ubuntu Server Bionic) to work with [opensemanticsearch]("https://www.opensemanticsearch.org/") or [Elastic Stack]("https://www.elastic.co/guide/en/elastic-stack-get-started/current/get-started-docker.html") on Docker.

However:
1. Opensemanticsearch does not seem to recognise characters on PDFs (I downloaded the server .deb package installation goes fine, a folder is added where images and documents are). Tesseract OCR is installed.
2. Elastic Stack implementation runs smoothly, but I don't know how to add the folder where the files are located. Ingest Attachment Processor Plugin is installed as well.

Any light thrown on the subject would be highly appreciated, whether it is this solution or another 100% or so working one. Basically, the server would take files from a network folder and then recognise words in them using OCR. Files are mainly invoices.

Thank you very much and best regards,
Iván.

---

### Post by TheFu on 2020-01-17
Not all PDFs have text inside them. Some are purely bitmap scans.  The trick is to get the image run through an OCR that places the text _under_ the image on the page.  **gscan2pdf** can do that.  Then you place the resulting PDF files into your normal file organization - yyyy/mm/ setup and run the indexer of your choice.  Last time I used OCR, I had to manually add keywords so that the document would be found later, if needed.

PDFs directly provided by vendors - like a brokerage statement - don't need any OCR and can almost always be indexed perfectly.

I decided all this effort wasn't worth my time and switch to a simple, time-based, paper filing system and manually entering each transaction into our accounting program.  More details are entered for more expensive purchases, especially those with warranties.  That's the only reason any of this is useful to us.  Getting warranty service. 

As for indexing of files, I've found **recoll** to be excellent.

---

### Post by ivotkl on 2020-01-17
> **TheFu said:**
> Not all PDFs have text inside them. Some are purely bitmap scans.  The trick is to get the image run through an OCR that places the text _under_ the image on the page.  **gscan2pdf** can do that.  Then you place the resulting PDF files into your normal file organization - yyyy/mm/ setup and run the indexer of your choice.  Last time I used OCR, I had to manually add keywords so that the document would be found later, if needed.

It's a nice workaround, but the thing is that I'm planning on implementing this on the place I work at and it needs to be a webserver that does everything almost automatically and manually tagging nearly 50k documents / images is a no-go from the start :lolflag:.

Any other ideas?

---

### Post by TheFu on 2020-01-17
I worked in Document Management Systems at some huge companies from 1995 - 2007, some were art-centric systems, but most were either conversions from older systems or for archival data.

Pay Xerox.

---

### Post by TheFu on 2020-01-18
Turns out the OCR NC addon isn't stable. Sorry.   [https://apps.nextcloud.com/apps/ocr](https://apps.nextcloud.com/apps/ocr) if you'd like to get familiar.  Nextcloud is an impressive platform for all sorts of business needs.

They are working on it.  Claim it works with images, but PDFs seem to need extra time.  If you do create PDF files, best to stay with PDF version 1.6 for the most compatibility on F/LOSS.  Commercial tools like Acrobat will default to newer versions of the PDF standard which is problematic for Linux users trying to avoid commercial software.

---

### Post by ivotkl on 2020-01-20
> **TheFu said:**
> Pay Xerox.

I did not quite get the meaning of this.

Anyway, I guess I'll keep on searching on my own and waiting for a reply here as well.

Thanks.
Regards,
Iván.

---

### Post by TheFu on 2020-01-20
You asked "any other ideas?"
I answered, "Pay Xerox."

Xerox is a professional document and image scanning and management company which is expert at this sort of stuff.  I've used them at work for similar needs. Their prices are outside what a home user would spend, but for a business, they could be what is needed and in a few weeks you'd have a solution.

I miss the pizza from El Cuartito! Everywhere I travel, I seek better. Haven't found it and I've been subjected to some really bad pizza in that search.

---

### Post by ivotkl on 2020-01-21
Ok, thanks for the idea but I was asked to make an open source solution, hehe. It looks like you are working for Xerox. :lol: (Just joking).

I could not believe my eyes when I saw El Cuartito pizzeria on your reply hahaha.

If you ever come back to Buenos Aires, there other good pizza places you could visit, Güerrín is one of them.

---

### Post by TheFu on 2020-01-21
> **ivotkl said:**
> Ok, thanks for the idea but I was asked to make an open source solution, hehe. It looks like you are working for Xerox. :lol: (Just joking).

I could not believe my eyes when I saw El Cuartito pizzeria on your reply hahaha.

If you ever come back to Buenos Aires, there other good pizza places you could visit, Güerrín is one of them.

I understand the desire to use only F/LOSS.  We are the same way.  Sometimes F/LOSS doesn't do what we need or we can't bend it to our requirements.  

I tried to get the packaged version of tesseract-OCR working here.  Used both the **Lios** front-end and directly with the CLI tesseract tool.  If you are dealing with the same input forms all the time, then setting up a special tesseract config would be the way to go.  
Lios locked up a few times to the point I had to kill it from another terminal and the OCR was perhaps 90% accurate.  That's just enough to drive us crazy since most of the words are fine, but any complicated words were not.  Also, it routinely didn't get my first name correct, one of the most common first names in the USA.  Lios only works on 1 page at a time. That's a big limitation.

Looked to install gscantopdf and it wanted to install a bunch of stuff - 35MB worth - so I cancelled the install on that machine.  I'll keep using it on other box.  The OCR accuracy doesn't appear to have changed much the last 5-10 yrs, unfortunately.  Plus, putting the text under the PDF image is really what I need.
 
But all my production systems are on 16.04, so perhaps I'm only seeing the older versions.  18.04 could have much newer/better results.  IDK.  I'm running into that issue with some TTS work.

---

