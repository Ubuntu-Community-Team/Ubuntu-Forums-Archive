---
title: "help with ekiga and asterisk..."
date: 2008-04-15
forum: General Help
---

### Post by Mia_tech on 2008-04-15
I have installed asterisk from the repos using sudo apt-get asterisk, and after configuring the sip.conf file like this:
```

[general]
port = 5060
bindaddr = 0.0.0.0
context = others

[2000]
type=friend
context=my-phones
secret=1234
host=dynamic

[2001]
type=friend
context=my-phones
secret=1234
host=dynamic

```
and the extensions.conf file
```

[others]

[my-phones]
exten => 2000,1,Dial(SIP/2000)
exten => 2001,1,Dial(SIP/2001)

```
then I start ekiga and enter
user:2000
password:1234
registrar: the ip address of the asterisk machine

but I get client unable to register... any help appreciated

thanks

---

### Post by Mia_tech on 2008-04-15
I just tried to connect ekiga from the same box as my asterisk and I get this error:

```
 -- Starting Skinny session from 127.0.0.1
[Apr 15 03:08:17] WARNING[22611]: chan_skinny.c:4387 get_input: read() returned error: Connection reset by peer
[Apr 15 03:08:17] NOTICE[22611]: chan_skinny.c:4484 skinny_session: Skinny Session returned: Connection reset by peer

```

---

