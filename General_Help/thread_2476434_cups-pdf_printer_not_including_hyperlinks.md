---
title: "cups-pdf printer not including hyperlinks?"
date: 2022-06-26
forum: General Help
---

### Post by csae2608 on 2022-06-26
Hello,

i am on Ubuntu 20.04 and noticed just today that the cups-pdf printer package wont include Hyperlinks that are "clickable" in the resulting pdf.
It functions when i choose to "save to PDF" manually in the printing window, but not if i choose the cups-pdf printer.

Is there something am missing?
if not, where can i report the issue?

thanks

```
printer-driver-cups-pdf is already the newest version (3.0.1-6).

```

---

### Post by #&amp;thj^% on 2022-06-26
Mine works, how are you checking or opening the PDF?
I'll use Atril or firefox to open the printed PDF
See if the links work from my uploaded PDF
EDIT: Never mind, just remembered I'm not on Ubuntu today, I can confirm what you see now>>>No clickable links on Ubuntu/Debian only
Here's an old bug report: [https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/1551949](https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/1551949)

---

### Post by csae2608 on 2022-06-26
yes, your PDF has clickable links, tried with the standard-pdf viewer for Ubuntu 20.04, gotta be "Document Viewer".
i have not understood your second part, or edit: are you able to produce clickable PDF's on Ubuntu or Debian with cups-pdf , or not?
on Ubuntu 20.04, it seems not to function.

---

### Post by #&amp;thj^% on 2022-06-26
> **csae2608 said:**
> yes, your PDF has clickable links, tried with the standard-pdf viewer for Ubuntu 20.04, gotta be "Document Viewer".
i have not understood your second part, or edit: are you able to produce clickable PDF's on Ubuntu or Debian with cups-pdf , or not?
on Ubuntu 20.04, it seems not to function.

On arch linux, we have clickable links, on Debian/Ubuntu NO clickable links printed to PDF :(
> **1fallen said:**
> I can confirm what you see now>>>No clickable links on Ubuntu/Debian only


---

### Post by csae2608 on 2022-07-07
> **1fallen said:**
> On arch linux, we have clickable links, on Debian/Ubuntu NO clickable links printed to PDF :(

do you have clickable links when "save to PDF" or with cups-pdf which on my computer shows in the printing section just as "PDF"?[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290697&stc=1[/IMG]

---

### Post by #&amp;thj^% on 2022-07-07
save to PDF
Your not doing anything wrong, there just are "No" clickable links with PDF's on Ubuntu.
EDIT: I have it working with "Okular" on Debian Rolling
```
OS: Kaisen GNU/Linux 2.1 (rolling)
```
and:
```
apt policy okular
okular:
  Installed: 4:21.12.3-2
  Candidate: 4:21.12.3-2
  Version table:
 *** 4:21.12.3-2 500
        500 https://deb.kaisenlinux.org kaisen-rolling/main amd64 Packages
        100 /var/lib/dpkg/status

```

---

### Post by csae2608 on 2022-07-10
@1fallen,
go get myself understood; 
clickable links are produced/functions with "save as PDF" inside firefox/chromium with ubuntu or Kaisen2.1
clickable links are not produced when instead used is "printer-driver-cups-pdf" which adds section "PDF" to printer, and this is the undesired behaviour.

thanks

---

