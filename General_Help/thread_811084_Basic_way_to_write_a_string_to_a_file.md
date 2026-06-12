---
title: "Basic way to write a string to a file"
date: 2008-05-28
forum: General Help
---

### Post by kag on 2008-05-28
Hi,
I want to install a cron that would run from Monday to Friday at around 8PM. This job would simply write a string to /home/kag/news.strm.

This string would look like this:
[http://www.example.com/20080527.wmv](http://www.example.com/20080527.wmv)

Each time the cron would run, the date in the filename would be updated with today's date. I would then be able to easily always watch the latest newscast through my Xbox (XBMC).

What would be the most basic way (no dependencies on other things if possible) to do this?

Thanks!

---

### Post by flaggh on 2008-05-28
echo http://www.example.com/$(date +%Y%m%d).wmv >> /home/kag/news.strm

---

### Post by kag on 2008-05-28
For the record, my worker gave me the following command and it works like a charm:

```
echo http://ms.radio-canada.ca/$(date +"%Y")/medianet/CBAFT/LeTelejournalAtlantique$(date +"%Y%m%d")1800.wmv?MSWMExt=.asf > /media/Data/Telejournal.strm
```

I saved that string to a file named Telejournal.sh and marked it as executable (chmod +x Telejournal.sh).

I then installed the following cron so it will run at 6PM monday through friday:
```
# m h  dom mon dow   command
  0 18 *   *   1-5   ~/telejournal.sh
```

---

### Post by bingoUV on 2008-05-28
```

echo 'http://www.example.com/'`date +%Y%m%d`.wmv > /home/kag/news.strm

```

---

