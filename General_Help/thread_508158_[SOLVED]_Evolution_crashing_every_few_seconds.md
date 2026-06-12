---
title: "[SOLVED] Evolution crashing every few seconds"
date: 2007-07-23
forum: General Help
---

### Post by BlueNoteExpress on 2007-07-23
I've been using Ubuntu and Evolution for a few weeks now, but today Evolution started crashing about 5 seconds after I open it every time.  Anybody know what might be causing this?

When I start evolution from a terminal, here's what I get:

```
nick@Coruscant:~$ evolution
CalDAV Eplugin starting up ...

(evolution-2.10:6466): evolution-mail-WARNING **: ignored this junk plugin: not enabled or we have already loaded one

(evolution-2.10:6466): e-utils-WARNING **: Plugin 'Spamassassin junk plugin' failed to load hook 'org.gnome.evolution.mail.junk:1.0'
** (evolution-2.10:6466): DEBUG: mailto URL command: evolution %s
** (evolution-2.10:6466): DEBUG: mailto URL program: evolution
Segmentation fault (core dumped)
nick@Coruscant:~$ 
```

Anybody know how I can fix this Segmentation fault / core dump?

Thanks.

---

### Post by BlueNoteExpress on 2007-07-24
Well, I managed to resolve this issue.  It turns out that one of the messages in the Inbox was in a format Evolution couldn't handle.  It was an expected message (not spam or anything) so I guess Evolution (this version anyway) just isn't very robust.  Maybe I'll give Thunderbird a whirl.

Fortunately, this account also has a web client.  I deleted the offending message using the web client, and then deleted Inbox.cmeta.  Evolution stopped crashing after I did that.

---

### Post by stchman on 2007-07-24
Cool.  Thunderbird is supposed to be more robust.  Tbird irritates me.

---

### Post by holbech on 2007-08-22
If you don't care too much about your configurations you can delete the config directory

#rm -rf .evolution

Worked for me, All accounts still working, all mails kept etc... Only thing I can see missing is the plugins (which were causing Ev to crash)

---

### Post by aonegodman on 2008-02-14
> **BlueNoteExpress said:**
> Well, I managed to resolve this issue.  It turns out that one of the messages in the Inbox was in a format Evolution couldn't handle.  It was an expected message (not spam or anything) so I guess Evolution (this version anyway) just isn't very robust.  Maybe I'll give Thunderbird a whirl.

Fortunately, this account also has a web client.  I deleted the offending message using the web client, and then deleted Inbox.cmeta.  Evolution stopped crashing after I did that.

Can't locate "inbox.cmeta" to delete?

Please show the way. Thanks.  :)


Well it seemed to work by deleting the offending file with a video attachment on my Gmail web mail server. Evolution has become stable again.

I guess I don't need to delete the inbox.cmeta on my computer, but would still like to know where it's at.   Thanks again.

---

### Post by tillo4 on 2008-02-22
Sorry guys tried out all the above n still it crashes every 2 secs H:elp:confused:

---

