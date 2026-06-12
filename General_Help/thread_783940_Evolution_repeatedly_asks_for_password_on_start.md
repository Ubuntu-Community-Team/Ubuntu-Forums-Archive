---
title: "Evolution repeatedly asks for password on start"
date: 2008-05-06
forum: General Help
---

### Post by frogotronic on 2008-05-06
Hello,

Got a strange new annoyance/bug from evolution.  Running Gutsy Gibbon, all upgrades.  I am connecting to a MSX 2007 server via POP3 interface. Since Gutsy has been out, I've had no problems.  Recently (three days ago) I get a error when I first start the Evolution program.  The program prompts me for my password (which I have saved) and when I type it in, it refuses to accept it.  When I hit cancel and then check my mail, there are no problems and after this point the program functions normally.

Any ideas?  I'll try starting Evolution from the terminal and post the results.

Thanks,
CH

---

### Post by frogotronic on 2008-05-06
> **cement_head said:**
> Hello,

Got a strange new annoyance/bug from evolution.  Running Gutsy Gibbon, all upgrades.  I am connecting to a MSX 2007 server via POP3 interface. Since Gutsy has been out, I've had no problems.  Recently (three days ago) I get a error when I first start the Evolution program.  The program prompts me for my password (which I have saved) and when I type it in, it refuses to accept it.  When I hit cancel and then check my mail, there are no problems and after this point the program functions normally.

Any ideas?  I'll try starting Evolution from the terminal and post the results.

Thanks,
CH

Here's the error (over & over) when starting from terminal:

```
(evolution:9515): camel-CRITICAL **: get_message_info: assertion `folder->summary != NULL' failed

```

---

### Post by frogotronic on 2008-05-06
(not)SOLVED.

I resinstalled all "evolution" related packages via Synaptic.

___________________________________________________________________

On reboot this morning, issue was back.


Hmmm......

---

