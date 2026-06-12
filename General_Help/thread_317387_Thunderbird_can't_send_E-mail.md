---
title: "Thunderbird: can't send E-mail"
date: 2006-12-12
forum: General Help
---

### Post by IusedTObeSOMEONEelse on 2006-12-12
Good Morning Everyone!! When trying to send E-mail using Thunderbird I keep getting error something to do with SMTP not allowing it to send. I have contacted my ISP and all is ok on that end. I can receive ok. Error message is something about failing to connect to SMTP and to check settings. I have completely removed thunderbird and re-installed. When I removed Thunderbird, the SMTP did not remove.How can I completely wipe out all info in Thunderbird? Also should be noted that same error occurs with Evolution about sending and SMTP

---

### Post by earobinson on 2006-12-12
have you tried any other email clients?

---

### Post by IusedTObeSOMEONEelse on 2006-12-12
Thank you for quickness i response! No I haven't. I really don't know any other. I do not require any thing fancy as I only use it to receive simple E-mail from family & such. I am open to suggestions ;)

---

### Post by DeadEyes on 2006-12-12
Have you checked the setting for the "outgoing mail server", that it matches the one your ISP wants you to use?
Edit:
[this]("http://kb.mozillazine.org/Cannot_send_mail") might help

---

### Post by IusedTObeSOMEONEelse on 2006-12-12
When I go to tools, there is no account settings,Address Book>Extensions>Themes>etc.

---

### Post by earobinson on 2006-12-12
> **MustangSallydd said:**
> Thank you for quickness i response! No I haven't. I really don't know any other. I do not require any thing fancy as I only use it to receive simple E-mail from family & such. I am open to suggestions ;)
evolution comes with ubuntu and its worth a try to see if its a thunderbird thing or not

---

### Post by IusedTObeSOMEONEelse on 2006-12-12
> **earobinson said:**
> evolution comes with ubuntu and its worth a try to see if its a thunderbird thing or not

> **MustangSallydd said:**
> Good Morning Everyone!! When trying to send E-mail using Thunderbird I keep getting error something to do with SMTP not allowing it to send. I have contacted my ISP and all is ok on that end. I can receive ok. Error message is something about failing to connect to SMTP and to check settings. I have completely removed thunderbird and re-installed. When I removed Thunderbird, the SMTP did not remove.How can I completely wipe out all info in Thunderbird?** Also should be noted that same error occurs with Evolution about sending and SMTP**

already tried

---

### Post by earobinson on 2006-12-12
wow my bad, sorry, Im betting you have the wrong settings, they work on any other boxes? Windows?

---

### Post by DeadEyes on 2006-12-12
> **MustangSallydd said:**
> When I go to tools, there is no account settings,Address Book>Extensions>Themes>etc.

That is probably referring to the windows version. I'm not at home so I don't have access to the Linux version, just try all the different menus and see can you find it. I do remeber it being tricky to find.

try Edit->Account Settings

---

### Post by ajgreeny on 2006-12-12
Assuming you have tried entering all your account details without success, another possibility is to make sure all your mail is backed up:-
~/.mozilla-thunderbird/alphanumeric.default/Mail
then delete your profile, the same .mozilla-thunderbird folder.  Now restart thunderbird.  You will now be asked to create a user acount, if I remember correctly and can enter all your details which you should have from your ISP.

This sort of thing can happen if a configuration file has corrupted in some way.  Any add-ons or extensions you had will need to be reinstalled, but beware; it could be one of those which caused the problem.

---

### Post by IusedTObeSOMEONEelse on 2006-12-12
ok, I just had my ISP walk me through a set up on my linux machine with thunderbird and still get same error. I went to synaptic and completely removed thunderbird and reinstalled.it re-installs with SMTP already there. How so? I had not re-configured yet. And also theme was there as well. I would like to start with a "virgin" thunderbird. How can I wipe all info out. I have nothing to back up so it should be simple?

---

### Post by IusedTObeSOMEONEelse on 2006-12-12
Got it  :p   I went into /home/mozz. and wiped out history and that presented me with a fresh thunderbird. Thanks to all who replied.

---

