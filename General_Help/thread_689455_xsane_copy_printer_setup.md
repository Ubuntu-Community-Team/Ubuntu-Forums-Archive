---
title: "xsane copy printer setup"
date: 2008-02-06
forum: General Help
---

### Post by Randy R on 2008-02-06
I am trying to configure a printer in xsane for the copy function. My printer is is a cups printer on a remote machine.

The remote printer works fine from the machine with the scanner attached, I just am not able to configure the printer to work with xsane.

I tried using the: lpr -P "printer name"  as recommended. That did not work.  Obviously i substituted my printer name.

Thanks in advance.

---

### Post by LarryJ2 on 2008-03-01
Grrr.   Mine didn't work initially either.  {:-(

1.  Do **sudo lpstat -d -p**

You should see something like:

[I]no system default destination
printer BrotherLaser is idle.  enabled since Sat 01 Mar 2008 03:42:21 PM MST[/I]

This tells me that the printer name is BrotherLaser. (Your printer name will be different)

2.  In XSane   Preferences-> Setup ->Copy

I entered ** BrotherLaser**  opposite *Name:*
I entered ** lpr -P BrotherLaser**  opposite *Command:*

3.  I clicked Apply.   The Printer Selection changed to read "BrotherLaser"

4.  In testing,  I found lpr -P printer  filename  to be useful.  For example, ** lpr -P BrotherLaser test.txt**   prints the file test.txt on my CUPS LANed laser printer.  (Nice printer the HL-2070 by the way!)

---

