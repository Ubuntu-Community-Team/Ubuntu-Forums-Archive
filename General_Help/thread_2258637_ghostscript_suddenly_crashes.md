---
title: "ghostscript suddenly crashes"
date: 2014-12-29
forum: General Help
---

### Post by l4m3 on 2014-12-29
Hello dear community,

as the title says my /usr/bin/gs crashes with the message: gs crashed with SIGSEGV in i_free_object().
This happens, when I'm trying to print from an java application.
I can print from AbiWord and LibreOffice just fine.

The ghostscipt package is ghostscript 9.10~dfsg-0ubuntu10.02.
My distribution is Xubuntu 14.04.1.
My architecture is AMD64.
The Printer is an HP LaserJet 1200.
This also happens with cups-pdf.
lsusb says that the printer is recocgnized: Bus 001 Device 009: ID 03f0:0317 Hewlett-Packard LaserJet 1200

The printjob stops saying that the file is not a pdf file.

Can anyone of you give me a hit how to solve the problem?
Any help is highly appreciated.

Best regards,

Max.
[ATTACH=CONFIG]258860[/ATTACH]

Edit: changed applet to application

---

### Post by Holger_Gehrke on 2014-12-29
> **l4m3 said:**
> Hello dear community,
This happens, when I'm trying to print from an java applet.


A Java application or an applet ? An Applet runs heavily sandboxed in a web browser and should not have the kind of access to the system necessary for printing. It renders itself into something like an image. Printing would be done by the Browser.

---

### Post by l4m3 on 2014-12-29
Sorry.
It is an application of it's own.

Thanks for your reply!

Max

---

### Post by l4m3 on 2015-01-02
Hello again.

My problem unfortunately is still unsolved.
Maybe I should add, that I was able tp print from the applicaton in the past.

Any help is highly appreciated.

Best regards,

Max.

---

### Post by l4m3 on 2015-01-04
I have solved the problem by installing gs 9.15

Thanks

---

