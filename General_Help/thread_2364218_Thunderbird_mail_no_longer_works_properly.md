---
title: "Thunderbird mail no longer works properly"
date: 2017-06-20
forum: General Help
---

### Post by bask185 on 2017-06-20
I connected my work's exchange acount to my Thunderbird Mail but it no longer shows me new e-mails and it does not show the ones I send leave. 

I removed/reinstalled TB but it does not work.
Every time I find my half incomplete inbox back.

Now I removed my account but I can no longer start the app. Reinstalling TB does not help.

Is there a way to fix this?

---

### Post by deadflowr on 2017-06-20
*Thread moved to **General Help**.*

---

### Post by plucky on 2017-06-21
> I removed/reinstalled TB but it does not work.
Every time I find my half incomplete inbox back.

Reinstalling Thunderbird does not remove the data stored in your /home directory.
```
~/.thunderbird
~/.cache/thunderbird
```
are the two files you need to remove.

> Now I removed my account but I can no longer start the app. Reinstalling TB does not help
Open a terminal and type ```
thunderbird
```
Post any output that results if thunderbird doesn't open.

Good Luck

---

### Post by bask185 on 2017-07-05
Hey I have another question. I followed your instructions, repaired thunderbird and set it op again with my exchange mail but when thunderbird stops again with showing new e-mails is there an easier way to fix that? Is it also known what the cause may be?

---

