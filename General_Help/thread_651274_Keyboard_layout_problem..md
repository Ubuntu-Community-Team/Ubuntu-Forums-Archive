---
title: "Keyboard layout problem."
date: 2007-12-27
forum: General Help
---

### Post by PaulFXH on 2007-12-27
When I want to send an email to Brazil in the Portuguese language from abroad, I change the (Gutsy) Keyboard Layout Indicator to Bra (for Brazil) and now I can type accented Portuguese letters, such as ã, ê, ó and ç with ease.
Problem is that my colleague in Brazil sees something quite different to what I typed.
So for example, when I type "não está" what is received in Brazil is "nÃ£o estÃ¡" which actually makes the message almost unreadable.
Of course, this problem only shows intself in those letters which are not in the English alphabet.
While I realize this has something to do with encoding that's basically as far as my knowledge stretches.
Can anybody please advise as to how this problem can be resolved or what further information is required in order to ascertain what's going wrong here.
Thanks
Paul

---

### Post by icheyne on 2007-12-27
Which program are you using to send the email? That should have a setting to send email with UTF-8 encoding.

---

### Post by PaulFXH on 2007-12-27
Thanks for the reply.
I using Gmail and my colleague in Brazil uses Hotmail.
In googling around, it seems that my accented characters are indeed utf-8 encoded although my browser encoding is set to Automatic.
However, it seems that my colleague is using iso-8859-1 which gives rise to this problem. 
If I type something in Gmail with Automatic encoding (which is really utf-8 in my case) and then change the encoding to iso-8859-1, I see the exact font "mutation" that my colleague has seen in Brazil.
So, it seems this is the answer.
Can I assume that an Automatic Encoding setting in the browser in Brazil will be able to pick up that my emails are encoded in utf-8 and make the appropriate changes?

---

### Post by icheyne on 2007-12-27
In Gmail settings, there is an option called "Outgoing message encoding". Set that to UTF-8.

---

### Post by PaulFXH on 2007-12-27
OK, I'm gonna try that.
However, I'm not really sure this is going to work as my belief is that my messages ARE going out in utf-8 form.
The problem, as I see it, is that the computer in Brazil is set to iso-8859-1 coding.
Nevertheless, there's only one sure way to know and that's to try i out.

---

### Post by icheyne on 2007-12-27
If that doesn't work then I'm out of ideas.

---

