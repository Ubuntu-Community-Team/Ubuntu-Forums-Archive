---
title: "Mail in terminal!?"
date: 2005-04-24
forum: General Help
---

### Post by telmo on 2005-04-24
I'm tired of searching a howto configure mutt...
I would like to have mutt sending and receiving mails from/to a Gmail account.
Is that possible? What can i do?

thx

---

### Post by Xerampelinae on 2005-04-24
I have yet to set this up in Ubuntu, but I have configured mutt a bunch in Gentoo.   Here's the basic outline (I'm doing this all without testing it...):

**Use Getmail to Receive New Messages** 
```
apt-get install getmail4
mkdir -p ~/Mail/inbox
mkdir ~/.getmail
cat >> ~/.getmail/getmailrc << EOF
[options]
verbose = 1
delete = 0
delete_after = 7
read_all = 0
message_log = ~/.getmail/log

[retriever]
type = SimplePOP3Retriever
server = pop.gmail.com # REPLACE WITH WHATEVER GMAIL'S SERVER IS
username = USERNAME_HERE
password = PASSWORD_HERE

[destination]
type = Maildir
path = ~/Mail/inbox/
EOF
chmod 600 ~/.getmail/getmailrc

```

Now when you type 'getmail', it should download your email and save messages in ~/Mail/inbox/.


**Configure Mutt to Read New Mail** 
```
apt-get install mutt
mkdir -p ~/.mutt
echo >> ~/.mutt/muttrc << EOF
set folder = ~/Mail             # where i keep my mailboxes
set mbox_type = maildir
set spoolfile = =inbox/
macro index G "!getmail <enter>" 'start getmail' #Use capital G to get new mail in mutt pager
EOF

```

Mutt should now display your email when you type 'mutt'.

**Sending Mail with Postfix** 
It seems as if Ubuntu comes with postfix, so we might as well use that to send mail.  This is the part that I am the least sure about, since there are many different situations you have to deal with for sending mail.  However, if we're lucky you can just do the following... be sure to change smtp.isp.net to your smtp server.
```
sudo sed -e "{s/relayhost\ =/relayhost\= smtp.isp.net/}" /etc/postfix/main.cf
sudo /etc/init.d/postfix restart
```

I hope it works.  If not, I'm sure there are a million other howto's on the web to help with each of these components.

---

### Post by telmo on 2005-04-24
Thank you very much!
I'll try it now! ;)

---

### Post by telmo on 2005-04-25
When i try getmail i get:

```
ImportError:  No module named getmailcore
```

When i try mutt i get no mail at all... :(

...and when i try sudo sed -e "{s/relayhost\ =/relayhost\= smtp.gmail.com/}" /etc/postfix/main.cf i get:
```

# See /usr/share/postfix/main.cf.dist for a commented, more complete version

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

myhostname = localhost.localdomain
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = localhost.localdomain, localhost.localdomain, localhost
relayhost= smtp.google.com
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = loopback-only

```

Don't know what it means!

But i really REALLY would like to have it fully working!
It's a must have.

---

### Post by telmo on 2005-04-26
When i try getmail i get:

```
ImportError:  No module named getmailcore
```

When i try mutt i get no mail at all... :(

...and when i try sudo sed -e "{s/relayhost\ =/relayhost\= smtp.gmail.com/}" /etc/postfix/main.cf i get:
```

# See /usr/share/postfix/main.cf.dist for a commented, more complete version

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

myhostname = localhost.localdomain
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = localhost.localdomain, localhost.localdomain, localhost
relayhost= smtp.google.com
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = loopback-only

```

Don't know what it means!

But i really REALLY would like to have it fully working!
It's a must have.

---

### Post by AgenT on 2005-05-07
[QUOTE=telmo]When i try getmail i get:

```
ImportError:  No module named getmailcore
```
[/QUOTE]

This is a packaging problem. For whatever reason, the current getmail4 package insists on installing the python modules in the wrong place (in the wrong version of python). It will install the modules into .../python-2.3/ instead of .../python-2.4/. Do this (as root or sudo) to fix your problem:

 ```
cp /usr/lib/python2.3/site-packages/getmailcore/ /usr/lib/python2.4/site-packages/ -rf
```

This assumes that your current version of python is 2.4.

---

