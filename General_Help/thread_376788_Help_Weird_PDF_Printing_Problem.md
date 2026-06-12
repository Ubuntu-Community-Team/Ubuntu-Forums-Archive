---
title: "Help: Weird PDF Printing Problem"
date: 2007-03-05
forum: General Help
---

### Post by doundounba on 2007-03-05
Hi all,

I am currently a grad student, in the middle of writing my thesis.  As such, I am almost constantly downloading and printing reprints of scholarly articles from such places as [JSTOR]("http://www.jstor.org/"), in PDF format.  I've been doing this for years, and had never had a problem until my last few downloads.

The last few files I've downloaded don't print properly.  The pages seem just fine when displayed on the screen, but when I print, for *some* of the pages, only the top left quarter of the page comes out.  I've tried two different machines (mine and my SO's), with two different printers (a Lexmark laser and an HP color printer), with exactly the same results.  Both machines are running up to date Kubuntu Edgy installations, and I tried printing both from KPDF and kghostview.  Nothing works.

Anyone ever see anything like this?

If anyone wants to help, I'd really appreciate it.  I could send any printing experts in the audience a 600k, 5 page PDF file that exhibits the problem.  Send me a private message if you'd be willing to try...

TIA!

---

### Post by anaconda on 2007-03-05
Have you tried printing with "Adobe Reader" I have noticed that it is one of the best programs for printing in ubuntu..  with it you can zoom, in/out, print 4 pages to 1 etc.. lots of options..

EDIT: just remembered that i HAVE had similar experiences when trying to print doublesided and 2 pages to 1 page with some HP printer..  Found only 2 solutions to that problem.. using different printer or printing 1 page per page..

---

### Post by doundounba on 2007-03-05
Ah yes, Adobe Reader, that would make sense, wouldn't it... When in doubt, go to the guys who invented the bloody format! :)

I've just done a single file so far, but indeed, Adobe Reader (7.0.9) seems to be able to print my documents just fine.  At least it's free as in beer, even though it's not free as in freedom...  Guess FOSS stills has a little ground to cover here.

Thanks for the quick reply! :cool:

EDIT: A word of warning...  If you print in reverse order using Adobe Reader, and then try to print from the same document in *non* reversed order, it will not work (or at least, it doesn't work for me).  Unselecting the reverse checkbox is ineffective and pages still come out in reverse order.  You can get around this by quitting and re-opening your document in Adobe Reader. Makes manual duplex printing a bit more complicated, but hey, at least it prints the whole page, all the time.

---

### Post by tom17 on 2007-07-09
How are you guys printing from Adobe Reader? I have it installed through crossover office and all I get is a bunch of raw postscript text and not the actual document in question.

I'm getting a bit 'pull my hair out' here with printing in Feisty in general. Maybe I am just too used to the windows ways of things. In windows, I would always be able to go into the 'print...' dialog of any application and choose draft, normal, b&w etc, but I am not finding the same flexibility and consistency in apps on the linux desktop. As a result, I have had to configure the same printer multiple times with different default quality settings. The thing is these default settings tend to be ignored half the time.

Additionally, when I do get linux to print in 'draft' mode, it is still really slow, like a millimetre at a time rather than whizzing the page through like XP does. (HP Deskjet 5440).

I have actually resorted to running XP in VMWare just so that my wife and I can view and print PDF files correctly - this is extreme overkill but I have found no easier alternative.

Are there any native apps that do a decent job of supporting PDF files?

Thanks,

Frustrated Tom...

edit: OK, as usual, I post a rant on a forum *before* looking one more time for info on what i'm trying to do. I just found Adobe reader in the repository. I Uninstalled my crossover office version and installed the repo version and I can now print from Adobe without using a VM :) *sigh*

Now to try and find a full version that works.. anyone?

---

### Post by Manolicious on 2007-10-10
I don't know if my problem is similar.  I just installed ubuntu 7.0# and it seems to print pdf files just fine, however on one particular pdf file that was made with MS word, it can print out the highlightable text and equations, but for those equations that are not highlightable it just prints out black squares.  Do I just need adobe reader?

---

### Post by PC_load_letter on 2008-04-08
> **anaconda said:**
> Have you tried printing with "Adobe Reader" I have noticed that it is one of the best programs for printing in ubuntu..  with it you can zoom, in/out, print 4 pages to 1 etc.. lots of options..

EDIT: just remembered that i HAVE had similar experiences when trying to print doublesided and 2 pages to 1 page with some HP printer..  Found only 2 solutions to that problem.. using different printer or printing 1 page per page..

I just experienced a very similar behaviour in Adobe Reader (with Feisty AMD64) and a Samsung ML1740 laser printer. 

First, I printed a range of pages (not the whole document), chose odd pages, and checked the reverse order box. Everything went fine. But....when trying to do the same for the even pages within the same range, I found the Reverse order check mark is still in place, proceeding this way, I got the pages printed but the order was **NOT** reversed. 
Tried one more time, only to realize that you need to uncheck/check the Reverse order box **twice** :roll: in order for it to work, or as previously suggested, close & reopen Adobe reader.

---

