---
title: "Address Book Inport"
date: 2008-04-10
forum: General Help
---

### Post by Ellaine on 2008-04-10
I have my Windows Address Book.wab on a floppy. Is there any way to open Evolution and import the entire address book? 
PS: I boot each system (Windows/Ubuntu 7.10) on seperate hard drives, and never have both in the box at the same time.

---

### Post by ryanhaigh on 2008-04-10
Not really sure if this will help but maybe consider using thunderbird to import your wab contacts and then import the thunderbird format into evolution? I've heard this mentioned when using outlook previously.

---

### Post by scramasax on 2008-04-10
> **Ellaine said:**
> I have my Windows Address Book.wab on a floppy. Is there any way to open Evolution and import the entire address book? 
PS: I boot each system (Windows/Ubuntu 7.10) on seperate hard drives, and never have both in the box at the same time.

The WAB format is not the best place to start from.

Have a look at the importer in Evolution.  It specifically mentions being able to import a CSV (comma separated values) Outlook-format address book.  I presume Outlook and OE produce similar CSV files.

See this article:

[http://support.microsoft.com/kb/175017](http://support.microsoft.com/kb/175017)

Otherwise, I'd suggest using vCards.  Evolution will actually import a multiple vCard, although I can't recall if the Windows Address Book can make one.  Obviously, it can be a pain importing a large number of vCards one at a time.

But those look like your two choices -- CSV file or vCard.

---

### Post by Ellaine on 2008-04-10
Tried Thunderbird but it won't import a .wab file either. Just like Evolution it needs a CSV file to import. Outlook Express will only make a .wab file. I could switch to Outlook in windows and create a file that evolution will accept, but it's not worth the trouble. 

Thanks for the help.

---

### Post by Ellaine on 2008-04-10
Dummy here just found out that Outlook Express WILL export to a .csv file. Once this is done I don't need Microsoft anymore.

Thanks again.:)

---

### Post by Yeti can't ski on 2008-04-24
Ellaine, 

I also tried exporting contacts on ".CSV" from Outlook to Evolution. The information was there, but Evolution wouldn't improperly. For istance, the name of a contact would be inserted as an e-mail and vice versa. 

Some guys suggested installing Thunderbird, but that seemed too troublesome. My advice is to use G-mail (you can open an account for that) to do the trick. 

- Export your contacts from Outlook to as a regular ".CSV" file;
- Import that contacts' file into Gmail (in webmail mode);
- Export from Gmail to a ".VCF" consolidated file (it will be a single file); and finally
- Import the resulting ".VCF" file to Evolution. 

The "bonus" is that Gmail will automatically cancel doubled/repeated entries. Really great. I hope someday Evolution will do all that by itself.

Good luck.

---

### Post by JanLN on 2008-05-12
I have made it this way. In windows open Thunderbird Functions/Import/adressbooks from Outlook Express and then export to a ldif-file which can be imported to Evolution.

---

