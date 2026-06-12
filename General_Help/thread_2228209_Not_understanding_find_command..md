---
title: "Not understanding find command."
date: 2014-06-06
forum: General Help
---

### Post by NertSkull on 2014-06-06
I have a cronjob running every hour that does the following

```
01 * * * * /usr/bin/find /path/to/folder/ -type f -mtime +10 -exec rm '{}' \;
```

I thought that would delete every file older than 10 days in all the subfolders.  But, it appears that if the parent folder has a date less than 10 days (say two days ago), then the children in that folder (even if way older than 10 days) are not getting deleted.

Its like the parent folder stops it from checking inside if it doesn't match the date.  I don't see any sort of recursive forcing in the manual.  I thought it just checked the subfolders.

What am I doing wrong?

---

### Post by TheFu on 2014-06-06
No need for single-quotes is the only thing I'd do differently.
I haven't tested this, but I've **never** enclosed the replacement parms {} in any quotes the last 20+ yrs.

---

### Post by NertSkull on 2014-06-06
Interesting, I swear I read somewhere once to place them in quotes, in case you get special characters returned by the find command.

But, either way.  I tried without the quotes around {}.  And still no luck.  It still doesn't delete items older than 10 days within a folder younger than 10 days.

---

### Post by steeldriver on 2014-06-06
I would have expected it to work - unless there's something funny about the way cron handles the arguments (or the escaped \; perhaps?)

However with GNU find you could try replacing the '-exec rm '{}' \;' entirely with a '-delete'

```

01 * * * * /usr/bin/find /path/to/folder/ -type f -mtime +10 -delete

```

As noted in the man page, -delete turns on -depth i.e. it unambiguously does a depth-first traversal

```

       -delete
              Delete  files; true if removal succeeded.  If the removal failed, an
              error message is issued.  If -delete fails, find's exit status  will
              be nonzero (when it eventually exits).  [B]Use of -delete automatically
              turns on the -depth option.[/B]

```

---

### Post by TheFu on 2014-06-06
> **NertSkull said:**
> Interesting, I swear I read somewhere once to place them in quotes, in case you get special characters returned by the find command.

But, either way.  I tried without the quotes around {}.  And still no luck.  It still doesn't delete items older than 10 days within a folder younger than 10 days.

**Looks like I'm wrong!**

Now that I'm looking, I see lots of examples with the '{}' shown.  Guess I've just been careful about filenames all this time to avoid issues. ;)  Hard to believe, I've not been burned by this  or just solved it some other way.  I tend to use double-quotes, so variable expansions work. Mainly use single-quotes for sed scripts.

I got nothing to help besides studying the man page for which loophole this falls under.  Perhaps putting the entire thing into a script and calling that from cron?

---

### Post by steeldriver on 2014-06-06
@TheFu, it *says *that, but I think it's not an issue in modern shells e.g. here's it working in a dir containing both a filename with spaces and even one containing a newline:

```

$ find tests -mtime -1 -exec rm -i {} \;
rm: cannot remove `tests': Is a directory
rm: remove regular empty file `tests/file with spaces'? y
rm: remove regular empty file `tests/odd\nfile'? y
$ 
$ find tests -mtime -1
tests
```

---

### Post by varunendra on 2014-06-06
Just wanted to confirm (and join myself to the thread since it is interesting) that I just created a new directory on my Desktop, gave it a random name "**nf**", and moved into it a directory (wireless-info-samples) containing a bunch of months old files. Used the command -
```
find ./ -type f -mtime +10 -exec mv '{}' ./nf/ \;
```
Works perfectly, so should work with 'rm' as well.

Keen to see what is causing the issue to the OP.

---

### Post by steeldriver on 2014-06-06
... just wondering if the files are actually deletable - no funny extended attributes like append-only (chattr +a) on the parent dir?

---

### Post by papibe on 2014-06-06
Hi NertSkull.

I made some testing and even if a folder is newer, 'find' finds the older files.

My first guess is that there's at least one file that is triggering the an interactive/confirmation prompt. For instance:
```
rm: remove write-protected regular empty file &#8216;dummy&#8217;? 
```
which it is usually because of permissions. A simple 'rm -f' could solve that situation.

I would debug the command by first getting the list of files to be removed:
```
find /path/to/folder/ -type f -mtime +10 -print > /path/to/log
```
This could give us light if the problem is with 'find' or with 'rm'.

Just a thought. Let us know how it goes.
Regards.

---

### Post by NertSkull on 2014-06-06
Allright I think that I may be at fault here.  The parent folder date was a red herring it appears.  Having messed around with it, what appears to really be happening is its deleting things 11 days old (even though I'm saying 10).  I think.  For example Today is the 6th.  Its deleting things from 26th, which is 11 days ago.

I'm not sure, but I think it may have something to do with this.

[https://unix.stackexchange.com/questions/92346/why-does-find-mtime-1-only-return-files-older-than-2-days](https://unix.stackexchange.com/questions/92346/why-does-find-mtime-1-only-return-files-older-than-2-days)

I know that says centOS.  But that appears to be what is happening to me.  The parent data folder time just threw me because I happened to have different times on those folders for this date.  Sorry for that.

Anyone know if that post I linked to applies to ubuntu (kubuntu 12.04) as well?  Assuming it does, I think I've got this one solved.

---

### Post by papibe on 2014-06-06
> **NertSkull said:**
> Anyone know if that post I linked to applies to ubuntu (kubuntu 12.04) as well?
It certainly does.

Most Linux system use GNU tools which include 'find'. Although CentOS 5.9 is old, so it should be running a previous version than 12.04, the core concepts are the same.

With that in mind, you could do:
```
find /path/to/folder/ -type f \( -mtime 10 -or -mtime +10 \)
``` 
or just:
```
find /path/to/folder/ -type f -mtime +9
``` 
Regards.

---

### Post by NertSkull on 2014-07-24
Cool.  That helped get everything working.

Thanks all!

---

