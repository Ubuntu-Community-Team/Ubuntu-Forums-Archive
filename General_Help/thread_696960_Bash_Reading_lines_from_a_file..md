---
title: "Bash: Reading lines from a file."
date: 2008-02-14
forum: General Help
---

### Post by spupy on 2008-02-14
Hi people.

I got a file with a song name on each line. I want to write a script that creates a mpd playlists from this file. But for this purpose i need to have some for cycle iterating over the file, and on each cycle the current line of the file is stored in a variable. Something like:
```
for $songname in this_is_somehow_the_songlist
do
    #here some stuff done with $songname
done
```

I never wrote for cycles in bash scripts, and i have no idea how to extract the lines of the file one at a time. Any help is highly appreciated.
Thank you for your time!

---

### Post by RedSquirrel on 2008-02-14
You can use the "while read" construct. See:

[http://tldp.org/LDP/abs/html/loops1.html](http://tldp.org/LDP/abs/html/loops1.html)

which is part of 

[Advanced Bash-Scripting Guide]("http://tldp.org/LDP/abs/html/index.html")

(a worthwhile read ;)).

---

### Post by spupy on 2008-02-15
Thanks! I know that guide, but it didn't occur to me that it would be easier with "while". And there was some tricky construction with piping the output of cat to the while statement, that is doing exactly what i need.

---

