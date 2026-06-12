---
title: "Suggestions on how to display SOP PDF Documents on an internal only Webpage"
date: 2014-03-27
forum: General Help
---

### Post by greavette on 2014-03-27
Hello,

We would like to serve up our SOP PDF Documents on a webpage to be served up to our internal workstations only.  We would need our users to be able to read the PDF documents in the browser only...we do not want the document downloaded to open it.  We don't want anyone to copy these documents so ideally it would be beneficial to just read the documents only.

Organizing the documents into sections and a search function would be ideal as opposed to just creating a webpage of a list of 50 documents which doesn't look very useful.  

Any ideas what we could use?  

Thank you.

---

### Post by TheFu on 2014-03-27
If the documents can be viewed, then they can be copied. Get over it.  You can only make it harder or use watermarks to make it clear that non-online versions are "uncontrolled" and invalid. I've seen that many places.

Whether it is downloaded first or viewed inside a webpage is largely based on the web browser settings.  Chrome and chromium both will display PDFs inside the browser by default. I don't know about other platforms. Firefox might if a certain plugin is loaded. It is client-side.

I really wish companies would stop using page layout document formats when HTML works fine, especially for policy documents.  HTML should be the DEFAULT document format, unless there is a strong reason to use something else.

If you don't want documents copied, don't publish them as a document. Think about publishing them as paragraphs or sections - wiki-like. Using HTML (not PDF) would be the first step. There are tools that will do that, but those are not generally used by average document creators.  FAQ-o-Matic comes to mind.  O'Reilly has published many of their books online in this way too.  The "Perl Bookshelf CD" is one that comes to mind. I think they use DocBook. [http://www.docbook.org/](http://www.docbook.org/)

Plus searching/indexing HTML is much easier than PDFs.

---

### Post by greavette on 2014-03-27
Thank you for the reply and suggestions.

We'll be using Chrome/Chromium as our primary browser so yes the PDF documents will be viewed within the browser.  The workstations used by the employees are thin clients without email installed and no Internet Access so no one can attach a USB key or email the documents if downloaded so we are safe that way.  I know people can still use a cell phone to take pictures so we are not totally safe, but with the safe guards we have in place we are satisfied.

Owners of the company are creating the PDF documents with protection enabled.  I wasn't part of that decision on what format to use.  There is no capacity unfortunately to convert these documents to any other format like HTML.

I've been asked to serve these up to their employees easily.  Easy in my mind is on a local webpage everyone in the office can access.  For now we are using Simple Groupware where I've setup a share that the owner can save the PDF file into.  Simple Groupware views the files in that share and serves them up.  I've setup each workstation to auto-open a PDF by default in Chrome/Chromium.  Although this system is working for employees to read the SOP's online, the look of the PDF's in Simple Groupware is ugly.  We are looking for serving up these documents as a webpage that groups the documents by task or function.  Something that looks better than we currently have.

Any other ideas are most welcome on what we can use.

Thank you!

---

### Post by greavette on 2014-04-04
Just thought I would post my findings so far....

I've installed ownCloud on my Ubuntu Server and I think this will do what we need.  I can create a folder of our SOP documents.  The folder will be mounted to my ownCloud server (NFS Share from our NAS).  I can create a share to the SOP folder and save a Google Chrome Application Shortcut to this ownCloud share on each workstation in our office so users can easily view all procedures.  There is a PDF viewer available with ownCloud for users that login to ownCloud.  I won't be using this since I'm using a share instead. There is supposed to be a PDF viewer when using a share but it's currently not working so within Chrome on each workstation I will set it up to auto open PDF files in Chrome.  When the PDF viewer is fixed I won't have this issue any longer.

---

### Post by tgalati4 on 2014-04-04
You can organize the PDF's into categories.  Stick to the "Rule of 12's", no more than 12 categories.  You can have PDF's listed in multiple categories.  You can use symbolic links for the duplicates, or simply copy them into multiple, appropriate folders.  You can use RSS feed publishing (as well as emails) to announce when the handbooks are updated with new policies.

For Human Resource purposes, it's a good idea to track the reading of the policies to avoid legal issues going forward.

---

### Post by TheFu on 2014-04-04
Make certain that full-text search works, especially if there are more than a few documents.
If the users cannot find the document they need, then they will use their memory instead.  No matter how good our memories are, we all make mistakes.

I worked in document management for a decade - legal, NASA, IT security standards, technical documentation for aircraft ... it all comes down to good organization, and Full-Text Search that WORKS.  Without that, forget it.  Many search engines do a good job with non-scanned PDF files.  It is possible to hook up **recoll** to a web search page.  My friend JoshR wrote "[how to index anything]("http://www.linuxjournal.com/article/6652")" in the mid-1990s - the ideas are all the same today as back then.

---

