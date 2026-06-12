---
title: "mutt , multiple accounts w/ google"
date: 2008-04-08
forum: General Help
---

### Post by yaxomoxay on 2008-04-08
I have two email accounts w/ google and I'm trying to setup mutt so that I can read them (using 'c' to change the folder), but I cannot figure out how. 
My .muttrc is this (of course I changed the username and psw):

set imap_user = "usernamei@gmail.com"
set imap_pass = "mysupersecretpassword"

set smtp_url = "smtp://username@smtp.gmail.com:587/"
set smtp_pass = "mysupersecretpassword"
set from = "username@gmail.com"
set realname = "username@gmail.com"

set folder = "imaps://imap.gmail.com:993"
set spoolfile = "+INBOX"
set record="+[Gmail]/Sent Mail”
set postponed=”+[Gmail]/Drafts”

set header_cache=”~/.mutt/cache/headers”
set message_cachedir=”~/.mutt/cache/bodies”
set certificate_file=~/.mutt/certificates

set move = no

set sort = 'threads'
set sort_aux = 'last-date-received'

ignore "Authentication-Results:"
ignore "DomainKey-Signature:"
ignore "DKIM-Signature:"
hdr_order Date From To Cc

------------

Also another info: everytime I connect, mutt fetches all the messages on the server. Is there a faster way to retrieve just the new messages ?

THANKS !!

---

### Post by Kadin2048 on 2008-06-15
Unfortunate that you didn't seem to get any replies; I'm trying to do the same thing.

I *think* that what you have to do is define multiple mailboxes (using the 'mailboxes [path]' statement in .muttrc) and then use account-hooks to change the imap_username and password variables for each account.

It looks complicated and I haven't gotten it quite working yet.  But this page might get you started (it shows what I think the right syntax is):
[http://www.mail-archive.com/mutt-users@mutt.org/msg28397.html]("http://www.mail-archive.com/mutt-users@mutt.org/msg28397.html")

Good luck and do follow up if you found a working solution!

---

