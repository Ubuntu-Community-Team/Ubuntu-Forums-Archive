---
title: "Suddenly, print failure! OOo, PDF and evince"
date: 2008-01-24
forum: General Help
---

### Post by Steelangel on 2008-01-24
I'm utterly stumped at this problem. In short, my printer will not actually print PDF files that have been created from OpenOffice. 

My System: 
xubuntu 7.04
P3 550 MHz
384 MB RAM

openoffice.org 2.2.0-1ubuntu5
evince 0.5.2 using poppler 0.5.4
---

I have a few documents in OpenOffice's .odt format that I would like to convert to PDF and print from my printer (HP LaserJet 3390), 

Using the 'export as PDF' option in OOo, I can create a PDF that is readable by evince without difficulty. 

However, when I print the file from evince, the printer blinks three times then stops completely, as if the document was completed printing. The printer makes no sound. The job appears on the CUPS job list as 'in process' or 'completed' but there was no actual printer output. 

I have tried 
```
lpr -P printer filename.pdf 
```
to no avail. I get the same routine: Blink, stop. However, if I use the lpr command, there are notices in the error log that look like this: 
```
[Job 169] pdftops-options: -cfg /etc/cups/pdftops.conf
```
These error messages do not appear when printing from evince. 

Other PDF files that I have (not made from OpenOffice) print from evince. Test pages seem to print fine from CUPS.

Evince seems to give me a string of error messages to the terminal when I try to print from it. This happens regardless of whether the file actually prints or not. 
```
Model not found, discarding config

(evince:6498): GnomePrint-WARNING **: Could not create filter from description 'GnomePrintFilterSelect': filter 'GnomePrintFilterSelect' is unknown

(evince:6498): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(evince:6498): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(evince:6498): GnomePrint-WARNING **: Could not create filter from description 'GnomePrintFilterClip [ GnomePrintFilterMultipage ]': filter 'GnomePrintFilterClip' is unknown

(evince:6498): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(evince:6498): libgnomeprintui-CRITICAL **: gnome_print_layout_selector_load_filter: assertion `GNOME_IS_PRINT_FILTER (f)' failed

(evince:6498): GLib-GObject-CRITICAL **: g_object_set: assertion `G_IS_OBJECT (object)' failed

(evince:6498): GLib-GObject-CRITICAL **: g_object_set: assertion `G_IS_OBJECT (object)' failed

(evince:6498): GLib-GObject-CRITICAL **: g_object_set: assertion `G_IS_OBJECT (object)' failed

(evince:6498): GLib-GObject-CRITICAL **: g_object_set: assertion `G_IS_OBJECT (object)' failed

(evince:6498): GLib-GObject-CRITICAL **: g_object_set: assertion `G_IS_OBJECT (object)' failed

(evince:6498): GnomePrint-CRITICAL **: gnome_print_filter_reset: assertion `GNOME_IS_PRINT_FILTER (f)' failed

(evince:6498): GnomePrint-CRITICAL **: gnome_print_filter_flush: assertion `GNOME_IS_PRINT_FILTER (f)' failed

(evince:6498): GLib-GObject-CRITICAL **: g_object_set: assertion `G_IS_OBJECT (object)' failed

(evince:6498): GLib-GObject-CRITICAL **: g_object_set: assertion `G_IS_OBJECT (object)' failed

(evince:6498): GLib-GObject-CRITICAL **: g_object_set: assertion `G_IS_OBJECT (object)' failed

(evince:6498): GLib-GObject-CRITICAL **: g_object_set: assertion `G_IS_OBJECT (object)' failed

(evince:6498): GLib-GObject-CRITICAL **: g_object_set: assertion `G_IS_OBJECT (object)' failed

(evince:6498): GLib-GObject-CRITICAL **: g_object_set: assertion `G_IS_OBJECT (object)' failed

(evince:6498): GnomePrint-CRITICAL **: gnome_print_filter_reset: assertion `GNOME_IS_PRINT_FILTER (f)' failed

(evince:6498): GnomePrint-CRITICAL **: gnome_print_filter_flush: assertion `GNOME_IS_PRINT_FILTER (f)' failed

** (evince:6498): WARNING **: could not set the value of Settings.Document.Filter, node not found
```

OOo will print the .odt files perfectly fine without resorting to PDFs - so I suspect that there is some sort of incompatibility between how OOo creates a PDF file and the pdftops conversion that goes on between the computer and the printer. I wonder if the default export options for OOo are the suspect.

Is there a solution to this? Most of the related posts discuss the complete inability to print PDFs from evince. I can print them, but the ones created by OOo do not print.

---

### Post by mssever on 2008-01-24
Just a stab in the dark: Can acroread print the files?

---

### Post by Steelangel on 2008-01-27
I don't have acroread installed - but I can certainly check this when I get back to the office on Monday.

---

### Post by Steelangel on 2008-01-28
Update: 

Acroread does print the PDF files made by OOo, I think the problem is therefore in evince; what the issue actually is, however, I really do not know.

---

### Post by stchman on 2008-01-28
Yes, I found that Evince is not very good PDF software when it comes to printing.  I installed Acrobat reader and it works WAY better especially in printing.

Here is how to install Adobe Acrobat in Ubuntu 7.04 and later.

[http://www.stchman.com/install_adobe.html](http://www.stchman.com/install_adobe.html)

Also make sure that the paper size is set properly using the CUPS web based manager.

---

### Post by mssever on 2008-01-28
> **Steelangel said:**
> Update: 

Acroread does print the PDF files made by OOo, I think the problem is therefore in evince; what the issue actually is, however, I really do not know.

Maybe those files are somewhat invalid, or maybe there's a bug in evince. If they're not sensitive, it might be helpful to file a bug report and attach those files.

---

