---
title: "Using the find command with the -size test"
date: 2017-08-01
forum: General Help
---

### Post by John_Patrick_Mason on 2017-08-01
I don't quite get the behavior of the find command with the -size test. If I change my directory to:

```

cd Pictures

```

and then do:

```

ls -lh
total 6.5M
-rw-r--r-- 1 mason mason  26K May 27  2013 file1.png
-rw-r--r-- 1 mason mason 1.5M Sep 20  2013 file2
-rw-r--r-- 1 mason mason 155K Apr  2  2013 file3.jpeg
-rw-r--r-- 1 mason mason 245K Nov 27  2016 file4.jpg
-rw-r--r-- 1 mason mason 675K Jun 14  2014 file5.jpg
-rw-r--r-- 1 mason mason 210K Nov 27  2016 file6.jpg
-rw-r--r-- 1 mason mason 348K May 27  2013 file7.png
-rw-r--r-- 1 mason mason 805K Feb 27  2015 file8.jpg
-rw-r--r-- 1 mason mason 8.6K May 26  2013 file9.png
-rw-r--r-- 1 mason mason  20K Mar  9  2013 file10.jpg
-rw-r--r-- 1 mason mason 1.9M Jun 14  2014 file11.png
-rw-r--r-- 1 mason mason 404K Jun 14  2014 file12.jpg
drwxrwxr-x 2 mason mason 4.0K Mar 18 16:55 Wallpapers
-rw-r--r-- 1 mason mason 145K Jan 15  2015 file13.png
-rw-r--r-- 1 mason mason 6.7K Apr  2  2013 file14.png

```

and finally apply:
```

find ~/Pictures -type f -name "*.jpg" -size -1G

```

I get nothing. Whereas, if I type:

```

find ~/Pictures -type f -name "*.jpg" -size -5G

```

I get:

```

/home/mason/Pictures/file4.jpg
/home/mason/Pictures/file5.jpg
/home/mason/Pictures/file6.jpg
/home/mason/Pictures/Wallpapers/file5.jpg
/home/mason/Pictures/Wallpapers/file4.jpg
/home/mason/Pictures/file8.jpg
/home/mason/Pictures/file10.jpg
/home/mason/Pictures/file12.jpg

```

What gives? Shouldn't I get the same results if I type "-size -1G" than if I type "-size -5G"? I mean all of the .jpg files above are less than 1G anyway.

---

### Post by TheFu on 2017-08-01
I can confirm the same behavior here and it doesn't make sense.  There's something about "-1G" in my limited testing. Other numbers and size modifiers work as expected.

I would use a similar **find** that you are using, btw.  Though I'd use \*jpg - the dot (.) isn't needed except on Windows since it is a regex "match any character" modifier.

---

### Post by steeldriver on 2017-08-01
I agree it's confusing

The key to understanding it is this extract from the man page:

```

              The  +  and  -  prefixes  signify greater than and less than, as
              usual.  [COLOR=#000000]**Bear in mind that the size is rounded  up  to  the  next**[/COLOR]
              [COLOR=#ff0000]**unit.**[/COLOR]  Therefore -size -1M is not equivalent to -size -1048576c.
              [B]The former only matches empty files, the  latter  matches  files
              from 1 to 1,048,575 bytes[/B].

```

So, any file occupying less than 1048576 bytes is rounded up to 1M - and is therefore not less than 'size 1M' (but **is** less than 5M) - same applies to the G multiplier

---

### Post by John_Patrick_Mason on 2017-08-01
[QUOTE=steeldriver]So, any file occupying less than 1048576 bytes is rounded up to 1M - and is therefore not less than 'size 1M' (but **is** less than 5M) - same applies to the G multiplier 				[/QUOTE]

Quick question. If the file size is always rounded up before getting processed by find, doesn't that mean that a file with a size of 10458576 bytes should get rounded up to *2M*B instead of 1MB??? I thought 1MB was equal to 1,000,000 bytes?

---

### Post by steeldriver on 2017-08-01
Well, technically I guess they're MiB (mebibytes - or 2^20 bytes) - although the manual page uses the MB notation:

```

       -size n[cwbkMG]
              File uses n units of space, rounding up.  The following suffixes
              can be used:

              `b'    for  512-byte blocks (this is the default if no suffix is
                     used)

              `c'    for bytes

              `w'    for two-byte words

              `k'    for Kilobytes (units of 1024 bytes)

              `M'    for Megabytes (units of 1048576 bytes)

              `G'    for Gigabytes (units of 1073741824 bytes)

```

---

### Post by him610 on 2017-08-01
```
find ~/Pictures -type f -name "*.jpg" -size -1000M
```
works.

---

### Post by John_Patrick_Mason on 2017-08-01
[QUOTE=steeldriver]Well, technically I guess they're MiB (mebibytes - or 2^20 bytes) - although the manual page uses the MB notation [/QUOTE]

I'm sorry, I'm lost. You need to give me a couple of concrete examples, then I will be able to better understand what's going on. Like, what gets rounded up? The file size themselves or the units of the find command, i.e. "find ~/Pictures -type f -name "*jpg" -size **-1G**"?

