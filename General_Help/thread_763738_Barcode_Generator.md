---
title: "Barcode Generator"
date: 2008-04-23
forum: General Help
---

### Post by seeker1458 on 2008-04-23
Hey guys, Im looking for a free way to generate some bar codes based on customizable criteria. I am trying to get an inventory tracking system together so that the Owner of our company can see what type of computer all of his employee's are using.  I just need something simple that I can create a field for Branch, Brand, Department, S/N or ESC or ST, maybe monitor size and date purchased.  And then take that information and create a barcode.  We already have Intermec hand-helds with built in barcode readers.  So I don't want to have to buy a full Inventory suite when I can use some Avery labels and the equipment we already have.  Any ideas?

---

### Post by ryanhaigh on 2008-04-23
Searching in synaptic package manager (System>Admin>Synaptic) gives these options. Hopefully something will meet your criteria.

alexandria - a GNOME application for managing book collections
barcode - Utility and library for barcode generation
eancheck - Check digit validator for EAN/PLU/UPC barcode numbers
iec16022 - Generates 2d ISO/IEC 16022 barcodes (data matrix/semacode)
kbarcode - barcode and label printing application for KDE
libbarcode-code128-perl - Perl library to generate CODE 128 bar codes
libgd-barcode-perl - Library to create barcode images (GD::Barcode)
libpdf-reuse-barcode-perl - Create barcodes for PDF documents with PDF::Reuse
libpostscriptbarcode - A barcode generator written entirely in PostScript
php-image-barcode - Barcode generation

---

### Post by seeker1458 on 2008-04-23
I've downloaded libbarcode, and in terminal executed :
```
:~$ barcode
```
and got...
```
%!PS-Adobe-2.0
%%Creator: "barcode", libbarcode sample frontend
%%DocumentPaperSizes: letter
%%EndComments
%%EndProlog
```
so then I used synaptic to download libbarcode...
full package name is libbarcode-code128-perl

How do I get the front end to run?

---

### Post by seeker1458 on 2008-04-23
Guess I should have been a little more specific.  Im looking for a simple to use barcode that has a GUI frontend, not a terminal only frontend.

---

### Post by Foster Grant on 2008-04-23
KDE has a graphic barcode generator frontend (Kbarcode) which will run under GNOME.

---

### Post by seeker1458 on 2008-04-23
When I run the Kbarcode Configuration Wizard, I get a "No database drivers found. SQL database support has been disabled. 

What do I need to do from here?

I've tried using synaptic to load the phython Qt SQL drivers, but it still says they arnt found.(I just checked everything that had to do with Qt4 SQL
:edit:
This is the message I get when Kbarcode attempts to connect to the "Kbarcode" data base
> There are no Qt SQL drivers installed. KBarcode needs those drivers to access the different SQL databases. This drivers are part of the Qt Source distribution and should also be part of your distribution. Please install them first.

---

### Post by BCtom on 2008-05-24
Hello, I just installed KBarcode with Hardy 8.04, and I get the same message too, but I unchecked the "use database" option in the upper-right corner of the last window of the set-up wizard. That fixed that problem. I'm trying to get it to work with Open Office?

It works right after that as a great standard bar code generator.

---

### Post by StuartN on 2010-06-03
> **seeker1458 said:**
> Hey guys, Im looking for a free way to generate some bar codes based on customizable criteria.

There is a (possibly several) barcode plugin for OpenOffice [http://extensions.services.openoffice.org/node/1845](http://extensions.services.openoffice.org/node/1845)

---

### Post by fusiwye on 2010-09-06
I suggest you use [**iwinsoft Barcode Generator**]("http://www.iwinsoft.com/barcode-generator/") software

---

### Post by krimzonstarr on 2010-09-06
> **fusiwye said:**
> I suggest you use [**iwinsoft Barcode Generator**]("http://www.iwinsoft.com/barcode-generator/") software

1. Commercial software
2. Windows install files.
3. There are plenty of open source/free software version in the repo's.
4. ???
5. Win

---

