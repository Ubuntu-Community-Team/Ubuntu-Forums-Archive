---
title: "Postfix installing problem"
date: 2007-07-01
forum: General Help
---

### Post by vhof on 2007-07-01
Hi,

I failed to install by following this howto:
[[COLOR="Blue"]https://help.ubuntu.com/community/PostfixBasicSetupHowto?highlight=%28postfix%29[/COLOR]]("https://help.ubuntu.com/community/PostfixBasicSetupHowto?highlight=%28postfix%29")



```
telnet localhost 25
```

Postfix will prompt like following in the terminal so that you can use to type SMTP commands.

```
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 valhoffman ESMTP Postfix (Ubuntu)
```


Type the following code segment in Postfix's prompt.

```
ehlo localhost
mail from: fmaster@localhost
rcpt to: fmaster@localhost
data
Subjet: My first mail on Postfix
Hi,
Are you there?
regards,
Admin
. 
quit 
```


and then,

```
su - fmaster
mail
```

i got
```
No mail for fmaster
```


I don't know also if I need to own a domain name like abcdef.com, because that's what the howto says..

Help is greatly appreciated!

---

