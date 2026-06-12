---
title: "gFTP Filespec filtering"
date: 2006-11-23
forum: General Help
---

### Post by zackr on 2006-11-23
I run Quanta+ and other programs which generate a lot of 'backup' files which they signify by appending a tilde (~) on the end of the file name.

When I go to upload with gFTP it lists all those files, and it would really be helpful if I could change Filespec (Go to the  Local > Change Filespec) to filter out these unnecessary files.

I tried putting *~ in there, but of course that just shows all the tilde files, so I would like to know how to 'reverse' this. (Tried !*~ but it didn't work).

Since I use mainly .php files, I tried that, but I couldn't view any directories :(

Help would be much appreciated! I've done reg. exp. before but this seems to use a slightly different style...

---

### Post by thingy on 2006-11-23
Hi
 
Can you try this as the filespec:
 
> '*[!~]'
 
Note the ' <-- I'm hoping that this means that the filerspec won't expand the ~ to your home dir. If it does, then can you try this:
 
*[!\~]

---

### Post by zackr on 2006-11-23
Thanks for that, but no, they don't work (no files or directories appear).

What are these 'rules' called and is there a list of identifiers much like regular expressions somewhere?

---

