---
title: "How to create a list file using multiple directories- pls help"
date: 2014-09-17
forum: General Help
---

### Post by PratterFak on 2014-09-17
To any Terminal ninja out there,

I want to create one list file that contains all of the files of mulitple directories.

This is the format I'm using now and it works...

**ls -R /folder/path/directory1 /folder/path/directory2 | grep -e '\.filetype$' -e '\.filetype$' -e '\.filetype$' > ~/destination/file.txt**

However, the problem I can't figure out is the following:

When I do the above command, it creates an alphabetical list of directory1. It then creates an alphabetical list of directory2 and places those results on top of the results for directory1 in the file. So, my result is 2 seperate alphabetical lists. Is there any way to merge the results of these 2 directories prior to sorting them? My goal is to have one alphabetical list of the total contents of these 2 directories.

Any help would be greatly appreciated.
Thanks!

---

### Post by TheFu on 2014-09-17
That command didn't work on my box. Why have 3 identical greps?

I'd use **find** for this - something like **find . -ls**
Might need to **sort** it.

Perhaps if you showed the desired output?

---

### Post by PratterFak on 2014-09-17
Yep, "sort" was the key. Wow, I was making this more complicated in my mind than it needed to be... lol So, my resulting command that works perfectly now is-

**ls -R /folder/path/directory1 /folder/path/directory2 | grep -e  '\.filetype$' -e '\.filetype$' -e '\.filetype$' | sort >  ~/destination/file.txt**

Thanks!

*The 3 different greps are to retrieve only 3 specific type of files for the list.

---

### Post by TheFu on 2014-09-17
[B]find /path-to-top -type f -iname "*pattern1*" -o iname "*pattern2*" | sort > ~/target/files.txt
[/B]
Or if you use **locate** to pre-build a DB .... which will be much, much faster.

Seems odd to get 100 files, then just keep 3 of them.  OTOH, there are 1,000 different ways to solve these sorts of problems.

---

