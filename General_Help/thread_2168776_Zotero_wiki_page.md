---
title: "Zotero wiki page"
date: 2013-08-19
forum: General Help
---

### Post by Andrew_Lucas on 2013-08-19
As a student, writing essays and managing citations is a must.

I'm big on FOSS, so when I heard about Zotero, it was the natural home for me. I installed the stand alone program, and the Firefox/LibreOffice plugins.

I've just got a new laptop, so had to do a clean install, including a fresh copy of Zotero. Installation proceeded well (extract the package, mv /opt, add the plugins). I was happy and just doing some configuration of the preferences/settings, and hit a wall with the xpdf installation. No worries, I thought - a quick Google search sent me to the Zotero page, which wasn't especially clear regarding manual xpdf installation. I decide to see if there's a (X)ubuntu specific guide, and this led me to the Ubuntu wiki page.

The last edit was "2012-06-04 00:52:30" according to the page history, and the page refers to v2.x whereas my Zotero installation is v4.0.11. It's got an "immutable page" tag, so I can't see anyway to bring it up to date myself (which I'd be more than willing to do, if I could). Is anyone on the forum interested in doing the work?

It also isn't helpful at all with regards to xpdf installation. Can anyone give advice on installation? The Zotero page [here]("http://www.zotero.org/support/pdf_fulltext_indexing#advanced_installation") seems to suggest it's just a case of downloading from the xpdf site, and putting the binaries for your architecture into ~/.zotero. The install readme however inside xpdf states:

"[I]To install this binary package:

1. Copy the executables (xpdf, pdftotext, etc.) to to /usr/local/bin.

2. Copy the man pages (*.1 and *.5) to /usr/local/man/man1 and
   /usr/local/man/man5.

3. Copy the sample-xpdfrc file to /usr/local/etc/xpdfrc.  You'll
   probably want to edit its contents (as distributed, everything is
   commented out) -- see xpdfrc(5) for details.[/I]"

Can anyone give any guidance here?

---

### Post by tgalati4 on 2013-08-19
Open a terminal:

```
apt-cache search xpdf
```

If you see xpdf, then it's a matter of:

```
sudo apt-get install xpdf
```

Then you can get back to writing.  Don't forget to add the zotero plug-in for firefox--it's handy as well.

---

### Post by Andrew_Lucas on 2013-08-22
Cheers, I downloaded/installed the package. And well ahead of you with the plugin :D.

Will Zotero point to it automatically? The line about putting the xpdf binaries into ~/.zotero through me a bit, isn't it suggesting it needs a manual installation inside your home folder rather than a system wide installation of xpdf?

It's not a problem since I'm not using Zotero much at the moment anyway. :P It might become one towards the end of September, though, and obvs I'd rather have everything sorted before then.

---

### Post by tgalati4 on 2013-08-22
In Firefox, you can set which application you use to open PDF's.  You can use xpdf, evince, acroread (Adobe, proprietary).  Within your file manager preferences you can do the same thing.  I haven't used the native Zotero app, but there may be a similar setting.  The operating system handles files by their MIME type, based on the extension and any file headers.  So it should work automatically.  I don't know why you would need to install it within the zotero directory, unless you are migrating your work on a flash drive and you want zotero to work with xpdf wherever you plug it in.

---

### Post by Andrew_Lucas on 2013-08-25
> **tgalati4 said:**
> In Firefox, you can set which application you use to open PDF's.  You can use xpdf, evince, acroread (Adobe, proprietary).  Within your file manager preferences you can do the same thing.  I haven't used the native Zotero app, but there may be a similar setting.  The operating system handles files by their MIME type, based on the extension and any file headers.  So it should work automatically.  I don't know why you would need to install it within the zotero directory, unless you are migrating your work on a flash drive and you want zotero to work with xpdf wherever you plug it in.

I've set Aurora (I've yet to find a bug which makes the programme unusual, and like the newer features) to open PDFs. I've no need to have a portable Zotero, but we'll see how things go, and if any problems appear down the line.

Thanks for your help!

---

### Post by Bucky Ball on 2013-08-25
*Thread moved to **General Help**.*

***The Cafe*** is not for support threads. Thanks.

PS: Zotero rocks! But I've never installed any of the stuff you're talking about. Only ever the standalone and the Firefox plugin. All fine. 

Why does xpdf need to be installed manually? 

