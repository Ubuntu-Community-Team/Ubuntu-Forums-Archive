---
title: "Pan Aborted (core dumped)"
date: 2007-05-12
forum: General Help
---

### Post by sobepmp on 2007-05-12
Pan was working fine for months.  Now this morning its not loading.  I tried to start it up in a terminal and got this "pan: fptools.c:458: _FP_fgets: Assertion `*buf' failed.
Aborted (core dumped)
user@user-desktop:~$ "  I tried googling for a solution but couldn't find one so I thought I'd ask here.

---

### Post by sekcon on 2007-05-15
hey guys, this just happend to me. only had pan insalled for about a week with minimal usage. all of a suden it wouldent open anymore. tried to reinstall which was no help.. anyone have a solution at all? :confused:

---

### Post by sekcon on 2007-05-15
ok.. to fix it delete the file tasks.nzb which is in the .pan2 folder in your home directory. hope this helps someone.

---

### Post by sobepmp on 2007-05-16
> **sekcon said:**
> ok.. to fix it delete the file tasks.nzb which is in the .pan2 folder in your home directory. hope this helps someone.

I deleted that file and Pan now loads but it doesn't work.  I can't download new headers or anything.  I tried reinstalling Pan but it wont download a list of newsgroups.

---

### Post by apfejes on 2007-05-17
I had the same error, and I didn't want to spend the time to figure out what was causing it.  As a brutal remedy, simply deleting the config files for pan works well enough. Of course, you'll be starting from scratch with your pan config.

> 
cd ~
rm -rf .pan/
rm -rf .pan2/

---

### Post by stonerfish on 2007-05-30
I deleted the folder article-cache and it worked fine.  But I had some tasks running when it crashed, and it started them up again.   After a minute it crashed again.  So after a couple of rm -rf article-cache; pan repetitions I noticed it was stopping at the same task each time.  I deleted the task and it seemed to work fine after that.
I was doing a bulk download of my unread messages in the alt.binaries.pictures.grotesque.  The subject name was "some sweet looking girls'.  Could it be a bomb in wmv file?

stonerfish

---

### Post by gpeck157 on 2007-06-08
> **sobepmp said:**
> Pan was working fine for months.  Now this morning its not loading.  I tried to start it up in a terminal and got this "pan: fptools.c:458: _FP_fgets: Assertion `*buf' failed.
Aborted (core dumped)
user@user-desktop:~$ "  I tried googling for a solution but couldn't find one so I thought I'd ask here.

After uninstalling pan, ```
sudo aptitude purge pan
``` I removed the folder .pan2 then installed Pan again, and now everything is working again. Yeah I had to start from scratch but at least it's working.

---

### Post by ikester8 on 2007-08-14
> **sekcon said:**
> ok.. to fix it delete the file tasks.nzb which is in the .pan2 folder in your home directory. hope this helps someone.

This worked for me. Thank you, I did not want to set up the newsserver again.

---

### Post by ricardisimo on 2007-09-29
Mine looks slightly different:
```
~$ pan
pan: parts.cc:244: void pan::Parts::set_parts(const pan::PartBatch&): Assertion `pch == part_mid_buf + part_mid_buf_len' failed.
Aborted (core dumped)
```
Deleting tasks.nzb appears to have done the trick. The second time around I bypassed a duplicate partial, or broken, post, and only selected the completed posts. Like I said, so far so good.

---

### Post by ricardisimo on 2007-09-29
I take it back... it wasn't a dupe posting, just a very similarly named file. So, I have absolutely no idea why the file was a problem, if it was after all.

---

### Post by chkno on 2007-11-11
When I got this error, I found this in my ~/.pan2/tasks.nzb:
```
<file ...>
  ...
  <segments>
    <segment ... number="3">...</segment>
    <segment ... number="4">...</segment>
    <segment ... number="5">...</segment>
    <segment ... number="6">...</segment>
    <segment ... number="7">...</segment>
  </segments>
</file>
```

That is, this one <file> entry did not have a segment numbered 1 or 2.  I removed this one <file> node from tasks.nzb (with vim) and pan was then able to start normally.

You can use GDB to help you find which file is causing the problem.  Run pan in gdb, wait for the assert, view a backtrace ("bt"), jump to the end_element() frame (eg: "frame 4"), and "print context->iter".  This will show you the the part of your tasks.nzb immediately *after* the problem node.

---

### Post by Franko30 on 2008-05-27
Hi,

my failure message was:

```
pan: parts.cc:244: void pan::Parts::set_parts(const pan::PartBatch&): Assertion `pch == part_mid_buf + part_mid_buf_len' failed.
```

It happened twice, so now I can recreate the procedures:

I was downloading huge queues of files. Then I had to restart Ubuntu due to updates.

Stopped all the queues, ended pan, moved all the complete files (in different directories) my network attached storage, restarted Ubuntu und when starting pan I get this error message.

I guess there are some errors with directories pan expects to be there. Maybe working with subdirectories for different downloads isn't such a good idea...

I'll try to edit all the file-download-paths in tasks.nzb to an existing default directory and then report back.

Cheers

Franko30

---

### Post by Franko30 on 2008-05-27
Hi again,

I edited the tasks.nzb to contain only a few downloads that point to existing paths and pan worked fine again!

[B]My conclusion:
[/B]
pan seems to have problems when directories specified in the tasks.nzb suddenly don't exist anymore. It could just "recreate" these directories, but obviously it doesn't and hence the error...

**Solution:**

Delete different download directories only after all tasks are done - or work only with one download directory (i.e. "pan-downloads") for all the files and sort them later.

Cheers

Franko30

---

