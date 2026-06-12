---
title: "what on earth is up with the &quot;search for files&quot; function?"
date: 2008-04-20
forum: General Help
---

### Post by VMOS on 2008-04-20
I'm talking about the one that's under the "go" menu, activates with ctrl-f, I've been somewhat miffed with it's less than stellar performance in ubuntu7.1 but I had other things to try and sort out first. 
Then today I try kubuntu and find the search there works just fine and dandy so I go back and try my ubuntu pc again and give it a go. 
I try searching for "system.reg", no results even though I'm sure it's there somewhere.
I open up my home folder and the first file I spot is "firefox wallpaper.jpg" so I do a search for "fire" it doesn't find the wallpaper despite the fact that I'm looking straight at it, but it does find some text files which contain the word "fire" somewhere in them
What's the deal with that and any idea how to fix it?

/edit and as if that wasn't enough, the search that's under the "places" menu won't look in any of my ntfs drives, oy

---

### Post by diaa on 2008-04-20
see [http://ubuntuforums.org/showpost.php?p=4675895&postcount=6](http://ubuntuforums.org/showpost.php?p=4675895&postcount=6)

---

### Post by miketowninc on 2008-04-20
> **diaa said:**
> see [http://ubuntuforums.org/showpost.php?p=4675895&postcount=6](http://ubuntuforums.org/showpost.php?p=4675895&postcount=6)
 Can the indexing slow down your computer alot? Should  i turn it off? I really dont need it and I only have 256 RAM.

---

### Post by chrisccoulson on 2008-04-20
FWIW, this has been fixed in Hardy. Nautilus is no longer built with Tracker support, so it's search function works as expected (searching file/folder names)

---

### Post by diaa on 2008-04-20
> **miketowninc said:**
> Can the indexing slow down your computer alot? Should  i turn it off? I really dont need it and I only have 256 RAM.

I don't have a benchmark that says that tracker is slow but with 256 of RAM I think you should turn all non-essential services down also I recommend using [locate]("https://help.ubuntu.com/community/FindingFiles#head-3d0ebe3e11ed426088ba88dbe615e90dd9980b1b") if you are comfortable with the command-line.

---

### Post by ghostdog74 on 2008-04-20
> **VMOS said:**
> 
I try searching for "system.reg", no results even though I'm sure it's there somewhere.
open a terminal, type in
```

find / -type f -name "system.reg"

```
if the file exists, it will show. If not, you will see no results.  GUI is not the answer everytime.

---

### Post by ryanhaigh on 2008-04-20
I disabled tracker indexing because I keep my files organised and don't need the overhead. Of course this completely broke the search function in nautilus so after a couple of months I created this howto: 
[http://ubuntuforums.org/showthread.php?p=4524368](http://ubuntuforums.org/showthread.php?p=4524368)
With that you can recompile nautilus in gutsy without tracker support so that search works properly again.

---

