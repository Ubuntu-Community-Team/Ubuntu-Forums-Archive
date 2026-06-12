---
title: "Special characters not displaying correctly"
date: 2006-10-31
forum: General Help
---

### Post by zeeR on 2006-10-31
I downloaded edgy and made a clean install of it, after removing dapper. The problem is that now, every letter like "á, à, ô" and all of that, aren't displaying correctly! it appears as a question mark...This happens on movie subtitles, and filenames, for example..

My chosen ubuntu language was portuguese,now is english,but this problem happened from the beggining, in both of the languages. And although i don't remember really well, i think that on dapper this didn't happen! I remember watching movies and not noticing any problem with the special characters...


Here's a screen, the little square was supposed to be an "ó"

---

### Post by jordilin on 2006-10-31
Go to System->Administration->language support and choose your preferred language. Hope this will solve your problem.

---

### Post by zeeR on 2006-10-31
i think you didn't read well...The installation language was portuguese, the problem occured, i changed it to english, and it still happens... I'm portuguese, so why would i have to change it to my desired one?...It was portuguese! I changed it to english for personal taste...i wanted it to be english...I'd say the problem has nothing to do with the languages...

---

### Post by jordilin on 2006-10-31
> **zeeR said:**
> i think you didn't read well...The installation language was portuguese, the problem occured, i changed it to english, and it still happens... I'm portuguese, so why would i have to change it to my desired one?...It was portuguese! I changed it to english for personal taste...i wanted it to be english...I'd say the problem has nothing to do with the languages...
Right, but you need the Portuguese language support.

---

### Post by zeeR on 2006-10-31
> **jordilin said:**
> Right, but you need the Portuguese language support.

I opened the language support window, and in fact, there were some files missing. After installing them all, i tried to open a movie...and the subtitles still show the same problem! I'll try to download other subtitles, but i doubt that's the problem... Thanks for all the help, and keep it coming ;)

---

### Post by zeeR on 2006-11-03
I found the problem...It seems that windows uses a different codification for these special characters...The question mark inside the square only happened when i copied things directly from windows to the linux HDD (there is a program that allows you to)...When copying from other media, as a dvd or a pen drive, all the special characters appear normally...also, when browsing the linux hdd with windows, all the special characters written in linux don't show up in windows either! it's an OS compatibility problem...

Hope this helps anybody with the same problem...

---

