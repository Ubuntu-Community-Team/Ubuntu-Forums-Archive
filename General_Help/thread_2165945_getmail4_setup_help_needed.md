---
title: "getmail4 setup help needed"
date: 2013-08-07
forum: General Help
---

### Post by bill-lancaster on 2013-08-07
I want to download my emails using the command line and thought I'd try getmail.
I've set up the directories it needs and tried to figure out the  correct settings but get this message:-


  getmail version 4.30.2
  Python version 2.7.3 (default, Sep 26 2012, 21:51:14) 
[GCC 4.7.2]

Unhandled exception follows:
    File "/usr/bin/getmail", line 721, in main
    success = go(configs)
    File "/usr/bin/getmail", line 299, in go
    retriever.abort()
    File "/usr/lib/python2.7/dist-packages/getmailcore/_retrieverbases.py", line 746, in abort
    self.conn.rset()
  AttributeError: 'SimplePOP3SSLRetriever' object has no attribute 'conn'

Please also include configuration information from running getmail
with your normal options plus "--dump".

I don't understand these messages.

This is how my getmailrc file looks:-

[retriever]
type = SimplePOP3SSLRetriever
server = pop3.lineone.net
port = 110
username = bill-lancaster
password = xxxxxxxxxxxxx

[destination]
type = Maildir
path = ~/mail/

[options]
delete = true
message_log = ~/.getmail/log-foreman-example

Any help would be very welcome.

---

