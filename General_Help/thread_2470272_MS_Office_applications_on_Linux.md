---
title: "MS Office applications on Linux"
date: 2021-12-23
forum: General Help
---

### Post by sara-meyer3 on 2021-12-23
Hi all, 

Due to my lack of computer literacy, I have been mainly using windows PCs for the past years. 
I am now planning to set up a Linux notebook as a backup system. I would need this Linux notebook mainly for document management. 

The main programs I am using on my windows PC are

- word
- access 
- excel 

This means, my Linux notebook would need to provide these functionalities too. 

I am particularly doubtful whether I could find a solution for the access databases on Linux without being an expert with databases

Thanks in advance for your ideas.

Sara

---

### Post by fyfe54 on 2021-12-23
LibreOffcie will do what you need. 
[https://www.libreoffice.org](https://www.libreoffice.org)

---

### Post by grahammechanical on 2021-12-23
What are the file formats of those Microsoft applications? Can Libreoffice read and save in those formats?

[https://wiki.documentfoundation.org/Faq/General/012](https://wiki.documentfoundation.org/Faq/General/012)

Libreoffice is installed by default in Ubuntu. But it is without a database application. That has to be install separately from the Ubuntu Software. It is the application that installs and removes applications for us. The Libreoffice database application is called Base. 

[https://ask.libreoffice.org/t/can-i-open-a-ms-access-file-in-libreoffice/18538](https://ask.libreoffice.org/t/can-i-open-a-ms-access-file-in-libreoffice/18538)

[https://www.libreoffice.org/discover/base/](https://www.libreoffice.org/discover/base/)

Regards

---

### Post by QIII on 2021-12-23
Base does not have the same idea of modules and macros as Access.  Most programming is done separately from the database file and it definitely does not use VBA as its programming language.

The bottom line is that applications cannot be designed in the same manner and the files are NOT compatible with .accdb files.

---

### Post by HermanAB on 2021-12-24
MS Word documents tend to look slightly different on Linux, mainly because of font differences.  If you don't use many weird fonts, then Libre Office will be OK.

Cross Over Office is another solution: [https://www.codeweavers.com/](https://www.codeweavers.com/)

---

### Post by ActionParsnip on 2021-12-24
You can use O365 in the web browser too. No problem

---

### Post by SeijiSensei on 2021-12-24
I keep a VirtualBox virtual machine with Windows 10 on it to use Access (and a few other things).  There is no good alternative to Access in Linux.  I use LibreOffice Writer and Calc for everything.  They read and write to MS formats just fine, though I guess there can be layout or formatting issues in complex documents.  Calc is pretty much a drop-in replacement for Excel except for VBA.

(I use Postgresql on Linux as my DBMS and connect to the databases from Access using the ODBC driver available from postgresql.org.)

---

### Post by dragonfly41 on 2021-12-24
> Calc is pretty much a drop-in replacement for Excel *except for VBA*.

Some discussion threads below .. and you might try googlesheets as an intermediary to convert VBA.

[https://www.linux.org/threads/how-to-convert-a-ms-access-application.31824/](https://www.linux.org/threads/how-to-convert-a-ms-access-application.31824/)

[https://help.libreoffice.org/6.2/en-US/text/sbasic/shared/vbasupport.html](https://help.libreoffice.org/6.2/en-US/text/sbasic/shared/vbasupport.html)

[https://developers.google.com/apps-script/guides/macro-converter/convert-files](https://developers.google.com/apps-script/guides/macro-converter/convert-files)

[https://developers.google.com/apps-script/guides/macro-converter/tutorials](https://developers.google.com/apps-script/guides/macro-converter/tutorials)

---

### Post by grahammechanical on 2021-12-24
Some years ago Microsoft allowed a set of True Type fonts to be come public domain. Those fonts are still available can can be installed in Linux/Ubuntu. We need to accept the Microsoft End User License Agreement. These fonts might improve the font compatibility issue. They will be available in Libreoffice just like any other font.

[https://linuxconfig.org/install-microsoft-fonts-on-ubuntu-20-04-focal-fossa-desktop](https://linuxconfig.org/install-microsoft-fonts-on-ubuntu-20-04-focal-fossa-desktop)

Regards

---

### Post by QIII on 2021-12-24
I own a software development company.  I can say from experience that most of the "easy conversion" methods described for Access to LibreOffice aren't -- and their efficacy drops sharply with the complexity of the VBA code.  Those articles are all well and good -- for the simplest of applications. 

Even within the Windows environment, my colleagues and I eschew Access in favor of applications (some with Windows GUIs, some that support web applications) written in modern languages that access a more capable and powerful RDBMS.  Access is, by definition, and RDBMS, but it is not a robust one and not scalable beyond 2GB without breaking it up into separate databases.  VBA is not particularly powerful, either.

Base and Access are simply different animals despite whatever "easy" conversion tool one might find.

If you want a personal-level database system (it sounds like yours will be -- it's not an enterprise-level application)  I would go with the easiest and cheapest route:  A Windows virtual machine and whatever Access database you already have.  If you don't want to do that and you don't think you can do the work yourself, be prepared to lay down some cash for people who can do it right.

---

### Post by HermanAB on 2021-12-24
Redhat made a set of fonts that are indistinguishable from the MS fonts - so there is no need to install the MS fonts. The liberation fonts are part of every Linux distro: https://github.com/liberationfonts

---

### Post by sara-meyer3 on 2021-12-25
> **QIII said:**
> ....  If you don't want to do that and you don't think you can do the work yourself, be prepared to lay down some cash for people who can do it right.


Thanks for all your answers :-)

I actually was planning not to go online anymore after having set up the system. I guess this idea would not work with the virtual machine solution. right?

---

### Post by QIII on 2021-12-25
Most of the other Office productivity apps have workable LibreOffice analogs, so long as you are careful.  Access is the cheese that stands alone.

But if you really, really need to have perfect interoperability, a VM might be the easiest choice.  Just bear in mind that this is coming from someone who is NOT a Linux evangelist, but a technology pragmatist.

---

### Post by Irihapeti on 2021-12-25
I don't use Access, but up until a couple of years ago, I was doing proofreading of Masters and Ph.D. theses for (mainly) international students. All of these were in Word.

I discovered that I couldn't rely 100% on Libreoffice writer docs transferring correctly to Microsoft Office on a Windows system and displaying correctly. Sometimes, it wouldn't display text that was actually in the document. Sometimes, the formatting was just "off" with tables and other fancy layouts. To me, that was a deal-breaker, especially as I was being paid for the work. Plus, when people submit work at the last minute (as most of them do!), there isn't time to figure out workarounds. I did try Office 365 online, and found it 1) too slow and 2) fine for the basics but not able to deal with advanced formatting.

I set up a Windows 10 VM with Microsoft Office and I've found that entirely satisfactory. Yes, it cost me some money, but as I could write it off against tax, I was happy with that.

Like QIII, I'm not a Linux evangelist but prefer to use what works.

---

### Post by Quarkrad on 2021-12-26
#12  This virtual machine is not 'a machine in the cloud' as such.  It is a machine that sits within your own pc/ubuntu environment.  You can install an environment on your ubuntu system (examples are Virtualbox, qemu/kvm) that allows you to install other operating systems.  Many people have these installed for things like testing, or having something like win 10  to use itunes.  So .... you could install qemu/kvm on your ubuntu box and install windows 10 in it.  You can run windows 10 full screen, and it is possible for it to runs as fast as a stand alone windows 10 pc, so for all intents and purposes it feels like you are working on a win10 machine, not a ubuntu one.   Hence the term virtual, it feels like you are using a win10 machine but in reality you are using a win10 machine within a ubuntu machine.  Personally I have a windows 10 and two other ubuntu systems within my main ubuntu install but many people have many of these virtual machines installed.  So you can have a windows 10 machine with ms office installed without having to go 'on-line'.

---

### Post by schragge on 2021-12-26
> **QIII said:**
> Most of the other Office productivity apps have workable LibreOffice analogs, so long as you are careful.  Access is the cheese that stands alone.
Another day I saw a post suggesting conversion from MS Access to [KEXI]("http://www.kexi-project.org") rather than to LibreOffice Base.

And on the command line there's also [the mdbtools set]("https://github.com/mdbtools/mdbtools"). A word of caution though. Ubuntu 20.04 LTS ships with mdbtools 0.7.1 which was released in October 2013. The current version is 1.0.0—it's already in Debian unstable, so definitely is going to be included in the next Ubuntu release which also happens to be an [LTS]("https://ubuntu.com/blog/what-is-an-ubuntu-lts-release").

Not saying any of them does better job importing MS Access data than LibreOffice does as I never tried. Just to mention other available options.

---