Suppose I typed:

```

find ~/Pictures -type f -name "*jpg" -size -2M

```

Would -2M be rounded up to -1M, and if so, would files with a size of 500,000 bytes end up in the final output? How about files of 1,500,000 bytes, or 1.5MB?

---

### Post by TheFu on 2017-08-02
Think I get it.  The modifier specifies a resolution, significant digits, if you will.

By specifying '1G', we've asked for 1G to be the base using of grouping.  Using a smaller unit would provide a smaller base unit for grouping.  That is why 1000M is NOT the same as 1G.  If we need byte level accuracy, then use a byte size parameter.  If 1 Kb is sufficient resolution, use that. If 1 Mb is needed, use that.  

We can test all of this by creating a few files of specific different sizes (use dd) and trying a few 'find' commands.

I tend to be looking for larger files, not smaller files - so files larger than 1G would work as expected.

---

### Post by vocx on 2017-08-02
> **John_Patrick_Mason said:**
> Quick question. If the file size is always rounded up before getting processed by find, doesn't that mean that a file with a size of 10458576 bytes should get rounded up to *2M*B instead of 1MB??? I thought 1MB was equal to 1,000,000 bytes?
I just wanted to explain this bit because it's interesting.

In international scientific notation, mega means "one million", so 1 megabyte, means 1 million bytes, 1 000 000.
And also, 1 kilobyte is "one thousand", and 1 gigabyte is "one thousand million" (one milliard).
The standard prefixes use the base 10. So, kilo 10^3, mega 10^6, and giga 10^9.

However, in computer notation, the terms acquired a different meaning.

Because of binary mathematics, where the base is 2, a common quantity is 2^10 = 1024. This became known as a "kilo" in computing environments.
Similarly, a mega is 2^20 = 1024^2 = (1024)x(1024) = 1 048 576.
And a giga is 2^30 = 1024^3 = (1024)x(1024)x(1024) = 1 073 741 824.

As you can see, the first numbers (base 10) are approximately the same as the latter ones (base 1024), but are not exactly the same.

