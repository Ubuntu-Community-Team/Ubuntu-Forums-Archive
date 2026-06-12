---
title: "Simple HTML Editor"
date: 2013-01-27
forum: General Help
---

### Post by asearle on 2013-01-27
Hi Everyone,

I currently use "Kompozer" (the Mozilla HTML editor) to make changes to simple web sites.  The tool isn't sophisticated but works fine.

The thing I like about it is that it includes a "publishing button" so that I can make changes and then click on "publish".

But this is an old tool which is no longer supported and also I have noticed that sometimes the publishing fails (or even worse) it publishes to the wrong site (in a number of sites are declared).

So now I am looking for an alternative and was wondering if anyone can recommend a simple tool (that doesn't clutter up the HTML as OpenOffice does and which has a "publish" feature).

Any tips would be most gratefully received.

Many thanks,
Alan Searle

---

### Post by Lars Noodén on 2013-01-27
The other one to look at would be Bluefish.

---

### Post by asearle on 2013-01-27
Hallo Lars,

Yes, Bluefish looks good ... but its not WYSIWYG, is it?  i.e. I need to write the HTML as code rather than creating it as in a word processor as is the case with Kompozer.  Or have I overlooked something?

That's not really a problem because it is OK for me to code directly to HTML and Bluefish has a nice browser-preview function.  But maybe there is a WYSIWYG-editor that I have missed.

And also with Bluefish I couldn't see a "publish" option.  Or should I better write a little command-line FTP script to do the publishing?  If so, then maybe someone out there has a little example that I could use as a basis?

Many thanks for any tips that you can give.

Yours,
Alan Searle

---

### Post by Lars Noodén on 2013-01-27
Well no HTML editor can be WYSIWYG because HTML has a separation between structure and formatting.  Bluefish does have a preview button which will show you the page in your browser, so you can see what it looks like on your screen with your desktop settings and your browser and browser settings.  But others, even with similar setups, will have a slightly different configuration and thus slightly different final appearance.  Best not to worry too much about that since it is part of the nature of HTML.

Bluefish does have an upload feature which supports SFTP.  You can find it under File->Upload / Download.  I'm not sure how advanced it is, but it does seem to have a fair amount of functionality.  However, I usually upload via the regular SFTP client in the shell or use rsync.  rsync also supports SSH by default.  I'd [avoid FTP](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp).  It's insecure.

---

### Post by asearle on 2013-01-27
Hi Lars,

Thanks for the feedback.  I'd get stuck in and give Bluefish a serious try.

And I'll look into SSH / rsync.  That sounds like good advice.

Many thanks,
Alan

---

### Post by ProxyCyber on 2013-01-27
> **asearle said:**
> So now I am looking for an alternative and was wondering if anyone can recommend a simple tool

Hi,


I'm sorry if I'm a bit off, but I've always LOVED Blogger for testing CSS, HTML codes. It's like making a website, but you can test with it. I do it all the time, whenever it is I need to test HTML. It's truly the best. Try it out and see what you think. 

You can test in settings

HTML
CSS
XML

and lots more. I don't actually use Software, I prefer Blogger's version considering I'm an internet user mostly, with Tor too. I'm not sure but I once used CodeBlocks.

---

### Post by andrew.46 on 2013-02-13
> **asearle said:**
> Thanks for the feedback.  I'd get stuck in and give Bluefish a serious try.

Good time to look at Bluefish as a new version, 2.2.4, has just been released!

---

### Post by lykwydchykyn on 2013-02-13
Haven't used it myself, but as I understand it [BlueGriffon](http://bluegriffon.org/) is picking up the Kompozer/Nvu torch.  It's not in the repositories, but they have downloads for Ubuntu on the website.

---

### Post by d4m1r on 2013-02-13
What's wrong with the built in notepad app in Ubuntu or something like Notepad++? ;)

---

### Post by trestevenson on 2013-02-26
Notepad++ might not be too bad of an idea!  I'll have to look into that...

---

