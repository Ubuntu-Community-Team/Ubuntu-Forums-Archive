---
title: "How to rotate PDF on command"
date: 2017-06-24
forum: General Help
---

### Post by satimis on 2017-06-24
Hi all,

Ubuntu 16.04

Please advise how to rotate PDF to certain deg (not exactly 90, 180, 270 etc) with command?

I have PDFtk running here.  Also I found following documents online;
1)
Manual pdftk
[http://manpages.ubuntu.com/manpages/xenial/en/man1/pdftk.1.html](http://manpages.ubuntu.com/manpages/xenial/en/man1/pdftk.1.html)```

Each option sets the page rotation as follows (in degrees):
                 north: 0, east: 90, south: 180, west: 270, left: -90, right:
                 +90, down: +180. left, right, and down make relative
                 adjustments to a page's rotation.

```

2)
Rotate PDF file
[https://askubuntu.com/questions/409880/how-to-save-a-rotated-pdf-file](https://askubuntu.com/questions/409880/how-to-save-a-rotated-pdf-file)```

pdftk   input.pdf cat 1-endsouth output output.pdf
# ^^^^^   ^^^^^^^^^ ^^^ ^^^^^^^^^^ ^^^^^^ ^^^^^^^^^^
#        input file     range  |          output file
# command                    direction

```

but couldn't resolve.  Please help.

Thanks

Regards
satimis

---

### Post by The Cog on 2017-06-24
As far as I can tell from the pdftk manual, it can only rotate by right-angles. You could try opening the pdf in LibreOffice Draw and using the rotate option there, then re-exporting to PDF.

---

### Post by satimis on 2017-06-24
> **The Cog said:**
> As far as I can tell from the pdftk manual, it can only rotate by right-angles. You could try opening the pdf in LibreOffice Draw and using the rotate option there, then re-exporting to PDF.
Hi,

Thanks for your advice. I got it done on LibreOffice Draw

Do you know where can I find example to set transparent background with pdftk?

On;
[http://manpages.ubuntu.com/manpages/xenial/man1/pdftk.1.html](http://manpages.ubuntu.com/manpages/xenial/man1/pdftk.1.html)```

If the input PDF does not have a transparent background (such
                 as a PDF created from page scans) then the resulting
                 background won't be visible - use the stamp operation
                 instead.

```

It said possible.

Regards
satimis

---

### Post by vasa1 on 2017-06-24
> **satimis said:**
> Hi,

Thanks for your advice. I got it done on LibreOffice Draw

Do you know where can I find example to set transparent background with pdftk?

...
[LIST]
[*]Please mark this thread [SOLVED] as shown here: [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)
[*]Please ask the transparent background question in a separate thread with an appropriate title so that the question and answer will be visible to people interested in that aspect.
[/LIST]

Thanks!

---

