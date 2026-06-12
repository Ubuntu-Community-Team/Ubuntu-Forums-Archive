---
title: "PDFlib for PHP"
date: 2005-08-15
forum: General Help
---

### Post by orpobanana on 2005-08-15
Hi,

I've installed Apache2, PHP and MySQL from ubuntu packets. I found gd-library, but I can't find/install pdflib? Is this available as ubuntu packet or can it be installed from somewhere else.

Thanks

---

### Post by PeP on 2005-08-15
did you enable extra repositories? it 's in universe.

check this : [http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

---

### Post by orpobanana on 2005-08-16
Yes I have extra repositories enabled.

There is only libpdf api for perl. I installed it and restarted apache2 but it didn't apply it to php configuration. mysql and gd were in packet as php modules, but libphp is not. Where could I get it.

---

### Post by MAsKrA on 2006-08-17
Good Ol' bump for I am having the same problem. 

I have installed:

```

sudo apt-get install libpdflib804-2
sudo apt-get install libpdfkit0
sudo apt-get install php-fpdf

```

but my phpinfo(); page does not have any reference to PDF.

Any help is apreciated....

---

### Post by gmarton on 2006-10-23
I was looking for an answer on this as well and here is what I ended up doing:

Download PDFlib and unzip it (I know 7 is out but I have things working in 6 so the link is for v6, but you can do 7 if you are starting something new):
> wget [http://www.pdflib.com/fileadmin/pdflib/products/pdflib/download/603/PDFlib-6.0.3p1-Linux.tar.gz](http://www.pdflib.com/fileadmin/pdflib/products/pdflib/download/603/PDFlib-6.0.3p1-Linux.tar.gz)
tar -zxvf PDFlib-6.0.3p1-Linux.tar.gz -C /tmp

Then install it with pecl:
> pecl install pdflib
if command not found then install pecl with > sudo apt-get install pecl 
When prompted enter the path to 
> /tmp/PDFlib-6.0.3p1-Linux/bind/c

After this enable pdf.so in your php.ini file (pecl already copied it to appropriate location if install was successful

add this in php.ini
> extension=pdf.so

I use php4 so mine was at '/etc/php4/apache2/php.ini'

then restert apache2

> /etc/init.d/apache2 force-reload

You should now see pdf info on your phpinfo()

You will get a big pdflib across the screen w/o a licanse but good for developing. 

Normally it would work if you compiled pdflib-Lite but that wont give you PDI which opens up existing PDFs and you can change them.

---

### Post by lenny8088 on 2007-06-29
Thank you! That worked perfectly and was exactly what I was looking for. 


-A

---

### Post by stashj on 2007-09-14
Afternoon!

Thanks for the howto on this. When I try it my pecl install finishes with the following error;

> checking for PDF_open_pdi in -lpdf... no
configure: error:
PDFlib extension requires at least pdflib 4.0.x.
See config.log for more information.

My googling has produced no leads and I'm now quite stuck. Can anyone help?

I've downloaded exactly the package above and am using php 5.1.2.

Thanks,

Stash

---

### Post by gmarton on 2007-09-14
Hi, were you prompted to enter the path to pdflib c library?

---

### Post by stashj on 2007-09-17
Yes, and I entered it just as above which is where I'd extracted it to.

---

