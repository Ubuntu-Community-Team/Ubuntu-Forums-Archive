---
title: "Terminal command not matching man entry"
date: 2019-03-29
forum: General Help
---

### Post by freebird54 on 2019-03-29
I have run into something rather strange lately. There is a simple (!) terminal command named **cal** for displaying a calendar, and it no longer matches its man page entry. In particular, I redirect its output to a file for some sed processing, and wish to eliminate the 'highlight' placed on the current date (it messes up the sed). The man page claims that **cal -h** will suppress the highlight (as it used to) and all should be fine, but the version on my new install of 18.04 merely exits with usage info. Checking the output file shows the highlight still embedded, so now what? Can I find an OLD version of cal without jumping through too many hoops?

Amazing what comes up sometimes...

Freebird

---

### Post by The Cog on 2019-03-29
Interesting. On 16.04, **cal -h** works fine. Also, **cal** does highlighting, but **cal | hd** (or piping cal to anything, i.e. not to a tty) does underscore followed by backspace to do its highlighting. But I don't have access to an 18.04 to try right now.

But...
On a recent Red Hat linux, cal treats -h as --help. However, piping cal through anything else (e.g. **cal | hexdump -C** or even just **cal | cat**) turns the highlighting off.

---

### Post by freebird54 on 2019-03-29
Very strange.  However, I tried a couple of things for information. Yes, it still works fine on 16.04. It is listed in /usr/bin/ as cal -> ncal - both of them dated Mar 1 2016. ncal is 29840 in size.  On my 18.04, /usr/bin shows cal -> ncal still, but the date for the cal entry is Mar 20 (no year) and ncal is Jan 17 2018 (new size 29480). So who/where do I ask to see if I just substitute the older ncal for the newer one? Too simple? :)

Or, do I have to learn enough sed to filter out the excess bytes (and underlines) from the output of the new one? Great minds (and I) wish to know...

freebird

---

### Post by ajgreeny on 2019-03-29
Interestingly, on my 18.04, **cal** is failing like yours, but **ncal** seems to work fine for the simple commands such as **ncal -h** and **ncal -e**.

As in RHL according to The Cog, **cal -h** also treats the command as a simple help request in 18.04; no idea about 16.04 as I don't have that version to try.

---

### Post by Impavidus on 2019-03-29
cal is a symlink pointing to ncal. When ncal is called as cal, it switches to cal mode, just as when it's called with the -C option. In this mode, -h gives a help message (which is more or less a standard for the -h option).

ncal disables the highlight when called with -h, but changes the output format to put each week in a column instead of a row. The -b option changes the output format back to the weeks in rows, but keeps monday as the first day of the week (at least in my locale). The -S option fixes that. So the command you want to use is```
ncal -bhS
```
Unfortunately, the man page is for both commands at the same time, but doesn't clearly describe the differences between both modes of the program.

---

### Post by freebird54 on 2019-03-29
Ahh - so there is SOME sense to the results I  get! Why it changed, however....

Anyway - I will try your solution right after I undo the backdoor replacement of ncal with the one from 16.04 ;). Either way, I guess the problem is solved, as my old conky now includes a legible calendar again.  Thanks to all.

Freebird

---

### Post by freebird54 on 2019-03-29
Just a quick note - the alternative command (**ncal -bhS**) produces output identical to the original **cal -h** command, according to hexedit. It works fine as a substitute on my .conkyrc as well. 

So - if I could remember how to mark it SOLVED I would!

freebird

---

### Post by ajgreeny on 2019-03-29
You can mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. 

It is a great help to users searching the forum who come across this same behaviour..

---

