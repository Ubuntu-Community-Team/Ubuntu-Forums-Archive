---
title: "Thunderbird and Evolution Email Size"
date: 2006-10-12
forum: General Help
---

### Post by wizzkid on 2006-10-12
Hi! 

I installed both thunderbird and evolution. I sync them on my IMAP server. I noticed that evolution take little space then thunderbird.

Thunderbird = 962MB
Evolution = 231MB

is this normal? i was shocked the difference.

---

### Post by wizzkid on 2006-10-13
any comment here?

---

### Post by gvgerman on 2006-10-13
In the past, I have had problems w/ Tbird and the local folders being unusually large.  In my situation, I had many sub-folders in the local folders and some of the sizes of these sub-folders were unreasonably large vs. the number of messages in the sub-folder and the content and format of these messages.

As I recall, I believe the solution was to delete the files with the .msf extension associated with the problem sub-folders.  These files reside in the profile folder; do some drill-down.  The data remains untouched (it resides in the same-named file without the .msf extension).  When you reload Tbird, it "resets" (in layman's terms) and the "phantom" bytes that were inflating the sub-folder file size went away.  This also made Tbird run much faster for me.  In my case, the file size errors were several megabytes and this fixed the issue completely.

If your file sizes are approximately the same, I'd not worry about it as long as everything works.  If your file sizes are different by a large amount, then you may have a corrupt *.msf file.

Caution - You should do some Googling to make sure this instruction is appropriate. Some time has passed since I did this and I'm writing this from memory, not so much from an "expert" position.  I searched the Mozilla site at the time and found easy-to-follow instructions to resolve my Tbird mail file corruption issues.

For what it is worth, I find Evolution is generally faster than Tbird and have settled on using it.

---

