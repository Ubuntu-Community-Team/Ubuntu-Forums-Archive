---
title: "procmail with mutt"
date: 2007-12-24
forum: General Help
---

### Post by go_beep_yourself on 2007-12-24
After email is sorted with procmail, how can I view all the different emails at once with Mutt? Can I see a list of the sorted emails? I see this in the example .muttrc that I found and am using. What does it do?

mailboxes ! +Fetchmail +slrn +mutt

I see one example online where this is in a .muttrc

set spoolfile = /home/user/Mail/install

Is this a good idea to do? Why or why not?

---

### Post by andrew.46 on 2007-12-25
Hi,

 Good to see a fellow mutt user:

> **go_beep_yourself said:**
> After email is sorted with procmail, how can I view all the different emails at once with Mutt? Can I see a list of the sorted emails? I see this in the example .muttrc that I found and am using. What does it do?

mailboxes ! +Fetchmail +slrn +mutt

It all depends on where procmail delivers the mail, whether simply to the mail spool or to individual maiboxes. The "mailboxes ! +Fetchmail ..." tells mutt to notify you when there is new, unread mail in those mailboxes.

>  I see one example online where this is in a .muttrc

set spoolfile = /home/user/Mail/install

Is this a good idea to do? Why or why not?It is a rather odd name to call your mail spool, but you get to chose where the mail is delivered. Traditionally the mail spool is /var/spool/mail/username but it could as well be $HOME/mail/inbox. The choice is yours.

          Andrew

---

### Post by go_beep_yourself on 2007-12-25
> **andrew.46 said:**
> Hi,

 Good to see a fellow mutt user:



It all depends on where procmail delivers the mail, whether simply to the mail spool or to individual maiboxes. The "mailboxes ! +Fetchmail ..." tells mutt to notify you when there is new, unread mail in those mailboxes.

It is a rather odd name to call your mail spool, but you get to chose where the mail is delivered. Traditionally the mail spool is /var/spool/mail/username but it could as well be $HOME/mail/inbox. The choice is yours.

          Andrew

Are mailboxes different mail files that procmail has sorted? I'd like to be able to switch between those in Mutt. I noticed your guide doesn't have anything about procmail. Are you going to add that information to it?

---

### Post by go_beep_yourself on 2007-12-25
Also, your guide should include integrating gpg with Mutt.

---

### Post by andrew.46 on 2007-12-26
Hi again:

> **go_beep_yourself said:**
> Are mailboxes different mail files that procmail has sorted? I'd like to be able to switch between those in Mutt. I noticed your guide doesn't have anything about procmail. Are you going to add that information to it?

Hmmm.... are you perhaps referring to this:

[http://ubuntuforums.org/showthread.php?t=565326](http://ubuntuforums.org/showthread.php?t=565326) 

which is a guide I wrote? This contains a small introduction to procmail but not much more, but the intention was only ever to furnish a *starting* point.

Mailboxes can take several different formats, I use mbox myself which is a single file format unlike Maildir for example. To navigate to different directories in mutt start by pressing the 'c' key.

This walkthrough will not be developed any further by me as I no longer use Ubuntu.  I leave it to others to refine, rewrite etc. I will however keep working on my own private mutt page:

[http://www.andrews-corner.org/mutt.html](http://www.andrews-corner.org/mutt.html)

which might perhaps have information of use to you?

     Andrew

---

### Post by go_beep_yourself on 2007-12-26
> **andrew.46 said:**
> Hi again:



Hmmm.... are you perhaps referring to this:

[http://ubuntuforums.org/showthread.php?t=565326](http://ubuntuforums.org/showthread.php?t=565326)

No, this.

[http://www.andrews-corner.org/mutt.html](http://www.andrews-corner.org/mutt.html)

> Mailboxes can take several different formats, I use mbox myself which is a single file format unlike Maildir for example. To navigate to different directories in mutt start by pressing the 'c' key.

If mailboxes are files when using mbox format, then why did you refer to them again as directories?

> [http://www.andrews-corner.org/mutt.html](http://www.andrews-corner.org/mutt.html)

which might perhaps have information of use to you?

There's not explanations of what's in your example .muttrc and how to setup procmail to work with Mutt even though your .muttrc has been configured to work with mail sorted by procmail. The part about using imap with gmail, but have been useful, but I am not sure it's working.

---

### Post by andrew.46 on 2007-12-27
Hi,

 I am not completely sure *exactly* what your question is but I shall attempt an answer:

> **go_beep_yourself said:**
> No, this.[http://www.andrews-corner.org/mutt.html](http://www.andrews-corner.org/mutt.html)
If mailboxes are files when using mbox format, then why did you refer to them again as directories?

In fact the use of the term 'directories' was inaccurate. You will note in the ~/.muttrc on that particular page the following:

```
set mbox_type=mbox    # Mailbox type
```This specifies the mbox format which contains each  'mailbox' in a single file. To navigate these in mutt press the 'c' key.

 > There's not explanations of what's in your example .muttrc and how to setup procmail to work with Mutt even though your .muttrc has been configured to work with mail sorted by procmail. The part about using imap with gmail, but have been useful, but I am not sure it's working.There is actually sufficient explanation on this page to achieve a working copy of mutt in combination with msmtp and procmail. If you read a little closer you will note that procmail has been set to deliver to the mail spool as mutt has bee set to read from there. A sorting recipe for 'slrn' has been suggested in the procmail section that delivers to the local mail folder of $HOME/mail and mutt has been set to flag new mail in this folder with the mailboxes ! +slrn section of the ~/.muttrc file.

If you have suggestions for improvement to this page I would welcome your thoughts but please have a close read of the page first, I think many of your needs have already been answered there.


Andrew

---

