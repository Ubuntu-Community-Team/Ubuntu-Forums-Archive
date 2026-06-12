---
title: "URGENT How to recover a replaced file"
date: 2007-11-13
forum: General Help
---

### Post by sk87 on 2007-11-13
Hi guys, help if you can please

I just replaced one file with an older version backup. This wouldn't of been so bad apart from the fact that the 3 backups that i made at the same were all corrupted by OOo. So now my good copy has been replaced by a corrupted one and all my backups are also corrupted.

i did some searching and found that i should do ls -al to see if an old version of it is still there, unfortunatley i do no understand the results.

:~/work/y2/CM0255$ ls -al
total 8
drwxr-xr-x 2 sam sam 4096 2007-11-13 22:16 .
drwxr-xr-x 6 sam sam 4096 2007-11-09 14:24 ..
-rwx------ 1 sam sam    0 2007-11-13 10:11 fibreoptics.doc

i think i replaced it at 22:16 so if i can recover it to any time before that would be great.

what do i do next?

many thanks

---

### Post by sk87 on 2007-11-13
Sorry to double post

but does the dates and times refer to any hidden backups that may of been created and how do I access them

---

### Post by RTrev on 2007-11-13
> **sk87 said:**
> Hi guys, help if you can please

I just replaced one file with an older version backup. This wouldn't of been so bad apart from the fact that the 3 backups that i made at the same were all corrupted by OOo. So now my good copy has been replaced by a corrupted one and all my backups are also corrupted.

i did some searching and found that i should do ls -al to see if an old version of it is still there, unfortunatley i do no understand the results.

:~/work/y2/CM0255$ ls -al
total 8
drwxr-xr-x 2 sam sam 4096 2007-11-13 22:16 .
drwxr-xr-x 6 sam sam 4096 2007-11-09 14:24 ..
-rwx------ 1 sam sam    0 2007-11-13 10:11 fibreoptics.doc

i think i replaced it at 22:16 so if i can recover it to any time before that would be great.

what do i do next?

many thanks

I don't know OO well at all, but I see that under Tools | Options | Paths there is a section saying where your backup files are stored.  perhaps you'll get lucky and find one in there?

Bob

---

### Post by sk87 on 2007-11-13
No that hasn't worked

Any other ideas?

---

### Post by RTrev on 2007-11-13
> **sk87 said:**
> No that hasn't worked

Any other ideas?

Well, I don't suppose you have the program open still?  Nah, that would be *too* lucky!  <g>

If you do, though, just copy/paste into another editor.

So, my understanding is that OO saved the file in a corrupted format?  Is it possible that it actually saved it in the wrong character set, or something of the sort?  If so, then perhaps trying to read the file with other editors and/or experimenting with the character set chosen might allow it to be read?

Is this a known bug in OO?  If so, perhaps chasing down the bug report might put you in contact with people who know why it happens and possibly how to recover it?

Sorry, running out of ideas.

Bob

---

### Post by sk87 on 2007-11-13
it shows as 0kb so theres nothing in it at all.

I'll look into the bugs but i think my time now is better spent redoing the essay


thanks for your help

---

### Post by RTrev on 2007-11-13
> **sk87 said:**
> it shows as 0kb so theres nothing in it at all.

I'll look into the bugs but i think my time now is better spent redoing the essay


thanks for your help

Bummer.  Bet you never forget to make backups again though.  :(

---

### Post by sk87 on 2007-11-13
thing is i had backups, just didn't realise they were corrupted

---

### Post by RTrev on 2007-11-13
> **sk87 said:**
> thing is i had backups, just didn't realise they were corrupted

All of your backups are zero bytes too?  This is called "Having a really bad day!"

---

### Post by sk87 on 2007-11-13
yeah, well i think the general rule is if something goes wrong it goes very wrong. In my experience of Linux, this is very true

---

### Post by Luna.jp on 2007-11-13
> **sk87 said:**
> yeah, well i think the general rule is if something goes wrong it goes very wrong. In my experience of Linux, this is very true

Its all about crossing your Ts **AND** dotting your I.

Whenever I am writing something important I frequently back it up, then check the back up.

Just another one of life's lessons.

---

