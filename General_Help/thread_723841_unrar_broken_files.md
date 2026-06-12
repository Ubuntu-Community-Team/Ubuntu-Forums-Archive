---
title: "unrar broken files?"
date: 2008-03-13
forum: General Help
---

### Post by heiNey on 2008-03-13
hi,

have a question regarding unrarring files that are broken...im trying to unrar a bunch of files and want it to keep the file even if it is broken...im using:

unrar e -kb file.part01.rar, 

but as soon as it tries to unrar the file that has the bad CRC, it just skips the rest.  it DOES keep the file up to the point where it reaches the bad file though.  what i want is for it to keep unrarring the entire thing, cuz the par files i have need the whole thing in order to recover...i know windows can do it...why cant ubuntu?

e.g.:

there are 20 x 50 meg files, with file 10 being corrupt.  the output im getting is a file that is 500 megs (10 x 50)

what i want is a file that is 1000 megs (20 x 50), and then i can run the par2 files to repair it.

btw, the par2 files were created to repair the file inside, instead of the rars...stupid i know, but cant do anything about it.

---

