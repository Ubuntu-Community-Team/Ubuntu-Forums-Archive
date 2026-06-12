---
title: "index.htm &amp; index.html"
date: 2016-10-06
forum: General Help
---

### Post by ex-para on 2016-10-06
I have a Nginx website that I have had for years and changed it from one computer to another lots of times but this time when I install the Nginx software I get index.htm & index.html. The Welcome to Nginx appears only in index.html. I would be obliged if I could be told why this is.

---

### Post by TheFu on 2016-10-07
It isn't clear that there is an issue from the text above.  Is there an issue?

index.html is the default page to be displayed on Unix systems. Linux is a Unix system.
On a Windows system, for historical reasons, the default file was index.htm.

You can configure 1 or both to be the default for your site.  Use the **index** or **try_files** keywords inside the site config files inside sites-available/ directory.

---

### Post by ex-para on 2016-10-11
Thank you for the reply, all is now clear.

---

