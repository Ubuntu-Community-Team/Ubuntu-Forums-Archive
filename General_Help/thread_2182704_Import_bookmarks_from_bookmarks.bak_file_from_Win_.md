---
title: "Import bookmarks from bookmarks.bak file from Win XP"
date: 2013-10-22
forum: General Help
---

### Post by broliukas on 2013-10-22
Hi,
I'd like to have my Windows Chrome bookmarks on my Ubuntu Chrome.
My Win XP partition crashed, ergo I can not export my Chrome bookmarks in to an .html file in Windows. I do have my 'Bookmarks' and 'Bookmarks.bak' file. I tried to replace the original 'Bookmarks' file in my  /home/<user_name>/.config/google-chrome/Default folder, with the corresponding file from windows, but that did not work - all it did was remove all the bookmarks that I did have originally in my Ubuntu Chrome.
I tried syncing by logging in to Chrome with my gmail account, but all that gave me was several bookmarks from over a year ago.

I tried DTFG, but to no avail.
I am relatively new to Linux (say 2 months of exp).
Help plz. This is my first post ever ;)

---

### Post by coffeecat on 2013-10-22
Is this of any help?

[https://github.com/bdesham/py-chrome-bookmarks](https://github.com/bdesham/py-chrome-bookmarks)

It looks as though the script will simply take the Bookmarks file and output it to a html file which you can then use to import into your Ubuntu Chrome.

---

