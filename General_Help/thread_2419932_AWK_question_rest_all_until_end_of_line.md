---
title: "AWK question: rest all until end of line?"
date: 2019-05-27
forum: General Help
---

### Post by ajamc on 2019-05-27
Hello ubuntu forums.
I'm first here, don't know where to ask my question exactly.
(If this question doesn't belong here, tell me the proper destination URI, then I will move.)

When I use AWK, $1 ... $100 arguments for 'print' command are the fields.
Then, if I want to specify all the rest things until the end of line, what shall I use?

Here is an example. I want to list all the files with the paths and sizes.
Then, I tried BASH command as below.
[sudo find . -type f -ls | awk '{print $11"\t"$7}']
So, [find . -type f -ls] part will give me the lines like below.
14051   28 -r-x------   1 1027     users       27972 Dec 19  2015 path/filenamekakaka
Then, $7 will be exactly the size. But, $11 would be only the first part of filename if it has spaces within it.
...
I have to debug my awk code like [awk '{print $@@"\t"$7}']... but I don't know what I have to use in $@@ to specify "all the rest parts from 11th until end of line".
Please help me.
Thanks in advance.

---

### Post by ajamc on 2019-05-27
sudo find . -type f -ls | awk '{size=$7;$1="";$2="";$3="";$4="";$5="";$6="";$7="";$8="";$9="";$10="";print $0"\t"size}'
...
what the... this works but look so hasty... shame.

---

### Post by CatKiller on 2019-05-27
My knowledge of awk is scant. NF for "number of fields" is available, so you can simply iterate printing the fields from 11 till the last field, if you wanted.

---

### Post by Holger_Gehrke on 2019-05-27
I'd try a substring of $0 starting at the index where $11 is found in $0:

```

find . -type f -ls|awk '{print substr($0,index($0,$11))}'

```

Since $11 should be './' plus the first word of the filename, it's reasonably certain not to be found before the match we want to find, at least in this case. Might not be a good solution for other kinds of input.

On the other hand: if all you want is to get the name and the size, then I wouldn't bother with awk at all. I'd just use the '-printf' option of find and give it a format specifying which fields I want, something like '%-60p\t%15s\n' (path and filename with a width of 60 characters left aligned,a tab, filesize in bytes with a width of 15 characters and a  newline) in this case.

Holger

---

### Post by ajamc on 2019-05-29
Thank you so much :)

---

