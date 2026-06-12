---
title: "Making a copy of all files (including subdirectories)..."
date: 2013-09-15
forum: General Help
---

### Post by tharpa on 2013-09-15
Not sure if this is the right forum for this question ....  I would like to write a command to copy all of files in a directory and its subdirectories that have been modified in the last month. How do I do this?  I'd be just as happy (or happier) if there were a way to do this with a gui, but I think there is not.   (There is in Windows, but as far as I can tell not in Linux).

---

### Post by Vaphell on 2013-09-15
do you want them dropped into a single dir or maybe you need to preserve the dir structure?

---

### Post by tharpa on 2013-09-15
Yes, I would like to preserve the directory structure.

---

### Post by col48 on 2013-09-15
It looks to me like a combination of find, xarg and cp could do this.
find has an option -mtime -31 (the -31 means <31*24 hours ago) or -newer XXX where XXX is a file name

[B][COLOR=#FF8C00]Whatever you do, check this carefully yourself before trying it - I'm only basing this on documentation, not experience, so may easily have misunderstood something.
[/COLOR][/B]
Something like
find TOPDIRECTORY -mtime -31 -print0 > XXX |   cp -a XXX WHERETOCOPYTO
or (after the first time)
find TOPDIRECTORY -newer XXX -print0 > XXX |   cp -a XXX WHERETOCOPYTO

Maybe xargs could do the second stage more elegantly.

---

### Post by jamesisin on 2013-09-15
I would suggest using rsync in lieu of cp: better, faster, smarter.  Other than that, what col48 suggests is at least approximately correct.

---

### Post by Vaphell on 2013-09-18
too bad it's not immediately obvious how to do this with rsync with its crapload of params

i figured out something like this
```
cd /src
rsync -aR0v**n** --files-from=<( find . -mtime -30 -type f -print0 ) . /dest
```
n = dry run

---

### Post by col48 on 2013-09-19
Does it matter whether there is some overlap between one month and the next?

If not, then '-mtime 31' (every time) in find will cover the bases if this procedure is run on the same date each month.

If it does matter, my original suggestion (modified by using rsync, if you like) uses the option '-newer' in find to copy only the files modified since last time - whenever that was.  At critical periods it could be run weekly, daily or hourly without making any changes.  Just don't change the XXX file manually at any other time - and don't delete it!

---

### Post by jamesisin on 2013-09-19
I usually run rsync with -aiSP for my backups.

The argument v is for verbose and would be useful in conjunction with n for testing a dry run, as Vaphell suggests.

I'm not clear about 0.  Man says "-0, --from0  all *from/filter files are delimited by 0s" which is just about as useless a description as I could hope for.

What is the advantage in using -R (use relative path names)?

---

### Post by oldos2er on 2013-09-19
There's a GUI version of rsync called grsync, might be easier for the OP to use.

---

### Post by Vaphell on 2013-09-19
> **jamesisin said:**
> I usually run rsync with -aiSP for my backups.

The argument v is for verbose and would be useful in conjunction with n for testing a dry run, as Vaphell suggests.

I'm not clear about 0.  Man says "-0, --from0  all *from/filter files are delimited by 0s" which is just about as useless a description as I could hope for.

What is the advantage in using -R (use relative path names)?

frankly i slapped some switches together to see what sticks, -R might be useless

-0 means *rsync --from-files* expects null-delimited list, which is what it gets from *find **-print0***
Whenever in *cmd --help* you see something about 0/null and delimiter, this is what it's about.

null-delimited lists are the only rocksolid way to pass filename lists around. Newline is unsafe because you can create a file with \n in its name (eg *touch $'abc\ndef.txt'* )and you wouldn't be able to tell the difference between
```
[COLOR="#0000FF"]abc
def.txt[/COLOR]
```
and
```
[COLOR="#0000FF"]abc[/COLOR]
[COLOR="#006400"]def.txt[/COLOR]
```
Sure, it almost nobody uses such weird names but they can happen, if only by accident in some broken bash script.

In extN filesystems the only characters that can't be used in filenames are / (out of question, already taken, used to separate elements of the path) and null. That means only null is unambiguous when used as a delimiter and won't ever collide with the contents of the list.

---

### Post by jamesisin on 2013-09-19
Looks like maybe you could just use -z in find to get the same effect:

[http://stackoverflow.com/questions/6563979/linux-gnu-sort-how-to-use-null-0-as-delimiter](http://stackoverflow.com/questions/6563979/linux-gnu-sort-how-to-use-null-0-as-delimiter)

---

### Post by Vaphell on 2013-09-19
hm?
*find -print0* spits out null delimited list (or you can construct your own format with printf and use \0 there) but the command that takes it as input must know about it and use null as delimiter too, hence *sort -z*, *rsync -0*, *xargs -0*, etc.

---

### Post by tharpa on 2013-09-19
Thanks, Vaphell, that worked.  P.S. I would have used the Quote feature, but it didn't seem to work, at least not in the preview.  Similarly, Code tags didn't seem to work in my reply.    And the full text isn't showing up.    cd /src rsync -aR0vn --files-from=

---

### Post by jamesisin on 2013-09-20
Thanks, Vaphell.

---

