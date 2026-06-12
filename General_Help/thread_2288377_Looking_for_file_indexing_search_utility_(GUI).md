---
title: "Looking for file indexing search utility (GUI)"
date: 2015-07-26
forum: General Help
---

### Post by ncage on 2015-07-26
About 5 years ago it seems that desktop search programs where the craze but unfortunately most have seemed to die :(. Google desktop search was nice. I know linux, i think around the same time, had beagle but it look like it died too :(. Is there currently any descent ones left out there that are being actively developed? Hopefully opensource & doesn't require me to run it under wine. Here are my requirements:
1. like i said above it has to index the files (i don't just want a file search utility like agent ransack under windows).
2. are able customize where it indexes (there are some large networks shared i want to index)

Some nice to have things would be:
1. Advanced search syntax (maybe including regular expressions)
2. index accessible with HTTP (json/html)

Is there anything currently out there?

---

### Post by PhilGil on 2015-07-26
> **ncage said:**
> About 5 years ago it seems that desktop search programs where the craze but unfortunately most have seemed to die :(. Google desktop search was nice. I know linux, i think around the same time, had beagle but it look like it died too :(. Is there currently any descent ones left out there that are being actively developed? Hopefully opensource & doesn't require me to run it under wine. Here are my requirements:
1. like i said above it has to index the files (i don't just want a file search utility like agent ransack under windows).
2. are able customize where it indexes (there are some large networks shared i want to index)

Some nice to have things would be:
1. Advanced search syntax (maybe including regular expressions)
2. index accessible with HTTP (json/html)

Is there anything currently out there?

There's two that I know of in active development, Tracker and Recoll. Tracker is tightly integrated into the Gnome desktop (it's on by default in Gome Shell), but the search options may not as full-featured as you might like. Recoll is my favorite desktop search program. It has an excellent GUI (although there's a bit of a learning curve as the program is very powerful), it has an add-on system that allows you to index the contents/metadata of many different file types and (one of it's best features) you have the choice of whether to index on a schedule (using cron/anacron) or run an indexing daemon. The beauty of this is that, when using recoll on a less powerful PC, you can run the file indexing when the computer isn't being used instead of having it run in the background all the time.

---

### Post by jjpatricio33 on 2016-06-19
DocFetcher
[http://docfetcher.sourceforge.net/es/index.html](http://docfetcher.sourceforge.net/es/index.html)

---

### Post by sudodus on 2016-06-19
Also I would recommend ***recoll***.

---

### Post by HermanAB on 2016-06-19
KDE has some darned search thing that one always has to turn off.

---

### Post by vasa1 on 2016-06-19
> **HermanAB said:**
> KDE has some darned search thing that one always has to turn off.

nepomuk and later baloo?
[https://userbase.kde.org/Nepomuk](https://userbase.kde.org/Nepomuk)

---

