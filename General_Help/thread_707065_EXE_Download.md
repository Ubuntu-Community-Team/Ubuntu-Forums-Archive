---
title: "EXE Download"
date: 2008-02-25
forum: General Help
---

### Post by mkn on 2008-02-25
Congrats on Wubi's inclusion in Beta 5. 

Currently, users have to download the ISO, burn a CD, and then "Install inside Windows". In the final release, will users be able to download an EXE that will let them skip straight to that last step, and from there do an LVPM install if they so please? 

Thanks for all the hard work.

---

### Post by toa on 2008-02-25
> **mkn said:**
> Congrats on Wubi's inclusion in Beta 5. 

Currently, users have to download the ISO, burn a CD, and then "Install inside Windows". In the final release, will users be able to download an EXE that will let them skip straight to that last step, and from there do an LVPM install if they so please? 

Thanks for all the hard work.

Wubi is Ok

but why dont you download the ISO and burn it, and install Ubuntu directly from the CD 

It is useful to have the Live CD available for recovery.

---

### Post by evan d on 2008-02-25
[http://people.ubuntu.com/~evand/wubi/Wubi-8.04-alpha-rev431.exe](http://people.ubuntu.com/~evand/wubi/Wubi-8.04-alpha-rev431.exe)

To address the latter part of your question, I imagine Ago will update wubi-installer.org to include a link to the executable when Ubuntu 8.04 is released in April.  After all, the iso downloader code in Wubi is actively being developed and tested.

---

### Post by ago on 2008-02-25
To clarify, you can find the 8.04 alpha download also on wubi-installer.org. The file is in the FAQ, 8.04 section (and on sourceforge). It is the same file as in evand's link above and the same file you will get from the CD. More up-to-date (and unstable) downloads for testers will be available as usual in [http://wubi-installer.org/devel/minefield](http://wubi-installer.org/devel/minefield). 

Wubi 8.04, also works in stand-alone mode. I.E. it does have a built-in downloader that can grab the ISO for you and use it. Or you can provide your own ISO and place it in the same folder as wubi.exe. So no, there is no need whatsoever to burn a CD to use Wubi. 

Myself and Hampus (mostly Hampus) are also working to improve the downloader, but the current downloader works well with a single URL (which is the case at the moment), less so with multiple URLs (which will be the case after the final release).

---

