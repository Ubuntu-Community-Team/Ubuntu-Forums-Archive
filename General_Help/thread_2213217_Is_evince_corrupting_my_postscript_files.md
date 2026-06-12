---
title: "Is evince corrupting my postscript files?"
date: 2014-03-25
forum: General Help
---

### Post by ralph-beeby on 2014-03-25
I ignored this one as an occasional nuisance, but it seems to be happening more frequently, so I thought I'd see whether anyone else has encountered a similar problem. In a nutshell, I'm playing around with some data in IDL, and plotting the results out to postscript files. Depending on what I'm looking at, this often results in multiple-page .ps files, and I *think* I only encounter the problem with these. 

I use evince to view the plots, and every so often it will freeze and throw up the standard "Ubuntu has experienced an internal error" message. Once it's done this, I get a segfault / core dumped message every time I try to view that file subsequently. Of course, if I re-run the program and generate the .ps again, it usually works fine. It's just a bit of a nuisance, and I wonder whether anyone could guess what might be causing it?

---

### Post by frankmorris2 on 2014-03-25
Hello,

I do not use evince, but I assume this is only a reader/viewer program.

First, I would recommend a quick check of the ps files before and after the use of the viewer.

Get the MD5 sum before running the viewer on the original file
```

md5sum -b file1.ps

```

Run the viewer.

Get the MD5 again to see if file1.ps was altered. If the checksums are different, the viewer did modify the file.

After that, you could search the internet with the complete error message from the viewer.

Have a nice day

---

### Post by Impavidus on 2014-03-25
Or make a backup and check what was changed. But I think evince shouldn't change the file.

Maybe (speculating here) evince creates a cache of the file (in raster format). When evince crashes the cache is broken, when it tries to reload it reuses the cache and crashes again. I think evince discards the cache when it sees the PS file is newer than the cache, which happens when you regenerate the PS file. Or delete the cache (I've got no idea where it would be stored) or change the timestamp on the PS file with **touch**.

I found that evince often has difficulty with not very well structured but still standards conforming PostScript files. **gv** seems to do a better job. For example on a 1kiB table with all 24 bit colours (32768 pages), which evince seems unable to open.

---

### Post by ralph-beeby on 2014-03-26
> **frankmorris2 said:**
> Hello,
I do not use evince, but I assume this is only a reader/viewer program.

> **Impavidus said:**
> Or make a backup and check what was changed. But I think evince shouldn't change the file.

I found that evince often has difficulty with not very well structured but still standards conforming PostScript files. **gv** seems to do a better job. For example on a 1kiB table with all 24 bit colours (32768 pages), which evince seems unable to open.

Thank you both. You're quite right, frank, evince is just a viewer, a bit like Eye of Gnome but for postscripts and pdfs. The md5sum showed no difference before and after so it doesn't look like it's changing the file.

Impavidus: this wouldn't surprise me, as I've had problems in the past with IDL - I think it was a language designed for Windows and later ported to Linux, and does cause strange hiccoughs occasionally. (I would have abandoned it long ago if my group weren't still using it for a lot of things!) I can imagine that its .ps output might contain something that evince doesn't like - though gv seems to cope with the job perfectly, so thank you for the recommendation!

---

### Post by Impavidus on 2014-03-26
Great.

Could you mark the thread as solved? Click thread tools &#8594; mark as solved, above the first post.

---

### Post by ralph-beeby on 2014-03-28
Ah yes, of course - sorry, still learning the rules round here!

---

