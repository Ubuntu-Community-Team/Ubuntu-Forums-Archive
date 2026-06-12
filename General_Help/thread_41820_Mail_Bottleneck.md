---
title: "Mail Bottleneck"
date: 2005-06-14
forum: General Help
---

### Post by Drasla on 2005-06-14
At present, I use Outlook on my Windows machine to get e-mail from two POP3 accounts and an IMAP account, as well as downloading from a number of RSS feeds.  These are all stored in one central location (my local .pst) file, and are automatically sorted and filed into subfolders by a number of rules.

I basically want to set up my Ubuntu machine so that it behaves like a back-end Outlook, downloading and organizing all my e-mail and RSS, then permitting me access to it all in an Exchange-like WebMail interface, which I'd like to be able to access remotely.

Does anyone know of any program(s) that would be capable of doing this?

---

### Post by tonym on 2005-06-15
Possible way of doing this would be the following combination:

fetchmail - retrieves mail from the remote POP3 and IMAP servers.

Local Mail service - delivers the mail received from fetchmail into local mailboxes.  I use exim.  I assume the Ubuntu standard of postfix could be used.

courier-imap - makes the local mailboxes available via IMAP.

courier-webmail - provides a web interface to the mailboxes.  I haven't done that myself.

---

### Post by desdinova on 2005-06-15
Yep i'd use

fetchmail
postfix
courier-imap
squirrelmail (<- good webmail client available through apt)

also perhaps add

clamav antivirus
spamassassin

---

### Post by Drasla on 2005-06-15
Thanks a bunch.  Also, does anyone know how I could add to this:
[list]
[*]Download of RSS headers as .eml files and integration with inbox.  At present, the NewsGator plugin for Outlook is basically doing this for me.
[*]Calendering, Task Management, and Address Book functionality (which I'd also like to have accessible via web, a la Exchange)
[/list]

---

### Post by desdinova on 2005-06-15
Then I'd use eGroupware rather then squirrelmail - note however eml files are a windowsism - as I recall eGroupware can integrate News and RSS

---

### Post by desdinova on 2005-06-15
[http://www.egroupware.org/](http://www.egroupware.org/)

---

