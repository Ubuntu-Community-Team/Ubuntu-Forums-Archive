---
title: "Failure to download extra data files (mscorefonts)"
date: 2016-11-23
forum: General Help
---

### Post by MadMonkey1966 on 2016-11-23
Recently i have been getting this message when i have turned my PC on.

[ATTACH=CONFIG]272320[/ATTACH]
I have searched Google & the Ubuntu Forums, and tried various fixes but to no avail. It isn't a major issue, and i haven't yet found any applications that it effects, but it just gets annoying every morning.
Any help getting rid of it & solving the problem would be greatly appreciated :D

---

### Post by howefield on 2016-11-23
Have you got all the fonts actually installed ?

Loading up Libreoffice Writer and looking for andale mono, arial, arial black, comic sans, courier, georgi, impact, times new roman, trebuchet, verdana, and webdings should tell you.

If you actually have the fonts the following might get rid of the popup.

```
sudo touch /var/lib/update-notifier/package-data-downloads/ttf-mscorefonts-installer
```

---

### Post by MadMonkey1966 on 2016-11-23
Thanks howefield for the quick reply.
I checked in Libreoffice Writer and the files are there, so i ran that piece of code in the Terminal and re-booted.
So far all is good, so fingers crossed.
If all is still ok later, i will close the thread.
Many thanks for that speedy solve, cheers Ian :cool:

---

### Post by howefield on 2016-11-23
Cool, just give it a day or two to make sure it doesn't come back and let us know.

---

### Post by cobras on 2017-01-08
This seems to have worked for me as well.

---

