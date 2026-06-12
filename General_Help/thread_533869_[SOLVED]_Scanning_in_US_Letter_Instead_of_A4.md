---
title: "[SOLVED] Scanning in US Letter Instead of A4"
date: 2007-08-24
forum: General Help
---

### Post by gobbles414 on 2007-08-24
Hi all,

I have an Epson Stylus Photo RX620 all-in-one. Printing and scanning are both working on my system. Aside from not being able to print in reverse order the printer is working well. I did, however, have to edit */etc/papersize* as sudo before being able to print in US Letter size instead of A4.

The scanner is also working well, with one exception obviously. I can scan in US Letter if I select it from a drop-down menu in my scanning program ([gscan2pdf]("http://gscan2pdf.sourceforge.net")). I'd like US Letter to be the default. I know that it's not a gscan2pdf problem since it defaults to US Letter with a different scanner on another computer. FYI, I have deleted xsane and xsane-common -- replacing them with sane.

Thanks in advance.

---

### Post by gobbles414 on 2007-08-24
It looks like gscan2pdf will remember my preference of US Letter. Nevertheless I'd still like to know how to make a system-wide change to US Letter.

---

### Post by gjtoth on 2007-11-22
> **gobbles414 said:**
> Hi all,

I have an Epson Stylus Photo RX620 all-in-one. Printing and scanning are both working on my system. Aside from not being able to print in reverse order the printer is working well. I did, however, have to edit */etc/papersize* as sudo before being able to print in US Letter size instead of A4.

The scanner is also working well, with one exception obviously. I can scan in US Letter if I select it from a drop-down menu in my scanning program ([gscan2pdf]("http://gscan2pdf.sourceforge.net")). I'd like US Letter to be the default. I know that it's not a gscan2pdf problem since it defaults to US Letter with a different scanner on another computer. FYI, I have deleted xsane and xsane-common -- replacing them with sane.

Thanks in advance.

May I ask how you got your scanner working, please?  Mine was working until the upgrade to Gutsy.

---

### Post by gjtoth on 2007-11-22
Got it!  had to add a line to the epkowa.conf file... I'm up and scannin'

---

### Post by newraid on 2007-12-17
Hi
Can you tell me what that line contains
Thanks

---

### Post by rbmorse on 2007-12-17
> **gobbles414 said:**
> It looks like gscan2pdf will remember my preference of US Letter. Nevertheless I'd still like to know how to make a system-wide change to US Letter.

check the content of /etc/papersize  It's normal text file.  I changed what was there to 

letter

and saved the file.  Beginning with the next session, letter seems to be the system default paper size.

---

