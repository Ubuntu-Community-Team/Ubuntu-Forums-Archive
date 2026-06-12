---
title: "Curious problem with Epson wp-4015 printer"
date: 2015-02-22
forum: General Help
---

### Post by grey1beard on 2015-02-22
I'm in the process of rescuing an Epson wp 4015, by way of curing clogged nozzles.
My laptop running 12.04 successfully installed it in my 32 bit system, and it dutifully printed a test page.
When I came to print my head purging files, just strips of colour, created in Inkscape, I ran into problems. While it refused to print from inkscape, from Image viewer, or Gimp, it prints perfectly.
I assume that both the latter convert the image to a raster file before sending it to the printer, whereas Inkscape tries to send it as a vector file, which isn't acceptable to the printer.
Is this the case, or a reasonable approximation ?
I'd be grateful for more understanding and a cure.

Thanks,
John

---

### Post by pdc on 2015-02-24
I wonder which driver you are using: Epson [http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=19445&DSCCHK=f19be7033a2aa451249ee62d3c088d4cb5985f47](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=19445&DSCCHK=f19be7033a2aa451249ee62d3c088d4cb5985f47) provide the epson-inkjet-printer-201113w_1.0.2-1lsb3.2_i386.deb or epson-inkjet-printer-201113w_1.0.2-1lsb3.2_amd64.deb

---

### Post by grey1beard on 2015-02-24
I'm fairly certain I woudn't have used the second one, which I assume by its name is for a 64 bit chip.
But as a matter of increasing my knowledge - how do I find out which driver is installed ?

Thanks
John

EDIT yes, I can confirm that I installed the *epson-inkjet-printer-201113w_1.0.2-1lsb3.2_i386.deb* driver

---

