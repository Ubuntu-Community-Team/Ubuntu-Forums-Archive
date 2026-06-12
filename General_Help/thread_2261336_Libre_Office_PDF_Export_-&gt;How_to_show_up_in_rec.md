---
title: "Libre Office PDF Export -&gt;How to show up in recent files?"
date: 2015-01-18
forum: General Help
---

### Post by klemens_u on 2015-01-18
Hi,

Typical workflow:

- Edit Libreoffice document, save it and export as pdf
- Now in another app (e.g. Thunderbird) I want to attach the pdf. 
- Problem: only the libreoffice file, but not the pdf show up in the file dialogue's "recent files" list

Any suggestion on how to fix this problem?

Thanks a lot!
Klemens

---

### Post by SeijiSensei on 2015-01-18
If you know where the file was stored, just navigate to that directory in the file browser that pops up when you choose Attach.  Usually LibreOffice writes PDF versions into the same directory as the original ODF file.

---

### Post by klemens_u on 2015-01-18
Hi SeijiSensei,

thanks for your time, but my problem is not locating the pdf file in the filesystem ;-)
The recent files feature is very handy, so it's annoying that recently exported Libre Office pdf files don't show up there.
That's what I'm searching for.

---

### Post by bapoumba on 2015-01-18
I can confirm the behavior (not that I had ever noticed..). Created a test file with LO Writer > saved it as .odt > exported as pdf. Trying to attach a file to a new mail (Sylpheed here) shows the .odt and not the .pdf in recent files.
A little looking around shows that the recent files are indexed here : /home/bapoumba/.local/share/recently-used.xbel where the .odt is but not the .pdf.

That is all I got for now, trying to understand how the recently-used file is set up :)

Edit : [https://www.libreoffice.org/bugzilla/show_bug.cgi?id=66412](https://www.libreoffice.org/bugzilla/show_bug.cgi?id=66412)

---

### Post by klemens_u on 2015-01-18
Ok, Bapoumba - thanks a lot, now we know at least that it is a problem of LibreOffice. I confirmed the ticket in their bugzilla.

---

### Post by Holger_Gehrke on 2015-01-18
> **bapoumba said:**
> 
A little looking around shows that the recent files are indexed here : /home/bapoumba/.local/share/recently-used.xbel where the .odt is but not the .pdf.

That is all I got for now, trying to understand how the recently-used file is set up :)


Don't bother unless you really want to, there's something newer already out since at least 12.04 ...
zeitgeist is the new generation of history-management. It stores history in a sqlite database located at '~/.local/share/zeitgeist' and communicates with programs through dbus, both when they make a history entry and when they request a list of recently used files, urls or whatever else can go into a history; it's supposedly is more flexible and quicker. The one problem I have with it is privacy related: tools for working with the history database are still somewhat rare, especially if you want to clean up ;-) 
Not everyone likes starting the sqlite client and issuing SQL 'delete' queries ...

---

### Post by klemens_u on 2015-01-18
> **Holger_Gehrke said:**
> Don't bother unless you really want to, there's something newer already out since at least 12.04 ...
zeitgeist is the new generation of history-management. It stores history in a sqlite database located at '~/.local/share/zeitgeist' and communicates with programs through dbus, both when they make a history entry and when they request a list of recently used files, urls or whatever else can go into a history; it's supposedly is more flexible and quicker. The one problem I have with it is privacy related: tools for working with the history database are still somewhat rare, especially if you want to clean up ;-) 
Not everyone likes starting the sqlite client and issuing SQL 'delete' queries ...

Sorry, but I don't quite get you. How is this connected to the recent files list in Nautilus/File open dialogue?

---

### Post by bapoumba on 2015-01-18
> **Holger_Gehrke said:**
> Don't bother unless you really want to, there's something newer already out since at least 12.04 ...
zeitgeist is the new generation of history-management. It stores history in a sqlite database located at '~/.local/share/zeitgeist' and communicates with programs through dbus, both when they make a history entry and when they request a list of recently used files, urls or whatever else can go into a history; it's supposedly is more flexible and quicker. The one problem I have with it is privacy related: tools for working with the history database are still somewhat rare, especially if you want to clean up ;-) 
Not everyone likes starting the sqlite client and issuing SQL 'delete' queries ...

OK thanks, I had found about zeitgeist but I do not have it on my lubuntu install, so I looked elsewhere.

@klemens_u : looking further around got me to think about one thing. Recently *used* is different from recently *created*.
Please try this. Create a new .pdf from LO, then open it. Doing this allowed me to see it in the mail attachment list. So I guess things work as they are supposed to work. Recently *used* is, well, recently *used* files :)

---

### Post by mc4man on 2015-01-18
The sole determining factor here (ubuntu 14.04) is whether when exporting a pdf in LO I explicitly add a .pdf extension or not
When adding .pdf to the file name it's immediately shown in 'Recent'. If I don't, just use a filename, then it's not. (LO adds the ext but that doesn't matter in this regard

---

### Post by vasa1 on 2015-01-18
> **mc4man said:**
> The sole determining factor here (ubuntu 14.04) is whether when exporting a pdf in LO I explicitly add a .pdf extension or not
When adding .pdf to the file name it's immediately shown in 'Recent'. If I don't, just use a filename, then it's not. (LO adds the ext but that doesn't matter in this regard
Your solution works for me --- Lubuntu 14.04 (Openbox session, no DE, LibreOffice 4.3.4.1).

---

### Post by bapoumba on 2015-01-19
wfm, plain lubuntu 14.10, LO 4.3.3.2, thanks mc4man :)

---

### Post by klemens_u on 2015-01-20
> **bapoumba said:**
> 
@klemens_u : looking further around got me to think about one thing. Recently *used* is different from recently *created*.
Please try this. Create a new .pdf from LO, then open it. Doing this allowed me to see it in the mail attachment list. So I guess things work as they are supposed to work. Recently *used* is, well, recently *used* files :)

That makes no sense for me in a practical way. Creating a file is also a kind of "usage".

---

### Post by klemens_u on 2015-01-20
> **mc4man said:**
> The sole determining factor here (ubuntu 14.04) is whether when exporting a pdf in LO I explicitly add a .pdf extension or not
When adding .pdf to the file name it's immediately shown in 'Recent'. If I don't, just use a filename, then it's not. (LO adds the ext but that doesn't matter in this regard

Wow, that's an amazing finding which is a good workaround, thanks!
I'll add this to the LO bug ticket.

---

### Post by klemens_u on 2015-01-20
Please add a comment to the LO-Bugreport and add yourself to the cc list:
[https://www.libreoffice.org/bugzilla/show_bug.cgi?id=66412](https://www.libreoffice.org/bugzilla/show_bug.cgi?id=66412)
In this way we can raise the impact of this request.

If you have problems I'll be glad to help out.

---

