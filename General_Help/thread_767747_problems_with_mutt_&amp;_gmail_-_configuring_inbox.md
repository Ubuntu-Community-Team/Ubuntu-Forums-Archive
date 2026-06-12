---
title: "problems with mutt &amp; gmail - configuring inbox directory"
date: 2008-04-25
forum: General Help
---

### Post by flintmecha on 2008-04-25
Hey, I'm trying to get mutt set up to access Gmail with. Now, before I continue, I want to state that YES, I do know that this topic has been brought up before and I am fully aware of the great guide at [http://www.andrews-corner.org/mutt.html](http://www.andrews-corner.org/mutt.html). 

That being said, I am still unable to get things working correctly. 

The primary problem is where the mail goes when it is downloaded. Here are my issues:

What I WANT: all new mail go to ~/Mail/inbox (Inbox being the "mailbox file" or w/e)
What happens: all new mail goes to /var/mail/flint/ (flint is the "mailbox")
Here's the kicker: in NONE of the configuration files (.muttrc, .fetchmailrc, .procmailrc, hell - even .bashrc) is the directory /var/mail/ even mentioned at ALL. I cannot for the life of me figure out why mutt (or maybe Ubuntu?) is sending the mail there. However, I do have some lines that mention /var/spool/mail/flint/ but there's another kicker here: that's not a mailbox, it's just a regular directory.

Some things I have noticed:
I am perfectly able to SEND mail with mutt from my Gmail account. A mailbox "~/Mail/sent" correctly stores sent messages. 

I either want ~/Mail/inbox to be the mailbox where all new mail goes, -OR- I at least want mutt's default view (the list that appears when I run mutt) to be /var/mail/flint. Currently, when I run mutt, the default location is /home/flint/Mail and it tells me "No mailbox is open" - I can't seem to figure out how to get mutt to open a mailbox by default rather than just a directory. Plus, if I took that option, then my inbox and my "sent" box would be in two very separate locations, something I'd have to change further.

Okay so basically want I want to know is:
How do I create a mailbox called ~/Mail/inbox and make all new e-mails go there?

I would not be here if I had not already exhausted Google. Believe me when I say I have editted every rc file associated with mutt or the other programs over and over and I just can't get mutt to do what I want!

On a somewhat unrelated note (meaning it doesn't have to do with mailboxes) whenever I press 'G' in mutt, it says "connecting to pop.gmail.com..." for about a minute, then says there was an error. Yet if I instead type "fetchmail" I am able to connect to gmail just fine and download messages. It's like mutt itself is having trouble connecting to Gmail. In .muttrc, I have 'set pop_host="pop.gmail.com"' - is this correct? If so, what else could be wrong? My "set pop_user" and "set pop_pass" are both correct.

---

### Post by flintmecha on 2008-04-25
bump..

Okay, I have more info.

I completely removed mutt and all other mail-related programs (like fetchmail, promail, etc) and I deleted all (that I know of) -rc files associated with them.

I reinstalled mutt from scratch. When you first run mutt, it always asks you to create "~/Mail". It is also supposed to create a file called "mbox" here to store email. For some reason, mutt is not doing this.

Any ideas?

---

### Post by flintmecha on 2008-04-26
bump.... help?

---

### Post by andrew.46 on 2008-04-28
Hi,

Thanks for the mention of my guide for mutt and gmail :-). I have only just seen your post as I don't spend all that much time on these forums any more having pretty much moved to slackware.

BTW the web page you mention has a little brother on these forums which is Ubuntu specific:

[http://ubuntuforums.org/showthread.php?t=565326](http://ubuntuforums.org/showthread.php?t=565326)

I think your basic question is:

> What I WANT: all new mail go to ~/Mail/inbox (Inbox being the "mailbox file" or w/e)If this is definitely what you want it can be done. Using the sequence suggested in the andrews-corner web site:

----------------------------
1.. ssl certs remain the same
------------------------------
2. fetchmail settings the same
------------------------------------
3. At the beginning of the procmail settings I include directions for setting the default mail spool in ~/.bashrc:

```
# Sets the Mail Environment Variable
MAIL=/var/spool/mail/username && export MAIL
```You will need to change this to:

```
# Sets the Mail Environment Variable
MAIL=/home/username/Mail/inbox && export MAIL
```Substituting *your* username of course. You can test this as follows:

```
andrew@skamandros:~$ source ~/.bashrc
andrew@skamandros:~$ echo $MAIL
/home/andrew/Mail/inbox
```Create the directory structure and mailbox now:

```
$ mkdir -v $HOME/Mail
$ touch $HOME/Mail/inbox
```Next alter this setting in ~/.procmailrc:

```
DEFAULT=/var/spool/mail/username               
MAILDIR=$HOME/mail 
```to this:

```
DEFAULT=/home/username/Mail/inbox             
MAILDIR=$HOME/Mail  
```Replacing with *your* username of course.

-------------------

4. msmtp settings remain the same.

------------------
5. muttrc needs a few simple changes. Alter this:
```

# If not set in ~/.bashrc:
set spoolfile = /var/spool/mail/username
```to this:

```
# If not set in ~/.bashrc:
set spoolfile = /home/username/Mail/inbox
```and this:

```
set folder="$HOME/mail"      # Local mailboxes stored here
```to this:

```
set folder="$HOME/Mail"      # Local mailboxes stored here
```-------------------

This should get you started hopefully? 

             Andrew

---

