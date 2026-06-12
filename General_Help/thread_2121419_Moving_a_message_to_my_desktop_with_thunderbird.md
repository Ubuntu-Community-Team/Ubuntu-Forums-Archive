---
title: "Moving a message to my desktop with thunderbird"
date: 2013-03-01
forum: General Help
---

### Post by Raafat1991 on 2013-03-01
Hi guys:)...i want to move a certain message (after matched a filter) to my desktop as a txt file so how can i do that ?

my e-mail manager is Thunderbird .


thank you .

---

### Post by pfeiffep on 2013-03-02
[SIZE=3]Not a complete answer, however you might be able to use this info to find your local folders.[/SIZE]:)[SIZE=3]

My Thunderbird local folders are located .... /home/pfeiffep/.thunderbird/6t6drol7.default/Mail/Local Folders[/SIZE]

---

### Post by Raafat1991 on 2013-03-02
> **pfeiffep said:**
> [SIZE=3]Not a complete answer, however you might be able to use this info to find your local folders.[/SIZE]:)[SIZE=3]

My Thunderbird local folders are located .... /home/pfeiffep/.thunderbird/6t6drol7.default/Mail/Local Folders[/SIZE]

HI...but i didn't store my emails locally...

---

### Post by schragge on 2013-03-02
When I right-click on a message, and then select *_S_ave As...*, it gets saved to disk in [Unix mbox format]("http://manpages.ubuntu.com/manpages/precise/man5/mbox.5.html"). Does it sound as what you want?

---

### Post by Raafat1991 on 2013-03-02
> **schragge said:**
> When I right-click on a message, and the select *_S_ave As...*, it gets saved to disk in [Unix mbox format]("http://manpages.ubuntu.com/manpages/precise/man5/mbox.5.html"). Does it sound as what you want?

I want that action to be automatically done,meaning with a filter of thunderbird or with a script of Python

---

### Post by schragge on 2013-03-04
> **Raafat1991 said:**
> HI...but i didn't store my emails locally...
> **Raafat1991 said:**
> I want that action to be automatically done,meaning with a filter of thunderbird or with a script of PythonWell, I guess your emails are stored on an IMAP server then. I'm not aware of any tool that allows you to write a python script that selectively fetches your emails, but if you don't mind doing it in lua, there's [imapfilter]("http://manpages.ubuntu.com/manpages/quantal/en/man5/imapfilter_config.5.html").

---

### Post by Raafat1991 on 2013-03-04
> **schragge said:**
> Well, I guess your emails are stored on an IMAP server then. I'm not aware of any tool that allows you to write a python script that selectively fetches your emails, but if you don't mind doing it in lua, there's [imapfilter]("http://manpages.ubuntu.com/manpages/quantal/en/man5/imapfilter_config.5.html").

HI...no problem i will chagne my settings to POP3 if you have a script or a filter ?

---

### Post by schragge on 2013-03-05
Well, you also can try [fdm]("http://manpages.ubuntu.com/manpages/precise/en/man5/fdm.conf.5.html"). It works with both POP3 and IMAP, and uses regular expressions. Or [readmsg](http://manpages.ubuntu.com/manpages/precise/man1/readmsg.mailutils.1.html) from GNU [mailutils](http://packages.ubuntu.com/quantal/mailutils).

---

### Post by Raafat1991 on 2013-03-05
i'm going to read them but if you have a script to do that thank you...

---

