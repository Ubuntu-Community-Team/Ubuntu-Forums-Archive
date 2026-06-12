---
title: "Dapper WINE install Quicken 2005"
date: 2006-12-30
forum: General Help
---

### Post by Barney on 2006-12-30
On Dapper, I'm trying to install Quicken 2005 thru Wine 0.9.28; and I get as far as "Publishing product information" 89% and everything freezes.

Any ideas?

---

### Post by Stemp on 2006-12-30
[Wine Quicken]("http://appdb.winehq.org/appview.php?iAppId=107") ?

---

### Post by Barney on 2007-01-01
Perhaps I have worded my request for help badly.

I'm running Dapper, have WINE installed (9.28 from synaptic), have run winecfg and attempted  to install Quicken 2005, and the install gets as far as "Publishing product information" 89% and everything freezes.

Unfortunately, Quicken 2005 will not export .qif files, or I would be using Gnucash; and I have too much data from quicken to try to re-enter everything into Gnucash.

Ideas?

---

### Post by DnasTheGreat on 2007-01-01
Wine contains an application database with information about each app, which the previous poster linked to.
[http://appdb.winehq.org/appview.php?iVersionId=2510](http://appdb.winehq.org/appview.php?iVersionId=2510)
Apps also have hooks into a Bugzilla, so that bugs can be reported.

Strange that it doesn't install though.
[http://bugs.winehq.org/show_bug.cgi?id=3166](http://bugs.winehq.org/show_bug.cgi?id=3166) reports that (as of 11/7) it does. And Wine 0.9.28 is recent enough for that. Perhaps open another bug?
Are you sure you are running 0.9.28? Run wine --version. The version of wine in Dapper repositories is only 0.9.9.
If you want the latest versions, add Wine's official repository.
[http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)

But installation not working isn't too huge of a barrier. Try copying the installation over from a previous Windoze install.

Though, it seems that Quicken 2005 does not work very well, from the db anyway.

---

### Post by Barney on 2007-01-04
Great One,

Thanks, and yes, to all of the above.  I would rather get a clean install using wine than use something from a windows installation - I'll keep trying.

Barney

---

### Post by shutterbc on 2007-01-14
I'm using Edgy and was able to get 2005 Premier to install without a hitch.  However I'm having trouble running the program.  If I try to run ```
wine qw.exe
``` then I get the following error:

```

err:ole:TLB_ReadTypeLib Loading of typelib L"C:\\Program Files\\Quicken\\QWUTIL.dll" failed with error 1813

```

I'm using wine 0.9.22, so I think I might install from the wine repos next.

Stupid question -- how do I launch apps using the .lnk files?

---

