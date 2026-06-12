---
title: "Fonts"
date: 2008-05-06
forum: General Help
---

### Post by psychofish25 on 2008-05-06
I recently have had some trouble with fonts. 

When I type "gksudo nautilus" into terminal, I used to get an error saying mal-formed XML document in line 1 of ~/.fonts.conf. I went to that file and fixed that line, but then my firefox font changed to something weird. I thought the old font was Sans, so I downloaded Sans from a website, then noticed that it was slightly different from my old Ubuntu font. I was wondering if either someone could tell me what to do, ie how to go back and undo those changes, or simply upload the Sans font file for me.

Thanks,
Jordan

---

### Post by kerry_s on 2008-05-06
run this in terminal->
**sudo fc-cache -vf**

my bag, wrong 1. just delete or move .fonts.conf
mv ~/.fonts.conf ~/.fonts.conf.old

---

### Post by psychofish25 on 2008-05-07
excellent, thanks you

---

### Post by psychofish25 on 2008-05-07
Actually, I did that move last night and today my Ubuntu would crash every 5 minutes. I am running Ubuntu Hardy Heron 8.04 LTS and I think that fonts file was making it crash so violently. I unmv'd the file and now it is crash-free.

---

