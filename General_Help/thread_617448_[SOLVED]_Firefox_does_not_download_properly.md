---
title: "[SOLVED] Firefox does not download properly"
date: 2007-11-19
forum: General Help
---

### Post by PmDematagoda on 2007-11-19
I seem to be facing quite a major problem with Firefox, I cannot download almost any files or save any web pages. This started happening quite recently without any explanation at all. I believe that this may be linked to the Download Statusbar add-on I'm using but the problem was not fixed even after I disabled or uninstalled it.

I would greatly appreciate any help concerning this matter.:)

---

### Post by malfist on 2007-11-19
could you give us a little more information? Exactly what is it doing?

---

### Post by PmDematagoda on 2007-11-19
That is the problem, it's doing nothing at all, as said before. If I download a .deb, it downloads, but I have no idea if it has finished or anything, if it is something like a web page or picture, it does not download it at all.:confused:

---

### Post by malfist on 2007-11-19
Are you using a proxy? If so, check it's connections, if not, make sure firefox isn't trying to use one. Are you using fasterfox? That might be causeing the problem.

---

### Post by PmDematagoda on 2007-11-19
No proxy used, I'm using a direct connection to the internet. And I don't use FasterFox.

---

### Post by Milk &amp; Toast &amp; Honey on 2007-11-19
Hi, PmDematagoda, how are you?
Long time no see, this couple months I haven't online in msn.

Anyway, can you successfully download the link using another browser or try to download the link via wget?
Just to make sure firefox is the problem.

---

### Post by PmDematagoda on 2007-11-20
Hello Milk & Toast & Honey, it has indeed been a long time. :)

I tried downloading stuff using Kazehakase and it works properly, so it must be something with Firefox.

---

### Post by Milk &amp; Toast &amp; Honey on 2007-11-20
PmDematagoda, have you tried to clear the cache and restarting the firefox?

---

### Post by PmDematagoda on 2007-11-20
I tried by clearing the cache as you suggested Milk & Toast & Honey, but it did not work.:(

---

### Post by GavinZac on 2007-11-20
Did you check your download directory? It may have worked downloading stuff, but didnt give you the proper notification that it was done.

---

### Post by PmDematagoda on 2007-11-20
Yes I did, but the files that were supposed to be downloaded were not there.

---

### Post by Milk &amp; Toast &amp; Honey on 2007-11-21
PmDematagoda, 

I never get this problem before, although I've tried Download Statusbar.
Have you (re-)installed the Download Statusbar again, and doing download from that plugin, so we can surely know where the problem is.

Additionally, try running firefox (with no instance started before) from terminal to switch to a different profile.
```

firefox -ProfileManager

```
Create new profile, and try to download the same file (with problem) from there, to make sure the problem's not come from your firefox installation or any other plugin(s).

---

### Post by Nunu on 2007-11-21
I had this before running under windows. I don't think this is going to be of any help but maybe it will. 

When i had this issue with Firefox under windows. I ran an update on it and the problem disappeared. Like i said i don't think this will be the case with Linux, but its worth checking for an application patch or something like that from the Mozilla site

---

### Post by PmDematagoda on 2007-11-28
I just updated to Firefox 2.0.0.10 but the problem is still there.:(

---

### Post by PmDematagoda on 2007-11-29
Solved it:), simply removed the old configuration folder and created a new one, thanks for the solution Milk & Toast & Honey:).

---

