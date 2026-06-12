---
title: "How do I determine what options were compiled with?"
date: 2008-01-18
forum: General Help
---

### Post by aephex on 2008-01-18
I'm having a problem with streaming media. I'm using Mediatomb and I have a hunch (process of elimination) that it wasn't compiled with the proper options enabled.

I figure I might as well learn in the process.
So, I would like to know how to determine what options Mediatomb (and any given program) was compiled with.

---

### Post by jeffus_il on 2008-01-18
If it is stored anywhere it will be in the package itself. If you have a good hunch, download it and build it. I'll see if I can find something, Bye for now.

---

### Post by jeffus_il on 2008-01-18
Must try to download a source package and see what info is there.

---

### Post by aephex on 2008-01-19
I think I am going to just grab the source and build it making sure all the options I need are enabled.

I'd still like to know how I can check these things without rebuilding. I thought there might be a specific file I could do a regex search through, or something.

---

### Post by jeffus_il on 2008-01-19
When you download the source package have a look in it to see if there are any default values in in text file ... Post it here if you find something.

---

### Post by jeffus_il on 2008-01-19
Seems that there is some info in a Debian source package, try a file debian/rules.
See this thread
[http://ubuntuforums.org/showthread.php?t=142376](http://ubuntuforums.org/showthread.php?t=142376)

---

### Post by aephex on 2008-01-19
> **jeffus_il said:**
> Seems that there is some info in a Debian source package, try a file debian/rules.
See this thread
[http://ubuntuforums.org/showthread.php?t=142376](http://ubuntuforums.org/showthread.php?t=142376)

This thread provided some extra info, and gave me an idea of where to look in the source.
I was hoping I could avoid having to rely on grabbing the source (not that it's a big deal, just ideal in my mind).  Thanks for all the support.

I'll post later with Mediatomb specifics once I look through the package.

---

