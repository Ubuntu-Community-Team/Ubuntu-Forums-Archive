---
title: "Compressing files based on filenames"
date: 2007-09-11
forum: General Help
---

### Post by sparkles on 2007-09-11
Ordinarily at the end of each week I compress files that have been generated out of a batch process that's run on the weekend, but I've been lazy for the past year and haven't done it so now I have around 320K files that I need to compress into weekly files.

The files are all named MMDDxxxx.xxx (as in month, then day and then different stuff after that) e.g. 09121111.txt, and they are compressed into MMDD.tar.gz. Is there something that can be done with bash to compress files based on the first 4 letters of the filename?

TIA

---

### Post by p_quarles on 2007-09-12
You can use regular expressions with tar, so it should be pretty simple. I can't easily try this, since I don't have any appropriate sets of files, but here's how I would do it:
```
tar -zcvf 0912.tar.gz 0912*.txt
```
Rinse, wash, repeat. 

Like I said, that *should* work. If I were you, I would copy some files to a separate directory and test it before going live. 

It's probably also possible to automate this even more, by using variables to create tarballs that match the dates of the contents without typing in each individual day. I'm not good enough with regular expressions to advise you on this, though.

---

### Post by Jasper84 on 2007-09-12
Pretty sure we can do better much then doing that 50 times manually... But i have no experience with that. 

i=0
while [ i -lt 10000 ] do
let i=i+1;
tar -zcvf $i.tar.gz $i*.txt;
done;

Not exactly well written.. tar will whine a _lot_ about absence of arguments. :( (approx 10000 times actually.. Will spend more time whining then compressing :(. Someone who actually knows a little bash should advise here :).
I will test it. (still suggest you backup first) This to generate a list of stuff:
i=0;
while [ $i -lt 100 ];do
   let i=i+1; 
   echo $i;
  touch $i*gaga.txt; 
done;

---

### Post by pmg on 2007-09-13
Assuming you want to compress all the files in a directory:
```
for i in `ls | cut -c1-4 | sort -u`; do
echo tar -czf /some_other_dir/$i.tar.gz $i*
done

```
The echo is so it just writes out the commands and doesn't actually run them.  If that looks good you can redo without that, or better yet leave that in and add one more line of the tar without the echo, so you can see it write out each tar command before running it and you'll see how much progress is being made.

---

### Post by HermanAB on 2007-09-13
The 'find' command can search on a regular expression, recursively traverse subdirectories and spawn a process whenever it finds a match.  You don't need to write a loop or anything.   It can be immensely powerful - the father of all bombs if you are not careful.

Something like this:
find . -name \*.txt -print -exec tar -zcvf {} \;

Read the man page. I haven't tested the above.  There is no warranty and don't blame me if it causes cancer or ingrown toenails...

Cheers,

Herman

---

### Post by pmg on 2007-09-13
The **find** command is very powerful and good to know, but in this case, given the need to group files by the first part of their filenames and only run one **tar** for each group, it's easier and more versital using a pipeline and a loop.

---

