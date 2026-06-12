---
title: "NEED HELP w/ Mutt &amp; Procmail"
date: 2005-08-03
forum: General Help
---

### Post by hzs202 on 2005-08-03
Hi,

OK, I am having trouble with mutt & procmail...  ](*,)  

Firstly now that I have configured procmailrc... mutt can nolonger read or find my mail. At the bottom of mutt it identifies that it is reading from [FONT=Courier New]/var/mail/$LOGNAME[/FONT].

[COLOR=DarkRed]**The problem:**[/COLOR]
I have a directory called [FONT=Courier New]~/Mail[/FONT] however it is empty. Even after I executed [FONT=Courier New]fetchmail[/FONT] it remained empty. In fact after I executed [FONT=Courier New]fetchmail[/FONT] and downloaded 196 messages mutt could not find any mail. This is a new occurence since I setup procmail.

Below see my [FONT=Courier New].procmailrc[/FONT] file:```
# Hakim Singhji's .procmailrc file

SHELL=/bin/sh
PMDIR=$HOME/Procmail
LOGFILE=$PMDIR/pmlog
MAILDIR=$HOME/Mail
INCLUDERC=$PMDIR/rc.testing
INCLUDERC=$PMDIR/rc.subscriptions
# EOF
``` I am not sure where the messages that I downloaded went? Or why mutt cannot find any email messages? PLEASE HELP!

[SIZE=1]*My apologies for cross-posting to freebsdforum.org however I am porting the config files to FreeBSD and having the same problem... I cross-posted just incase there is a FreeBSD specific workaround.* [/SIZE]

---

### Post by dataw0lf on 2005-08-03
What folder and mailboxes do you have defined in your .muttrc? Take a look at this link for more info: 
[http://linux.ucla.edu/guides/mailguide.php3](http://linux.ucla.edu/guides/mailguide.php3)

It might help.

---

### Post by hzs202 on 2005-08-03
[QUOTE=dataw0lf]What folder and mailboxes do you have defined in your .muttrc?[/QUOTE]I was actually using the default [FONT=Courier New]/etc/Muttrc[/FONT] in Ubuntu which I notice does not have:```
set realname
set folder
set mbox=
``` Is that why my default mailbox is [FONT=Courier New]/var/mail/hzs202[/FONT]???

---

### Post by grj on 2005-08-11
sudo cp /etc/Muttrc /home/username/.muttrc

then add these lines near the top

set mbox_type=Maildir
# set mbox=~/Mail/inbox/
set spoolfile=~/Mail/inbox/
set folder=~/Mail/
set realname="your name"
set from="your full email address"
set use_from=yes
set envelope_from=yes
set move=no

you also need to set up a local .procmailrc with the following lines
HOME=/home/username              # where is our homedir
# DEFAULT=/var/spool/mail/gary # what is the default place to store mail
MAILDIR=$HOME/Mail
LOGFILE=$HOME/.procmaillog        # keep a log

:0
* ^Subject:*.*
inbox/

then on both files run
chmod 0660 filename

---

### Post by go_beep_yourself on 2007-12-25
> **grj said:**
> sudo cp /etc/Muttrc /home/username/.muttrc

then add these lines near the top

set mbox_type=Maildir
# set mbox=~/Mail/inbox/
set spoolfile=~/Mail/inbox/
set folder=~/Mail/
set realname="your name"
set from="your full email address"
set use_from=yes
set envelope_from=yes
set move=no

you also need to set up a local .procmailrc with the following lines
HOME=/home/username              # where is our homedir
# DEFAULT=/var/spool/mail/gary # what is the default place to store mail
MAILDIR=$HOME/Mail
LOGFILE=$HOME/.procmaillog        # keep a log

:0
* ^Subject:*.*
inbox/

then on both files run
chmod 0660 filename

Why should spoolfile be set to ~/Mail/inbox/? I saw a lot of examples online that have spoolfile=/var/mail/user. Why do you have "set mbox=~/Mail/inbox/" commented out?

---