Scientists decided to call the binary prefixes "kibi-", "mebi-", "gibi-", "tebi-", etc. instead of "kilo-", "mega-", "giga-", "tera-". Nevertheless, currently the names "kilo", "mega", "giga", "tera", etc. are still widely used in computer terminology and marketing. They have the base 10 name, but actually refer to base 2 multipliers. It is confusing for the uninitiated.
[https://en.wikipedia.org/wiki/Mebibyte](https://en.wikipedia.org/wiki/Mebibyte)

As for what exactly "find" does with the "-size" option, I'm not sure, I would have to test different files. It seems to be a resolution, that is, the minimum quantity that can be counted. So, a file that is 1.5 MB is not counted with size -2M, because it's not 0 MB. I guess it is rounded to 2 MB, and then not considered less than 2 MB. I'm not sure, but something along those lines. Basically, if you want to count both big and small files, you should use a small resolution, and big numbers, like -size -1000000K. This would count files with kilobyte (kibibyte) precision, and would search for those that are less than one million KB, so less than 1 GB.

---

### Post by 1clue on 2017-08-02
Removed content

---

### Post by sisco311 on 2017-08-02
> **steeldriver said:**
> I agree it's confusing

The key to understanding it is this extract from the man page:

```

              The  +  and  -  prefixes  signify greater than and less than, as
              usual.  [COLOR=#000000]**Bear in mind that the size is rounded  up  to  the  next**[/COLOR]
              [COLOR=#ff0000]**unit.**[/COLOR]  Therefore -size -1M is not equivalent to -size -1048576c.
              [B]The former only matches empty files, the  latter  matches  files
              from 1 to 1,048,575 bytes[/B].

```

So, any file occupying less than 1048576 bytes is rounded up to 1M - and is therefore not less than 'size 1M' (but **is** less than 5M) - same applies to the G multiplier

Thank you, steeldriver!

Took me 20 minutes and now I understand it.

It's counter-intuitive but the rule is clearly sated in the man page.

---

### Post by John_Patrick_Mason on 2017-08-02
I think I got the gist of it. The only time I found it not to work is if I type:

```

find ~/Pictures -type f -name "*jpg" -size +0M

```

in which case the find command just ignores the -size portion.

I also think I might have found a mistake inside the man page. If I type:

```

cd ~/Documents

```

which contains the following hypothetical text files:

```

ls -l
-rw-rw-r-- 1 mason mason 56K Aug  2 21:10 file1.txt
-rw-rw-r-- 1 mason mason 230K Aug  2 21:10 file2.txt
-rw-rw-r-- 1 mason mason 1.7M  2 21:10 file3.txt
-rw-rw-r-- 1 mason mason 468K  2 21:10 file4.txt
-rw-rw-r-- 1 mason mason 25K  2 21:10 file5.txt

```

and then do:

```

touch file6.txt

```

and finally:

```

find ~/Documents -type f -name "*txt" -size -1048576c

```

find will print not only files 1,2,4, and 5, but also file6.txt, which has a size of 0 bytes. The man page states that when using the "-size -1048576c" option, the find command will search for files that are between 1 and 1048575 bytes, but this can't be right since file6.txt also ends up in the output.

---

### Post by 1clue on 2017-08-03
The '-' in front of your size is the same as "less than."
A '+' in front of your size is the same as "greater than."
Using neither + nor - means that the rounded-off size of the file is equal to what you specify.

---

### Post by John_Patrick_Mason on 2017-08-03
I think I get it. The thing to keep in mind is that whenever the -size test is used, the specified size is rounded up by **one**.

Therefore, in my hypothetical directory, if I type:

```

cd ~/Downloads
ls -lh
total 1.5G
-rw-rw-r-- 1 mason mason 1.4M Aug  3 20:23 family_picture.jpg
-rw-r--r-- 1 mason mason 1.3M Mar 10  2013 PC-Building-Night-School.pdf
-rw-rw-r-- 1 mason mason 2.2M Mar 18 16:29 The Linux Command Line.pdf
-rw-rw-r-- 1 mason mason 1.5G Mar 19 22:22 ubuntu-16.04.2-desktop-amd64.iso
-rw-rw-r-- 1 mason mason 547K Aug  3 20:31 volcano.jpg

```

and then:

```

find ~/Downloads -type f -size +1M

```

find will search for files that are **equal to or greater** than 2MB. Since all **decimal** file sizes made visible by the "ls -lh" command get rounded up first, instead of working with the file sizes above, find sees the following:

```

-rw-rw-r-- 1 mason mason **2M** Aug  3 20:23 family_picture.jpg
-rw-r--r-- 1 mason mason **2M** Mar 10  2013 PC-Building-Night-School.pdf
-rw-rw-r-- 1 mason mason **3M** Mar 18 16:29 The Linux Command Line.pdf
-rw-rw-r-- 1 mason mason **2G** Mar 19 22:22 ubuntu-16.04.2-desktop-amd64.iso
-rw-rw-r-- 1 mason mason 547K Aug  3 20:31 volcano.jpg

```

and will therefore print:

```

/home/mason/Downloads/family_picture.jpg
/home/mason/Downloads/ubuntu-16.04.2-desktop-amd64.iso
/home/mason/Downloads/PC-Building-Night-School.pdf
/home/mason/Downloads/The Linux Command Line.pdf

```

Conversely, if one had typed the following instead:

```

find ~/Downloads -type f -size -2M

```

find would search for all files **less than or equal to** 1MB. Since all decimal file sizes still get rounded up when using the "ls -lh" command (before the find command is applied) find will only print one file:

```

/home/mason/Downloads/volcano.jpg

```

If I can get a confirmation on the above, I'll mark this thread as solved.

---

### Post by 1clue on 2017-08-04
No.

The -1M is <= 1M, and +M is >= 1M. The size you specify is what find is looking for. The file size that is matched for each file is rounded up to the nearest unit. Meaning any file which is exactly 1M is left at 1M, but if something is 0.5M it shows up as though it were 1M.

The search spec is not rounded up, the file size of each file is.

If you use **-size 2M** then vocano.jpg will not match because it's rounded to up to 1M.  However the first two in your list will match.  The third item won't because it will be rounded up to 3M.

If you use **-size 1G** then everything except the ubuntu image will match.

---

### Post by John_Patrick_Mason on 2017-08-04
OK, that makes much more sense. Only the file sizes themselves get rounded up, not the units of the -size option.

So,
```

find ~/Downloads -type f -size -1M

```

will search for files less than 1MB **after** they've been rounded up.

Similarly,

```

find ~/Downloads -type f -size -2M

```

will search for files less than 2MB, again, after they've been rounded up.

On the other hand,

```

find ~/Downloads -type f -size +1M

```

will search for files greater than 1MB after rounding up.

I think the thing that originally got me confused was which files get rounded up. At first -- to use the example above -- I thought a 547KB file would get rounded up to a 600KB file, not a 1MB file. Now I know that's not the case. I'm assuming a file as small as a 1KB file would still get rounded up to a 1MB file, correct?

It's counter-intuitive because if I type:

```

find ~/Downloads -type f -size -1M

```

the find command will ignore a file with a size of 300KB because find sees that file as being 1MB, and since we specifically asked for files that are less than 1MB, the 300KB file doesn't actually end up in the output.

---

### Post by 1clue on 2017-08-06
Or, using neither - nor + in the size spec,

```
find ~/Downloads -type f -size 1024c
```

Will find files in the ~/Downloads directory which are exactly 1024 bytes in size.

```
find ~/Downloads -type f -size 1k
```

will find non-empty files in the ~/Downloads directory which are between 1 and 1024 bytes.

```
find ~/Downloads -type f -size 2k
```

will find files in ~Downloads which are between 1025 and 2048 bytes.

```
find ~/Downloads -type f -size 1M
```

will find non-empty files in the ~/Downloads directory which are between 1 and 1048576 bytes.

```
find ~/Downloads -type f -size 2M
```

will find files in ~Downloads which are between 1048577 and 2098152 bytes.

---

