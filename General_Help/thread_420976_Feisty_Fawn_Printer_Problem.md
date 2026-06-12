---
title: "Feisty Fawn Printer Problem"
date: 2007-04-24
forum: General Help
---

### Post by Lokithor on 2007-04-24
I was really surprised that Feisty Fawn saw my network printer (Brother MFC-420CN).

However, I have a problem.  The Printing category shows the printer as "ready", but when I try to print a test page or a document from Open Office, it doesn't print.

I am very new to Ubuntu (and LInux) and may not have installed the printer correctly.

When it saw my printer it highlighted a printer driver and I could choose Install Driver or Next.
When I pressed the Install Driver button, i just got a screen showing  directories.  So I just pressed the Next button.

Also, when it showed my printer at the end of the three-step installation process, there were two boxes:  Description and Location.  I left them blank and Pressed the Finish button.

Can anyone help?

TIA  :(

---

### Post by dcstar on 2007-04-24
> **Lokithor said:**
> I was really surprised that Feisty Fawn saw my network printer (Brother MFC-420CN).

However, I have a problem.  The Printing category shows the printer as "ready", but when I try to print a test page or a document from Open Office, it doesn't print.

I am very new to Ubuntu (and LInux) and may not have installed the printer correctly.

When it saw my printer it highlighted a printer driver and I could choose Install Driver or Next.
When I pressed the Install Driver button, i just got a screen showing  directories.  So I just pressed the Next button.

Also, when it showed my printer at the end of the three-step installation process, there were two boxes:  Description and Location.  I left them blank and Pressed the Finish button.

Can anyone help?

TIA  :(

Does the Test Page print?

---

### Post by Lokithor on 2007-04-24
As I said in my original post, I cannot print a Test Page or document from Open Office.

Any help would be greatly appreciated.

---

### Post by ubu-for on 2007-05-01
Same here with my HP Laserjet 3150 via USB.

---

### Post by mgmiller on 2007-05-04
When installing a printer, if it highlights a driver that looks like yours, do not press the install driver button.  That is only for installing a driver other than the one that is highlighted.  Try deleting your printer and running the install printer wizard again.  This time when it suggests your printer, just hit next and continue to the end.  Also, sometimes Open Office will not see the paper selections you have as the default for your printer.  I believe it defaults to A4 both in the system>administration>printing and also in the printer setup area in open office (file>printer settings>properties)  You need to change it in both spots if you need US paper sizes.

---

### Post by ubu-for on 2007-05-30
> **mgmiller said:**
> When installing a printer, if it highlights a driver that looks like yours, do not press the install driver button.  That is only for installing a driver other than the one that is highlighted.  Try deleting your printer and running the install printer wizard again.  This time when it suggests your printer, just hit next and continue to the end.

CUPS suggests the ljet3 driver but the printer still does not work.

---

