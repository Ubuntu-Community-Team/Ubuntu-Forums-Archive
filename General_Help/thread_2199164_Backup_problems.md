---
title: "Backup problems"
date: 2014-01-12
forum: General Help
---

### Post by grier-devon on 2014-01-12
Hello Everyone,
So I am trying to use the stock Back up Utility in Ubuntu, I have it backing up to a folder on my external HDD. When I try to do the back up this is the error message I continue to get 
> Error opening file '/media/megan/PS3/mbf/duplicity-full.20140112T171825Z.vol1.difftar.gz': Input/output error

The backup works fine if I set it to the external HDD itself but keeps failing when I try to set the backup to specific folder on the external HDD, I want to backup my wifes computer and my computer each to there own folder since I only have one external HDD. Any ideas where to start to fix the situation? Thanks.

---

### Post by ibjsb4 on 2014-01-12
I am not familiar with your back up system, there are many different ways to backup and for starters there is Oldfred :)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=backup+oldfred&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=backup+oldfred&sa=Search&cof=FORID:9)

Myself I use rsync, its already on board (part of the default install).  And a GUI like grsync and/or luckybackup.

I also use a data partition.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=data+partition&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=data+partition&sa=Search&cof=FORID:9)

Some choose to use a home partition.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=home+partition&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=home+partition&sa=Search&cof=FORID:9)

Am I anywhere close to answering your question :D

---

### Post by grier-devon on 2014-01-13
What I found the issue to be was I needed to reformat the HDD, I am not sure why but it fixed it.

---

### Post by ibjsb4 on 2014-01-13
Nice find :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

