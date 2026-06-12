---
title: "getmail and yahoo.co.uk"
date: 2016-10-27
forum: General Help
---

### Post by Andrew_Welham on 2016-10-27
Thought this would be simple I'm trying to configure getmail to access pop.mail.yahoo.co.uk, which works from a thunderbird client so pop is enabled
my config file for getmaill is



```
[options]
verbose = 0
delete = false
read_all = false
message_log = ~/.getmail/filename.log
message_log_verbose = true

[retriever]
type = SimplePOP3SSLRetriever
server =  pop.mail.yahoo.co.uk
username = username
password = password

[destination]
type = Mboxrd
path = /home/andrew/Mail/inbox
user = osusername

```

every tine it just fails to connect with 

```
connect() [_retrieverbases.py:382] establishing POP3 SSL connection to pop.mail.yahoo.co.uk:995

```

any ideas

---

### Post by howefield on 2016-10-27
That configuration works for me with the addition of the port number....

```
[options]
verbose = 0
delete = false
read_all = false
message_log = ~/.getmail/filename.log
message_log_verbose = true

[retriever]
type = SimplePOP3SSLRetriever
server = pop.mail.yahoo.co.uk
port = 995
username = abcdef.ghij@sky.com
password = ghwivnhgdhvodvov

[destination]
type = Mboxrd
path = /home/hugh/Mail/inbox
user = hugh
```

---

### Post by Andrew_Welham on 2016-10-28
fixed.
The host with issues had additional dns filtering which routed all requests to open dns, so the error was correct could not connect....

---

