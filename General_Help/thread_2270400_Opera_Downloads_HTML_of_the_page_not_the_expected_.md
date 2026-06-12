---
title: "Opera Downloads HTML of the page not the expected data"
date: 2015-03-22
forum: General Help
---

### Post by backfour94 on 2015-03-22
I just tried to download my latest statement from by Bank in .ofx format. However, although the file extension is correct the actual file is HTML rather than the expected text. This also happened when I tried to download an extract from a phpList installation, i.e. html of what looks like the download page rather then .txt of the expected extract.

The HTML looks like the page that the download was coming from rather than the download file. 

Begins with is:

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd"> Transactions – Download transactions – Select account and dates

Running Xubuntu 14, Opera 12.16.

Ta

---

### Post by pqwoerituytrueiwoq on 2015-03-22
check the content type in the header, they probably messed it up and told the browser that is it plain text not a html page

---

### Post by backfour94 on 2015-03-23
Thanks for the reply.  I'm not sure I explained myself properly.

The file that is downloaded is the html for the page, not the file with the download data.  It works fine with Firefox, and used to be fine with Opera.

---

### Post by ajgreeny on 2015-03-23
What happens if you open the html file that downloaded using whatever browsers you have available by right clicking on the html and using "Open with XXX"; does it open the html page you expected in all of them or does it still mess up with Opera?

---

### Post by backfour94 on 2015-03-23
It looks like the original page, i.e. the page from which the download was being requested and not the data being downloaded.

Really wierd, it only seems to be a problem when opening in LibreOffice, and looks like it is something to do with the encoding.  Fine if the file is saved and then opened.

Am closing this thread.

Nope, spoke too soon :--)

When using phplist and trying to export a list of all subscribers.

I save the exported file.

In Opera although a .csv file it is the html for the page, i.e. starts with:

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd" >
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en" dir="ltr">
<head>

In Firefox when I use the same options and method, the file is a also a .csv but this time is has the expected list of subscribers.

---

