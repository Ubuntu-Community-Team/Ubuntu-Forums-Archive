---
title: "what happened to print to pdf printer option"
date: 2008-01-23
forum: General Help
---

### Post by AgentZ86 on 2008-01-23
Hi all,

I'm curious ? I did a re-install of Gutsy 7.10 and all updates, and noticed that there is not PDF printer function in my printer list anymore.

It use to be there by default ??

Does anyone know how to print to PDF or what happened ?

I see that I can add the CUPS/PDF_file_generator and simply select my printer, that all works good.

However when creating a pdf, by printing to file etc. I cannot edit this PDF with pdfedit I get a =f parse error or something on the screen ??

Any ideas on these 2 topics ???


Please advise

---

### Post by sandr- on 2008-01-23
Here's the steps in adding a pdf printer:
System->Administration->Printing
Click 'New printer'.
Select 'Print into PDF file'. You don't need to change the device-url.
Choose the generic driver. The recommended driver works just fine ( PDF file generator-> Generic pdf file generator ).

You can give your PDF printer a nice name, eg 'Print2PDF'.

Then , from any application, you can print on this printer. PDF files generated automatically go into the PDF directory in your home directory ( ~/PDF ).

I don't know why this printer isn't a default printer, but as you can see you can add one very quick. Good luck !

---

### Post by AgentZ86 on 2008-01-24
> **sandr- said:**
> Here's the steps in adding a pdf printer:
System->Administration->Printing
Click 'New printer'.
Select 'Print into PDF file'. You don't need to change the device-url.
Choose the generic driver. The recommended driver works just fine ( PDF file generator-> Generic pdf file generator ).

You can give your PDF printer a nice name, eg 'Print2PDF'.

Then , from any application, you can print on this printer. PDF files generated automatically go into the PDF directory in your home directory ( ~/PDF ).

I don't know why this printer isn't a default printer, but as you can see you can add one very quick. Good luck !

Yup, thanks

I was able to figure that out, but I was just wondering why it seemed to be different on my re-install as oppose to PDF printer just appearing by default as on my previous installation ?
Strange.

---

