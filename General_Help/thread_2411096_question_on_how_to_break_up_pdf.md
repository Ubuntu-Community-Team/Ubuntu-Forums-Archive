---
title: "question on how to break up pdf"
date: 2019-01-24
forum: General Help
---

### Post by jgw on 2019-01-24
Does anybody know if there is a way to break up a pdf page of pages.  I am talking about one of those single page pdf installation pages into its constituent parts so that I can print each page individually.

Thank you...................

---

### Post by #&amp;thj^% on 2019-01-24
Splitting up is easy for a PDF file: [https://linuxcommando.blogspot.com/2013/02/splitting-up-is-easy-for-pdf-file.html](https://linuxcommando.blogspot.com/2013/02/splitting-up-is-easy-for-pdf-file.html)

---

### Post by jgw on 2019-01-24
Thank you for the reply.

First, the installation of pdftk is different - goto [https://askubuntu.com/questions/1028522/how-can-i-install-pdftk-in-ubuntu-18-04-and-later](https://askubuntu.com/questions/1028522/how-can-i-install-pdftk-in-ubuntu-18-04-and-later)  for answer

After I got it installed I find that my question wasn't clear.  I have a pdf file with 2 pages.  Each page holds multiple hages.  The first page, for instance, holds 6 pages.   I think what I am going to have to do is to edit the file and then grab pages parts of the main page, then save it, etc.

Sorry for the confusion..........
Thanks again!

---

### Post by #&amp;thj^% on 2019-01-24
Hmm, well you could also use "pdftotext"
Example:```

pdftotext '/home/me/Documents/Iptablespdf' -f 1 

```
In my example i printed just the text contained on the 1st page in my .pdf
result:
```
Linux: 25 Iptables Netfilter Firewall Examples Fo...

https://www.cyberciti.biz/tips/linux-iptables-exam...

nixCraft

Linux Tips, Hacks, Tutorials, And Ideas In Blog Format

Linux: 25 Iptables Net&#65533;lter Firewall
Examples For New SysAdmins
last updated June 15, 2018 in Iptables, Linux, Linux distribution, Linux Embedded
devices, Linux laptop

Linux comes with a host based &#65533;rewall called Net&#65533;lter. The
net&#65533;lter is a set of hooks inside the Linux kernel that allows

kernel modules to register callback functions with the network stack.
A registered callback function is then called back for every packet
that traverses the respective hook within the network stack. This
Linux based &#65533;rewall is controlled by the program called iptables to
handles &#65533;ltering for IPv4, and ip6tables handles &#65533;ltering for IPv6. I strongly recommend
that you &#65533;rst read our quick tutorial that explains how to con&#65533;gure a host-based &#65533;rewall
called Net&#65533;lter (iptables) under CentOS / RHEL / Fedora / Redhat Enterprise Linux. If you
are using Ubuntu/Debian Linux, see how to setup UFW for more info. This post lists most
simple iptables solutions required by a new Linux user to secure his or her Linux
operating system from intruders.

1 of 48
```
As seen there are 48 pages available.
I hope I'm helping and not adding more confusion.

---

### Post by Holger_Gehrke on 2019-01-25
Might be a case of using atomic weapons to kill cockroaches, but I'd import the pdf into Inkscape, position and scale the pdf in the drawing area so that the actual page is in the page area of the drawing, print, reposition, print again ...
You could even print to one pdf-file per page and then join those files using pdfunite (from poppler-utils) or pdftk so you end up with the kind of PDF it should have been from the start.

Holge

---

### Post by dragonfly41 on 2019-01-25
[pdfshuffler]("http://ubuntuguide.net/mergesplit-and-re-arrange-pdf-pages-using-pdf-shuffler") also does the job

---

### Post by kc1di on 2019-01-25
I use Master PDF to edit pdf files.  I think you can do it with that. 
Master PDF found here: [https://itsfoss.com/edit-pdf-and-xps-files-in-ubuntu-linux-with-master-pdf-editor-free/]("https://itsfoss.com/edit-pdf-and-xps-files-in-ubuntu-linux-with-master-pdf-editor-free/")

---

### Post by HermanAB on 2019-01-25
Try pdfshuffler.

---

### Post by #&amp;thj^% on 2019-01-25
It's also worth a mention that PDF-Shuffler, which hasn't had a new release since 2012, will be removed from Debian because it depends on the old "python-poppler" package (unless a new version is released that doesn't depend on this package), which will be dropped from Debian 10 "Buster". ....(It's already been removed from the Arch repos)
I've been playing with this one also "PDFArranger":[https://www.linuxuprising.com/2018/12/pdfarranger-merge-split-rotate-crop-or.html](https://www.linuxuprising.com/2018/12/pdfarranger-merge-split-rotate-crop-or.html)
But for the just the way you want a PDF to be, I have to agree with Holger_Gehrke and edit first with Inkscape.
Now we have flooded your mind with all kinds of options. :p

---

### Post by jgw on 2019-01-25
Thanks for all the thoughts!

I went to adobe and the answser, for a single page holding multiple pages was something like:
If you want to break a single page into multiple pages
duplicate the page by the number of pages on the master page (I think there is an easy way to duplicate the master page but haven't a handle on it yet)
sequentially remove ALL pages but the one you want (do this for each of the pages on the master page)
you will end up with each page in a single file which you can then easily merge into a single file holding each page individually

I figure if that is adobe's solution then, I expect, this is probably the best solution.

I will mark this one as solved.   

Want to thank everybody again - THANK YOU!

---

