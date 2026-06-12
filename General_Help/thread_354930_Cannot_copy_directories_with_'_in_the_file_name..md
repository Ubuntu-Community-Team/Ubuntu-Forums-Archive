---
title: "Cannot copy directories with ' in the file name."
date: 2007-02-06
forum: General Help
---

### Post by djpm05 on 2007-02-06
I am having a problem trying to copy a directory called "Audio CD's" from terminal

I am typing cp -R -v Audio\ CD's /backup
and I get a carrot instead.
>

apparently the apostrophe will put the computer into that mode, and I've tried from my mac, my ubuntu desktop, etc.

it is on an NTFS file partition I am trying to get data off of so I can format it ext3.

I have been searching on google for about 3 hours, and hadn't gotten anywhere.

Thanks in Advance. :)

---

### Post by mcduck on 2007-02-06
Try this: cp -R -v Audio\ CD\'s /backup

---

### Post by djpm05 on 2007-02-06
> **mcduck said:**
> Try this: cp -R -v Audio\ CD\'s /backup


That works, thank you :) 

also, I saw your ninja edit. [IMG]http://obsidianrecordings.com/random/shifty.gif[/IMG]

---

### Post by mcduck on 2007-02-06
yup. I managed to post it before I realized that it's not going to work in this case :D

---

### Post by meng on 2007-02-06
djpm:
Does tab-autocomplete work for you? That is to say, if you type:
cp -R -v Audio
and then press TAB, will the full pathname (with escape characters, that's the \' part) appear?

---

### Post by djpm05 on 2007-02-06
> **meng said:**
> djpm:
Does tab-autocomplete work for you? That is to say, if you type:
cp -R -v Audio
and then press TAB, will the full pathname (with escape characters, that's the \' part) appear?

WOW I never knew about that!

Thank you for the advice, I will be using that a lot more.

---

### Post by meng on 2007-02-06
Yep it's a real epiphany when you learn about that. ;)

---

### Post by djpm05 on 2007-02-06
> **meng said:**
> Yep it's a real epiphany when you learn about that. ;)

What's sad is I've had my debian server for over a year, and my openBSD router for 6 months, and I'm just now learning this.

---

### Post by bodhi.zazen on 2007-02-06
Tab completion ... not just for files

works for commands as well :p

---

