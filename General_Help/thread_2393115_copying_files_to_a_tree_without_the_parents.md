---
title: "copying files to a tree without the parents"
date: 2018-05-29
forum: General Help
---

### Post by Skaperen on 2018-05-29
i am copying hundreds of files to a directory that for many of them subdirectories need to be added  (often more than one) as parents of the new file that do not exist.  the files need to get the same relative position in the destination tree.  there are many ways to deal with this.  one i found that seems to work well is to run two tar commands, one in the source tree, and the other in the destination tree, giving the file's relative path to the first tar (and options to create a tarball and output it to stdout), piping it to the second tar (with options to extract the tarball it reads from stdin.  normally i would just do a recursive cp from one tree to the other but i want to also filter out certain names.  for example:

```
find tree1 ! -type d -printf "%P\n"|grep "badfilename"|while read p;do (cd tree1;tar cf - "$p")|(cd tree2;tar xpf -);done
```

will copy from tree1 to tree2 without including anything named with "_badfilename_".

what ways would you recommend?

---

### Post by Holger_Gehrke on 2018-05-30
I do think rsync might be what you're actually looking for. It's not only for backups and network transfer, and its '--exclude' option should be just what you're looking for.

Holger

---

### Post by btindie on 2018-05-30
You're given command will only copy things with "badfilename" in the path. You need to use the '-v' to grep to get it to invert the match and filter out things.

Also, tar supports the '-C' option to change directory so the 'cd' commands are unnecessary. *tar* also supports an --exclude flag so the find command is probably also unnecessary. See *man tar* for more info.
```

tar -C /source/path --exclude '*~' -cf - . | tar -C /dest/path -xf -

```

But as mentioned previously, the easiest option would be to use *rsync* with either an exclude or filter rule. Plus with rsync, you can run it in *--dry-run* mode so you can what it'll do first without it making any changes.

---

### Post by SeijiSensei on 2018-05-30
tar also supports the --exclude-from directive; rsync takes a lot of its syntax from tar.  So you could use

```

cd /path/to/source
[s]tar cf - . | (cd /path/to/destination; tar --exclude-from=/path/to/exclude/file xf -)[/s]
```

with the exclude file consisting of the filenames or "globs" (e.g., "badfile*") to be excluded from the transfer.

Update: Syntax incorrect!  See below.

I used that tar+pipe method for many years, but now use rsync exclusively.

---

### Post by Skaperen on 2018-05-30
my bad about failing to use _-v_.  i do know about it; really.  but it is a "*typo*" i have made a few times.  maybe if i make a script named "_vgrep_" my internal thinking can work better about that.

i learned something new about _tar_ today, yay!

---

### Post by Holger_Gehrke on 2018-05-31
@SeijiSensei: Am I missing something or should the --exclude-from option go on the first 'tar' ? The way you've written the command, it would read all files and not write the ones that fit one of the patterns in the exclusion list. This would at best be a waste of time or make the whole thing fail if used to copy data off a failing -- but not yet failed -- drive if the exclusion list contained files known to have read errors ...

Holger

---

### Post by SeijiSensei on 2018-05-31
Yes, thank you.  The exclusion should apply to the first tar so those files are excluded as they are encountered.  As I say, I haven't used this method for some time, and obviously wasn't thinking clearly when I posted.

The correct command should be 
```

cd /path/to/source
tar --exclude-from=/path/to/exclude/file cf - . | (cd /path/to/destination; tar xf -)

```

Using rsync this distinction never arises.

---

