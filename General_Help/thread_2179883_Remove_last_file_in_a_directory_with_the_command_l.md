---
title: "Remove last file in a directory with the command line"
date: 2013-10-10
forum: General Help
---

### Post by Mimo_Camussi on 2013-10-10
Hello,

I need to delete the last file in a list within a directory. How do I do that using the command line?

[COLOR=#800080]*rm "file_name"*[/COLOR] is not enough, as I have a huge list and I don't know the names of the files.

Thanks in advance :)

---

### Post by TheFu on 2013-10-10
I didn't script this, but 
\ls -t1 - will order the output by time in 1 column.
tail -n 1 or 2 should grab the last 1 or 2 lines in the output.
**\ls -t1|tail -n 1**

Oops, that gets the oldest 1 file - you want the newest?  - use **head -n 1**

Then probably just pipe that into** xargs**.
Does that make sense?

---

### Post by sisco311 on 2013-10-10
Hi, Mimo_Camussi and welcome to the forums!

The output of ls is formated for humans and will cause bugs in scripts. Please check out a [http://mywiki.wooledge.org/ParsingLs](http://mywiki.wooledge.org/ParsingLs) and BashFAQ 003 (link in my signature).

---