PPS: Not sure if you're using the Libreoffice/Openoffice word processor plugin. If you're not, you should be. Gives a Zotero toolbar right in your word processor. Click 'Add Citation' icon and a Zotero window pops up, choose citation, add page number, hit okay. Footnote done. Hit 'Create bibliography' icon and a bibliography including all the refs used in the document is added. Easy as (I'm in my last year of honours and Zotero has been my best friend re. referenceing for the last six and a half years).

---

### Post by Andrew_Lucas on 2013-08-25
> **Bucky Ball said:**
> *Thread moved to **General Help**.*

***The Cafe*** is not for support threads. Thanks.

PS: Zotero rocks!

Agreed!

Thanks for the move, though the main point of the post was to try and get someone to edit the wiki page for Zotero - should I deal with that separately in a new thread (in Cafe?)

Thanks.

---

### Post by Bucky Ball on 2013-08-25
> **Andrew_Lucas said:**
> Agreed!

Thanks for the move, though the main point of the post was to try and get someone to edit the wiki page for Zotero - should I deal with that separately in a new thread (in Cafe?)

Thanks.

No. You should deal with it in the Zotero forum. 

[https://forums.zotero.org/](https://forums.zotero.org/)

This is a support forum for Ubuntu and looking for people to edit the Zotero wiki pages does not really fit in any of the sub-forums here. You might as well post on a Windows forum or Mac forum as there are just as many Zotero users there I'd imagine, but not sure if you'd get much help there, either. You'd be relying on someone stumbling on your thread that actually uses Zotero for one and actually has the same issue and knows what you are talking about secondly. Your queries belong with the Zotero community proper if you're looking for action on this.

If you want to know what's going on with the Zotero wiki it is the logical place to ask.

***Cafe*** is for general discussion of a light-hearted nature, as you might have around a water-cooler. You're asking a support question. ;)

* Here's a quick sniff on xpdf @ Zotero forum:

[https://forums.zotero.org/search/?PostBackAction=Search&Keywords=xpdf](https://forums.zotero.org/search/?PostBackAction=Search&Keywords=xpdf)

---

### Post by Andrew_Lucas on 2013-08-25
> **Bucky Ball said:**
> No. You should deal with it in the Zotero forum. 

[https://forums.zotero.org/](https://forums.zotero.org/)

This is a support forum for Ubuntu and looking for people to edit the Zotero wiki pages does not really fit in any of the sub-forums here. You might as well post on a Windows forum or Mac forum as there are just as many Zotero users there I'd imagine, but not sure if you'd get much help there, either. You'd be relying on someone stumbling on your thread that actually uses Zotero for one and actually has the same issue and knows what you are talking about secondly. Your queries belong with the Zotero community proper if you're looking for action on this.

If you want to know what's going on with the Zotero wiki it is the logical place to ask.

***Cafe*** is for general discussion of a light-hearted nature, as you might have around a water-cooler. You're asking a support question. ;)

* Here's a quick sniff on xpdf @ Zotero forum:

[https://forums.zotero.org/search/?PostBackAction=Search&Keywords=xpdf](https://forums.zotero.org/search/?PostBackAction=Search&Keywords=xpdf)

I didn't make myself clear. It was the ***ubuntu***wiki, the "Zotero" article. [This]("https://help.ubuntu.com/community/Zotero") page.

---

### Post by Bucky Ball on 2013-08-25
Ah, apologies. ;)

So you are asking why you can't edit the page and, when you can, does anyone want to help get it up to date?

As for xpdf help, I would still try the Zotero forums as well. They aren't bad.

---

### Post by Elfy on 2013-08-25
> **Andrew_Lucas said:**
> ... It's got an "immutable page" tag, so I can't see anyway to bring it up to date myself (which I'd be more than willing to do, if I could). Is anyone on the forum interested in doing the work?...

> **Andrew_Lucas said:**
> I didn't make myself clear. It was the ***ubuntu***wiki, the "Zotero" article. [This]("https://help.ubuntu.com/community/Zotero") page.

You now have an SSO account - so you should be able to login to the wiki, once done you should then be able to edit it.

You might find it easier to login via here - [https://help.ubuntu.com/community/](https://help.ubuntu.com/community/) and then go to [https://help.ubuntu.com/community/Zotero](https://help.ubuntu.com/community/Zotero) - hopefully it willr ecognise you've logged in.

I find sometimes that wiki refuses to see that I'm logged in - patience and keep trying gets me there eventually.

Hope that helps

---

