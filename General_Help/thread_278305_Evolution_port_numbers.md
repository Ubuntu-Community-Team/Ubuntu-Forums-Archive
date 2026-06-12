---
title: "Evolution port numbers"
date: 2006-10-16
forum: General Help
---

### Post by hca on 2006-10-16
My ISP is going to change port numbers on their servers in two weeks. By that I need to change portnumber for smtp to 587. For pop-serve the port number should be 110. Otherwise I will not be able so send mail (they say). They are giving instructions for performing changes in mail clients used with MS-windows programs but not for Evolution used by Linux. (they do not appear to like Linux very much.)
Evolution does not seem to give me any means of checking and/or setting these two port numbers.
What can I do??
I am using dapper 6.01 on a home built desktop with Intel P4.

---

### Post by gpas2pseudos on 2007-01-06
I have exactly the same problem (tele2). Did you finally find a way to change this exit port?

edit:
I have found the answer myself there actually
[http://ubuntuforums.org/showthread.php?t=127852&highlight=change+port+evolution](http://ubuntuforums.org/showthread.php?t=127852&highlight=change+port+evolution)

smtp.tele2.fr:587

---

### Post by ayoli on 2007-01-06
since i can't see any port settings in evolution conf, i guess you have to specify this with the server adress, ie:
smtp.mail.server.com:587
try this and give a feedback to let us know if it works.

---

### Post by hca on 2007-02-06
> **gpas2pseudos said:**
> I have exactly the same problem (tele2). Did you finally find a way to change this exit port?

edit:
I have found the answer myself there actually
[http://ubuntuforums.org/showthread.php?t=127852&highlight=change+port+evolution](http://ubuntuforums.org/showthread.php?t=127852&highlight=change+port+evolution)

smtp.tele2.fr:587

Excuse me for reacting so slowly. Yes thank you it solved the issue. What I did was to go into Evolution's  tool for account edit end further into sending email. There under smtp server I wrote 
smtp.tele2.dk:587

--AND ALL IS WELL NOW--

---

### Post by hca on 2007-02-06
> **gpas2pseudos said:**
> I have exactly the same problem (tele2). Did you finally find a way to change this exit port?

edit:
I have found the answer myself there actually
[http://ubuntuforums.org/showthread.php?t=127852&highlight=change+port+evolution](http://ubuntuforums.org/showthread.php?t=127852&highlight=change+port+evolution)

smtp.tele2.fr:587

Excuse me for reacting so slowly. Yes thank you it solved the issue. What I did was to go into Evolution's tool for account edit end further into sending email. There under smtp server I wrote
smtp.tele2.dk:587

--AND ALL IS WELL NOW--
Edit/Delete Message

---

