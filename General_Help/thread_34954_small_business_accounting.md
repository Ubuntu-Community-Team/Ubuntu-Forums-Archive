---
title: "small business accounting"
date: 2005-05-17
forum: General Help
---

### Post by hoover93 on 2005-05-17
can anyone recommend a small business accounting package for linux?  nothing too complicated, i just need the ability to invoice customers, enter expenses, and balance a checkbook.

i'd prefer a native linux application rather than a windows app running through wine or cross over office.  currently i use peachtree accounting but i have not been able to make it work with wine or cross over.

ease-of-use would be helpful too.  i tried gnucash about a year ago but i couldn't  figure out how to insert my company logo on an invoice.  this is quite easy in peachtree, but i couldn't make it happen with gnucash.  maybe things have improved in the last year?

a capable accounting package is the only thing holding me back from going completely microsoft-free!

---

### Post by Burgundavia on 2005-05-17
You might want to try quasar by linux canada, but I don't know if it has been packaged yet.

Corey

---

### Post by derrick1985 on 2005-05-17
[ftp://ftp.linuxcanada.com/pub/Quasar/1.4.5/binaries/Fedora/Core3/](ftp://ftp.linuxcanada.com/pub/Quasar/1.4.5/binaries/Fedora/Core3/)

I don't know if sudo alien *.rpm
and sudo dpkg -i *.deb on the files would install it correctly, but it's worth a shot.

EDIT: Found a screenshots link too [http://www.linuxcanada.com/quasar.shtml](http://www.linuxcanada.com/quasar.shtml)

---

### Post by rajaiskandarshah on 2005-05-17
i have written an unofficial guide on installing quasar on ubuntu using the firebirdsql database.

[http://www.ubuntuforums.org/showpos...8&postcount=155](http://www.ubuntuforums.org/showpos...8&postcount=155)

appreciate if you can test it out on your machine. i think it is much easier on ubuntu 5.

---

### Post by hoover93 on 2005-05-17
rajaiskandarshah,

the link in your post seems to be broken.  can you repost?

---

### Post by GOwin on 2005-05-18
how small is "small"?

try sql-ledger.com

---

### Post by KiwiP on 2005-06-03
If you car looking for something a bit bigger and complex, try looking at Compiere.

SLQ Ledger is also very good.

KiwiP

---

### Post by KiwiP on 2005-06-05
I have tried converting the RPM into a DEB by using alien.
The conversion seems to go OK, and the installation of the server deb also seem to proceed correctly.
But the client deb produced an error as you can see below.

Any suggestions as to how I can get around this.

$ sudo dpkg -i quasar-client_1.4.5_GPL-2_i386.deb
(Reading database ... 94372 files and directories currently installed.)
Unpacking quasar-client (from quasar-client_1.4.5_GPL-2_i386.deb) ...
dpkg: error processing quasar-client_1.4.5_GPL-2_i386.deb (--install):
 trying to overwrite `/opt/quasar/bin/quasar_setup', which is also in package quasar-server
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 quasar-client_1.4.5_GPL-2_i386.deb

Regards

KiwiP

---

### Post by jonny on 2005-06-16
I've been using Quasar to prepare our church's accounts.  It's very good - much more powerful than I need, in fact - and it's far more intuitive and feature rich than Sage (the most popular small business package for Windows in the UK), which I use in work.

Some of its good features are:

 - Purchase and sales order tracking.  Many small business products lack this functionality.

 - Decent flexibility in the chart of accounts layout.

 - Can be configured for UK VAT with a little care.

 - Extremely comprehensive cash reconcilitiation features, reflecting Linux Canada's commercial interest in POS software

 - All transactions can be voided or amended until accounting periods are closed

 - Good search and drill-down facilities

 - Good bank reconciliation screens

 - Stock (inventory for our transatlantic friends) control

 - Proper database support.  You can easily write your own SQL reports over Postgres - OpenOffice.org2's base offers a simple but effective report writer

 - And, um, it correctly spells cheque without a 'c' or a 'k' in sight.  Worthy of a recommendation alone!

I compiled Quasar from source, following the extremely comprehensive instructions given on the Linux Canada web site.  This worked pretty well, but took some time to see through to completion - I took a couple of evenings.  Unfortunately, I didn't take notes of what I did, but I can remember that my main mistake was to install postgresql after compiling Quasar.  The manual seems to suggest that you can do things the other way around.

Also, some of the dependencies are a little tricky.  Synaptic in ubuntu uses different names for some packages, so you need to search carefully and occasionally  guess - make sure you install the development packages, too.  I also found that the ubuntu version of some packages were too old, and I had to fetch the latest version and recompile.  All this is well documented in the manual, though.

This probably isn't a good first compilation project.  But if you've worked your way through a few configure and make errors before, you'll find it a breeze - albeit a lengthy one.

---

