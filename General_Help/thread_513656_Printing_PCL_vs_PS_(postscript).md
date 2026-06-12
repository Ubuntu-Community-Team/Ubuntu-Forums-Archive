---
title: "Printing: PCL vs PS (postscript)"
date: 2007-07-30
forum: General Help
---

### Post by bill-linux on 2007-07-30
At my office we have a Panasonic DP-C322 photocopier/printer. I'm using CUPS to print to this via a network. Here's the problem: The PPD for this printer is for Adobe-Postcript 3.0, but our particular model doesn't have this "module" - it costs some $3000! - instead it is PCL 6. So, when I send ps file generated from this PPD to the photocopier/printer it prints the first line then 100 or so blank sheets. If instead I generate a "ps" file in windows and then send it via linux (lpr -Ppanasonic test.ps, for example) it prints just fine. The difference between the linux "ps" file and the windows generated file is capture completely in the headers, which I've enclosed below.

It appears to me that Windows is generated a PCL file, while the linux ppd is generate a true postscript file. Fine, I loaded a generic PCL6 ppd from linuxprinting.org and it still generated a ps file nearly identical the one listed below. Should this not make a PCL file? Is there something big that I'm missing here?

Linux "ps" file header (this doesn't print well):

%!PS-Adobe-3.0
%%BoundingBox: (atend)
%%Creator: OpenOffice.org 2.0
%%For: bill
%%CreationDate: Mon Jul 30 12:07:03 2007
%%Title: 4891e
%%LanguageLevel: 3
%%DocumentData: Clean7Bit
%%Pages: (atend)
%%PageOrder: Ascend
%%EndComments
%%BeginProlog
%%BeginResource: procset PSPrint-Prolog 1.0 0
/ISO1252Encoding 

The "ps" file from windows, which does print well:

%!PS-Adobe-3.0
%%BoundingBox: (atend)
%%Creator: OpenOffice.org 2.0
%%For: bill
%%CreationDate: Mon Jul 30 12:07:03 2007
%%Title: 4891e
%%LanguageLevel: 3
%%DocumentData: Clean7Bit
%%Pages: (atend)
%%PageOrder: Ascend
%%EndComments
%%BeginProlog
%%BeginResource: procset PSPrint-Prolog 1.0 0
/ISO1252Encoding

---

### Post by bill-linux on 2007-07-30
Opps, that "ps" file from windows should be:

%-12345X@PJL COMMENT Panasonic DP-C322 PCL 6
@PJL COMMENT TREATASCHARACTER
@PJL COMMENT version 2K 5.01.054.001
@PJL JOB TIME="2007/07/30 11:26:46"
@PJL JOB NAME="4861.pdf"
@PJL JOB OWNER="Administrator"
@PJL JOB HOST="UNIVERSI-6X13UL"
@PJL JOB PCIP="172.016.239.129"
@PJL SET RESOLUTION=600
@PJL SET RESOLUTIONXY=600-600
@PJL SET BLANKPAPER=OFF
@PJL SET QTY=1
@PJL SET SORTING=STACK
@PJL SET ORIENTATION=PORTRAIT
@PJL SET ECONOMODE = OFF
@PJL SET RENDERMODE=COLOR
@PJL SET OUTBIN=AUTO
@PJL ENTER LANGUAGE=PCLXL
) HP-PCL XL;2;1;Comment (C) Panasonic Communications Co., Ltd. 2005


Sorry!

---

### Post by bogolisk on 2007-07-30
try to find the .ppd or .PPD file that windows use. find some linux savy person and get cups to use that ppd for the printer.

---

### Post by bill-linux on 2007-07-30
I have the printer working in windows already. The problem? Windows doesn't have a ppd file -- it is tied up in some binary format in ddl ... unless there is something I'm missing. I've search my windows box for the ppd and cannot find it. Any advice on where to find it.

---

### Post by bogolisk on 2007-07-30
> **bill-linux said:**
> I have the printer working in windows already. The problem? Windows doesn't have a ppd file -- it is tied up in some binary format in ddl ... unless there is something I'm missing. I've search my windows box for the ppd and cannot find it. Any advice on where to find it.


on my windows laptop, I have ppd files under system32\spool\drivers\...


Your next best bet might be choosing another printer that use PCL6 such as HPs. It's a trial/error thing.

---

### Post by fatality_uk on 2007-12-05
> **bill-linux said:**
> At my office we have a Panasonic DP-C322 photocopier/printer. I'm using CUPS to print to this via a network. Here's the problem: The PPD for this printer is for Adobe-Postcript 3.0, but our particular model doesn't have this "module" - it costs some $3000! - instead it is PCL 6. So, when I send ps file generated from this PPD to the photocopier/printer it prints the first line then 100 or so blank sheets. If instead I generate a "ps" file in windows and then send it via linux (lpr -Ppanasonic test.ps, for example) it prints just fine. The difference between the linux "ps" file and the windows generated file is capture completely in the headers, which I've enclosed below.

It appears to me that Windows is generated a PCL file, while the linux ppd is generate a true postscript file. Fine, I loaded a generic PCL6 ppd from linuxprinting.org and it still generated a ps file nearly identical the one listed below. Should this not make a PCL file? Is there something big that I'm missing here?

Linux "ps" file header (this doesn't print well):

%!PS-Adobe-3.0
%%BoundingBox: (atend)
%%Creator: OpenOffice.org 2.0
%%For: bill
%%CreationDate: Mon Jul 30 12:07:03 2007
%%Title: 4891e
%%LanguageLevel: 3
%%DocumentData: Clean7Bit
%%Pages: (atend)
%%PageOrder: Ascend
%%EndComments
%%BeginProlog
%%BeginResource: procset PSPrint-Prolog 1.0 0
/ISO1252Encoding 

The "ps" file from windows, which does print well:

%!PS-Adobe-3.0
%%BoundingBox: (atend)
%%Creator: OpenOffice.org 2.0
%%For: bill
%%CreationDate: Mon Jul 30 12:07:03 2007
%%Title: 4891e
%%LanguageLevel: 3
%%DocumentData: Clean7Bit
%%Pages: (atend)
%%PageOrder: Ascend
%%EndComments
%%BeginProlog
%%BeginResource: procset PSPrint-Prolog 1.0 0
/ISO1252Encoding

Better late than never!!!
Bill, visit [http://www.workio.info/](http://www.workio.info/) for the PPD.
I got mine from there. Not had any luck configuring it but its DEFINATELY the right PPD

---

