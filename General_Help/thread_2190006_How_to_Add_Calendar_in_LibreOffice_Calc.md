---
title: "How to Add Calendar in LibreOffice Calc?"
date: 2013-11-25
forum: General Help
---

### Post by CybaCowboy on 2013-11-25
I have an .ods (OpenDocument Spreadsheet) spreadsheet that I have created in LibreOffice Calc, and I would like to add a pop-up calendar...

Specifically, I want users to click on a cell in a certain column, have a calendar pop-up automatically and when the user clicks a date/month/year on the calendar, the calendar closes, inserting the applicable date in a suitable format.

How can I achieve this?

---

### Post by vanadium on 2013-11-25
This can be achieved using the macro programming language of Libreoffice.

---

### Post by CybaCowboy on 2013-11-25
> **vanadium said:**
> This can be achieved using the macro programming language of Libreoffice.

I don't want to be a pain, but can anyone please provide a guide or instructions to do this?

If it's any consolation, I intend to make my spreadsheet publicly-available as a template and given the difficulty in accomplishing this task, I am giving serious consideration to creating a YouTube video showing how it is done (I'm a firm believer of sharing knowledge, particularly with regards to uncommon issues like this one)... Once I work it out myself that is.

---

### Post by ccmiller12 on 2013-11-25
I am not any expert in macros, but have you tried searching an extension that would cover your need? Just a suggestion.

---

### Post by CybaCowboy on 2013-11-25
Actually, I never thought of that!

After searching for an extension, I came-up with this:
[http://extensions.libreoffice.org/extension-center/calendar-for-calc](http://extensions.libreoffice.org/extension-center/calendar-for-calc)

It's not exactly what I had in mind... Users still have to enter a keyboard shortcut or select the calendar from the menu, but maybe it's something I can work with.

Obviously I will still have to do a bit of reading regarding macros, but perhaps I can launch the extension with a macro rather than writing a macro to generate the calendar *and* input the date? If possible, I imagine this would be far simpler than writing a macro to do the lot...

---

### Post by Lars Noodén on 2013-11-25
The extension might do enough of what you want that you won't need macros, one can hope.  It seems written in Python.  With LibreOffice, you can write your macros in Python or Javascript.  I think Java might be an option, too.  This capability is underpublicized.

---

### Post by vanadium on 2013-11-26
I am not sure if it is possible to trigger a macro just by clicking on the very cell where you want to enter the data. It is possible, though, to create a button to run a macro. Thus, you could create a button next to the cell that the user may click to enter the date. Not ideal, but close.

---

