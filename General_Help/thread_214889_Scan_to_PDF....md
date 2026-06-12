---
title: "Scan to PDF..."
date: 2006-07-13
forum: General Help
---

### Post by Mtnear on 2006-07-13
I'd like to know if anyone is using the process described in [**THIS**]("http://maconstuff.blogspot.com/2006/05/scan-to-pdf-in-ubuntu-with-beagle.html") blog post for scanning documents straight into pdf format?

It seems like a great script to automate the entire process, but I keep ending up with blank .pdf files.  I launch the script and my scanner seems to make a scan, but following the conversion I am left with a blank .pdf.  Can someone please let me know what I'm doing wrong.  I've made sure that all of the packages that the poster mentions are on my system, and I don't receive any error messages during the process.  Thanks.

---

### Post by balloons on 2006-07-13
Upgrade Xsane, it can scan to pdf, or multipage pdf in the program.

[XSane multipage scanning]("http://www.xsane.org/doc/sane-xsane-multipage-doc.html")


Download and install these two packages
[http://ftp.us.debian.org/debian/pool/main/x/xsane/xsane_0.97-3_i386.deb](http://ftp.us.debian.org/debian/pool/main/x/xsane/xsane_0.97-3_i386.deb)
[http://ftp.us.debian.org/debian/pool/main/x/xsane/xsane-common_0.97-3_all.deb](http://ftp.us.debian.org/debian/pool/main/x/xsane/xsane-common_0.97-3_all.deb)

Or, enable the debian etch repos on ubuntu and force version to the newer xsane.

---

### Post by Mtnear on 2006-07-13
Thanks guitara, although I used the latest files (and some dependencies) from xsane's site rather than the packages you mentioned.  Those pkg's were already installed on my system.  

Anyway, it works great and solves my problem.  Thanks.

---

