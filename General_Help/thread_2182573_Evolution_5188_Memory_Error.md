---
title: "Evolution 5188 Memory Error"
date: 2013-10-21
forum: General Help
---

### Post by c14pialpha3 on 2013-10-21
Hello Everyone,

I have been using Ubuntu as my primary OS for 1 year now :)
I am running Ubuntu 13.04 with Cinnamon 2.0.

I like to use Evolution 3.6.4  as my mail client for gmail (as I dont like Thunderbird), however it keeps crashing on my randomly.
I have tried re-installing it, I have also tried manually installing the latest version from their website (but that caused many problems and I had to re-image my machine).
Today I tried running Evolution from terminal to see if i could get any errors listed, and aside from the few complaining about GTK themes I saw this error:

***MEMORY-ERROR***: evolution[5188]: GSlice: assertion failed: sinfo->n_allocated > 0
Aborted (core dumped)

Does anyone know how I can fix this?
Or even does anyone know of another email client similar to Evolution, which has IMAP and Calendar support for Gmail, which isnt Thunderbird, is not terminal based, and isnt simply a watcher which opens the gmail website?

Thanks in advance,

Sirik

---

### Post by neltnerb on 2013-11-11
I am seeing this same error using Ubuntu 13.10 (standard) using Evolution 3.8.4. It's been crashing for months. I ran it with gdb finally (didn't know what to do until today), and it gives:

> ***MEMORY-ERROR***: evolution[19174]: GSlice: assertion failed: sinfo->n_allocated > 0

I'm afraid I have no ideas what it could be, I've been trying to fix this since 13.04 though, and it's definitely still an issue in 13.10. I just see random crashes continually, with perhaps 5-10 minutes between them. I am constantly losing draft emails, and it's extremely frustrating. But I also agree with you that Thunderbird is even worse than Evolution while it is constantly crashing... :(

---

