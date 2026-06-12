---
title: "Upgrade to Kubuntu 13.04 - LibreOffice doesn't display EPS objects in fullscreen mode"
date: 2013-04-27
forum: General Help
---

### Post by DonkeySalami on 2013-04-27
Hello all,

I upgraded my computers to Kubuntu 13.04. Big mistake - LibreOffice doesn't display imported EPS graphics in Fullscreen mode but does in not-fullscreen mode. It also doesn't put them in exported PDF files. Unfortunately my presentations use a lot of EPS graphics. :(

This is pretty much a catastrophe for me... Is this a known issue? Any chance of having this fixed in short-term?

Thanks!

---

### Post by gordintoronto on 2013-04-27
Have you tried installing the PDF printer, and print from LibreOffice? cups-pdf

---

### Post by DonkeySalami on 2013-04-28
Hi,

thanks for the idea - unfortunately the EPS objects are also missing in the cups-pdf output. :(

I'm using LibreOffice Impress Version 4.0.2.2 (Build ID: 400m0(Build:2)).

The strange thing is that in "work mode" the objects are displayed correctly. But not in slideshow mode. Do these modes use different rendering engines?

I still have an older version (3.5.4.2) that can read and convert the files to PDF. Unfortunately that is on a laptop that hangs regularly due to IO errors making this quit a nuisance. :(

---

### Post by simoniux on 2013-05-24
I can confirm the same problem. After upgrading to ubuntu 13.04 64-bit (and LibreOffice 4.0.2), eps figures are not shown in slideshow mode nor are they exported to pdf. No problems with other formats (jpg,png,gif). 
This is a major problem.

---

### Post by nozarm on 2013-07-05
I am having the same problem.  Generated pdf file does not show eps figures in a presentation I made prior to upgrading to 13.04.  png files are exported.  

Is there a solution for this?  I'd rather not go through the pain of converting all the eps figures to png first and reimporting them.

Thanks,
Mina

---

### Post by puttux on 2014-07-01
I have this same problem on Ubuntu 14.04 LibreOficce Version: 4.2.3.3 Build ID: 420m0(Build:3)

---

