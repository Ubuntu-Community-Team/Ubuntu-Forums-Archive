---
title: "Mutt and pop3"
date: 2006-11-20
forum: General Help
---

### Post by thomasaaron on 2006-11-20
Hi, folks.
I'm trying to set up mutt to check my pop3 mail at yahoo.
Below is what I've been able to figure out thus far for my .muttrc file.
According to the web site I learned to do this from, this should do the trick. But it's not.

To be honest, I'm not even sure I'm pressing the right button in mutt to check my pop mail.

I'm pressing G (which, in the help menu is supposed to fetch pop mail). it's not working. It just says: "No mail messages."

Any ideas?

# Mail Folder
set folder = ~/Mail     # Directory that contains all mail files (mailboxes)
set spoolfile = +Inbox  # Default spoolfile
set mbox = +Inbox       # Where mail is appended to from spoolfile
set mbox_type = mbox    # Type of mail files
set postponed = +Unsent # Where to save postponed mail
set copy = yes          # Save copies of outgoing mail?
set record = +Sent      # Where to save copies of outgoing mail

# Personal options
set hostname = "pop.mail.yahoo.com"
set realname = "Thomas Aaron"
set signature = ~/.signature

# Aliases (address book)
set alias_file = ~/.mutt-aliases
source ~/.mutt-aliases
set reverse_alias       # Show real name instead of e-mail address in index
set sort_alias = alias  # Sort aliases by alias name not email address

# Prune the headers!
ignore *                        # Ignore all header info
unignore subject
unignore to
unignore from:
unignore date
unignore CC

hdr_order Date: From: To: CC: Subject:

# Mailboxes
mailboxes =Inbox
mailboxes =Mailing-Lists/Kickstart-list
mailboxes =Mailing-Lists/LinuxWorld
mailboxes =Mailing-Lists/PPA-Devel
mailboxes =Mailing-Lists/PPA-Users
mailboxes =Mailing-Lists/RPM-list

set pop_host ="pop.mail.yahoo.com"
set pop_user ="<my username>"  #yes,I entered my actual username
set pop_pass ="<my password>"  #yes, I entered my actual password
set pop_delete =no      # Save mail on server or not

---

### Post by mark_g on 2006-11-20
It's generally a better idea to use another program to retrieve your email (Mail Delivery Agent) and then use Mutt (Mail User Agent) only to read it.
There's a great program called getmail you can use that does this for you ([http://pyropus.ca/software/getmail/](http://pyropus.ca/software/getmail/)) and it's in the repositories. Fetchmail is a more well-known one, but I find getmail way easier to configure and just as powerful.

You can add something like this to your .muttrc to check you email.
```

macro index     G "!getmail -v -r /home/username/.getmail/getmailrc\n" "Invoke getmail"
```

or add the getmail command to cron to check it periodically.

An advantage of using this approach is you can even put another program between the two that will sort your e-mail or detect spam e.g.
getmail > spamassassin > mutt

---

### Post by andrew.46 on 2007-07-02
Hi,

 Hmmmm this is an old post but I have published a guide which may be of assistance to you:
[http://people.aapt.net.au/~adjlstrong/mutt.html](http://people.aapt.net.au/~adjlstrong/mutt.html)

                 Andrew

---

