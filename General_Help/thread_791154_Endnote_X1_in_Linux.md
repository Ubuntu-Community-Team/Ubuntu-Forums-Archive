---
title: "Endnote X1 in Linux"
date: 2008-05-11
forum: General Help
---

### Post by mr_brefast on 2008-05-11
Hello Everyone:

I am not sure how many people here will have used the Windows program EndNote X1, so let me explain it really quickly.

It allows a user to "Cite While You Write," as its called, meaning that your Microsoft Word is upgraded to include a new toolbar.  Amongst other buttons, it allows you to press one button and have the appropriate material be referenced where your cursor left off in the document, and then you can add page numbers &c.

Now, the problem arises with Wine that you cannot even open EndNote in it (I tried to yesterday).

Does anyone know of any way to make it work in Linux, either with Word in Wine (as I have already gotten working) or with OpenOffice or Abiword (I am personally using Xubuntu 8.04 on a Thinkpad T22 if that helps)?  I will not have access to a Windows machine this entire summer, and this 110 page paper would be infinitely easier to do with this program enabled.

My thanks in advance, and have a good evening all

-Brefast

---

### Post by daengbo on 2008-05-12
I hope someone has the answer to your question. I know that I don't. I will, however, tell you what I use to write and cite. I do about 600 pages of NF a year for publication.

OO.o has a biblioraphic database, but it's pretty weak.

Instead, I use Lyx and Referencer. It's a great and powerful combination. Pybliographer is supposed to be really good for citations, too. Latex (the backend for Lyx) is exceptional at handling citation and indexes, and it'll make your writing simple.

I suspect that you want to use MS Word, though, so this advice is probably useless for you.

---

### Post by tacutu on 2008-05-12
Jabref is a wonderful tool, but it is LaTeX-oriented and pretty well integrated with LyX.
But that probably won't cut it for you...

---

### Post by tenuki on 2008-05-12
I really recommend Bibus:

[http://bibus-biblio.sourceforge.net]("http://bibus-biblio.sourceforge.net")

Does online searches for references or can import data in variety of formats. Also talks to OpenOffice to allow citation formating.

---

### Post by mr_brefast on 2008-05-13
My thanks to everyone who replied - I have looked into each of the options concerned, and unfortunately none of them are as easy to use with the in-text citations as Endnote is (unless I am missing something, then please correct me).

I am not averse to using a different word processor to make citations easier, except it needs to be translatable to .doc format for the purposes of turning it in (silly monopoly over the market).  Any suggestions from what has already been posted that would make that possible?  If not, how easy is Lyx to get used to, and then would it be possible to simply copy and paste entire finished documents into Word for purposes of turning it in?  Thanks in advance.

-Brefast

---

### Post by r76 on 2008-05-14
try [zotero]("http://www.zotero.org/")

recommended [here]("http://ubuntuforums.org/showpost.php?p=4745746&postcount=29"), it is opensource, web-based and should work with either Word or OOo, although I haven't tried it myself. :)

---

### Post by tenuki on 2008-05-14
Hi again,

Are you sure the combination of Bibus + OpenOffice doesn't do what you want? I used to use Endnote + Word a lot for writing scientific papers, and also Endnote alone for downloading and organizing references. Since then, I have found that I can completely replace the combo with Bibus+Ooo (except when a collaborator insists on sending a .doc with Endnote refs in - which Ooo can't cope with).

Refs can be loaded into Bibus as per Endnote, and then inserted into OpenOffice docs as you would with Word. You can then format your bibliography to a particular journal format just as I used to do using Endnote. OpenOffice can also save in .doc format, although little bits of the formating tend to look a bit different in Word/Ooo.

Is this the sort of thing you are currently doing with Endnote X1 + Word, or are you looking to do something else?

---

### Post by chewym on 2008-05-16
Hi,

I have EndNote X1 working under Ubuntu Hardy. It generally works fine, however extended latin characters (diacratic marks etc) do not display properly in the preview pane. 

I could not use the installer from the CD. I copied the entire program directory (eg "Program Files\EndNote X1\") from a Windows installation.

You will need to copy some dll and manifest files from your windows installation - search for the following and copy into the EndNote program directory:
gdiplus.dll
mfc80.dll
mfc80u.dll
Microsoft.VC80.ATL.manifest
Microsoft.VC80.CRT.manifest
Microsoft.VC80.MFC.manifest
Microsoft.VC80.MFCLOC.manifest
msvcm80.dll
msvcp80.dll
msvcr80.dll

I also installed the following from Winetricks (not sure if all of them are needed):
vcrun2003
vcrun2005
vcrun2005sp1

Good luck!

---

### Post by chewym on 2008-05-16
Also, I cannot say whether Cite While You Write works in Wine. 

I am using OpenOffice.org and the RTF scan feature in EndNote.

---

### Post by mr_brefast on 2008-05-16
> **tenuki said:**
> Hi again,

Refs can be loaded into Bibus as per Endnote, and then inserted into OpenOffice docs as you would with Word. You can then format your bibliography to a particular journal format just as I used to do using Endnote. OpenOffice can also save in .doc format, although little bits of the formating tend to look a bit different in Word/Ooo.

So I have downloaded Bibus (the first time I tried it, I did something wrong but its running now).  The problem arises that I try to configure Openoffice to work with Bibus using the "First Connection Wizard" and it doesn't ever work - I am unable to cite anything in Openoffice.  Could you help me out configuring it?

To everyone else, I appreciate all the suggestions and have tried them each in turn; Bibus really seems to have everything I need and would like to have for this machine.  On the other hand, this thread will probably help a bunch of other people too.

-Brefast

---

### Post by tenuki on 2008-05-18
> **mr_brefast said:**
> So I have downloaded Bibus (the first time I tried it, I did something wrong but its running now).  The problem arises that I try to configure Openoffice to work with Bibus using the "First Connection Wizard" and it doesn't ever work - I am unable to cite anything in Openoffice.  Could you help me out configuring it?


Sure thing. I'll help out if I can. 

I've got the bibus+OOo combo working on a Debian etch machine and in Gutsy - both with bibus1.4.0 and OOo2.3.  I'm trying to think back to remember if there were any problems, but don't think so.  I think I just followed the installation as seen here:

[HTML]http://bibus-biblio.sourceforge.net/wiki/index.php/Installation#Ubuntu[/HTML]

... but it was a while ago, so I can't guarantee it.

Could you let me know which versions of bibus, OOo and Ubuntu are you using, and the error the first connection wizard is giving?

---

