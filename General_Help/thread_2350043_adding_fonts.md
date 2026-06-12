---
title: "adding fonts"
date: 2017-01-20
forum: General Help
---

### Post by papahonk on 2017-01-20
alright here is the deal, older dell running 16.4.1 i want to add some fonts. I typically do a google search first as I have never had much luck with the search on this site. google  finds postings on here that this sites search wont show me. [https://ubuntuforums.org/showthread.php?t=2234738](https://ubuntuforums.org/showthread.php?t=2234738) 
tried to add that as a link but either my computer or this site wouldn't let me type much past before it would try to add to the link. GGRR.  the first posting on there wont work for me  i get a error and permission denied if i try to copy and paste. the next post on that page  says to make another folder. that part works. ```
papahonk@papahonk-Vostro-1720:~$ mv ~/Downloads/BambooGothic-Book.otf /usr/share/fonts/truetype/myttf
mv: cannot move '/home/papahonk/Downloads/BambooGothic-Book.otf' to '/usr/share/fonts/truetype/myttf/BambooGothic-Book.otf': Permission denied

``` what am i doing wrong? am i typing the wrong place. I try not to ask to many questions on here as this website is always a headache for me to navigate.  Its easier to google and find others with the same issue. but this time it seems i'm the only one. 
 thank you for any help

---

### Post by howefield on 2017-01-20
Try prepending your command with sudo.. ie

```
sudo mv ~/Downloads/BambooGothic-Book.otf /usr/share/fonts/truetype/myttf
```

---

