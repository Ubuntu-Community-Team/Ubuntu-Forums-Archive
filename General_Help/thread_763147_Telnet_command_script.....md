---
title: "Telnet command script...."
date: 2008-04-22
forum: General Help
---

### Post by DJmart on 2008-04-22
Hey fellas,

In a nutshell I have posted some code of what I need automatically "entered" into a telnet session:

```

# !/bin/sh

  telnet localhost 25
  ehlo localhost
  mail from: myemail@mydomain.com
  rcpt to: anotheremail@anotherdomain.com
  data
  Message here, blah blah. What ever.
  .
  quit

```

After talking with some people, I realized this cannot be done directly, that script is rubbish, but it shows exactly how I need it to be done. a Telnet session WILL start if "telnet localhost 25" is executed, and the rest of the lines must be entered.

I do not know a lot about the scripting, which is why im asking for the assistance of the knowledgeable ones!

Thanks in advance anyone who can help!

-DJmart

---

### Post by warp99 on 2008-04-22
> **DJmart said:**
> Hey fellas,

In a nutshell I have posted some code of what I need automatically "entered" into a telnet session:

After talking with some people, I realized this cannot be done directly, that script is rubbish, but it shows exactly how I need it to be done. a Telnet session WILL start if "telnet localhost 25" is executed, and the rest of the lines must be entered.

I do not know a lot about the scripting, which is why im asking for the assistance of the knowledgeable ones!

Thanks in advance anyone who can help!

-DJmart

You could do it like this:

Place the items to be entered in the telnet session within a file:
```
ehlo localhost
mail from: myemail@mydomain.com
rcpt to: anotheremail@anotherdomain.com
data
Message here, blah blah. What ever.

```
Let's call the file mail_items, then issue the following command:
```
cat mail_items | nc -q 0 localhost 25
```
the arguments in the mail_items file will be passed to the telnet sessions via netcat (nc) and will exit (-q 0).

---

### Post by DJmart on 2008-04-22
You are the best!

It works perfectly, thanks so much.

---

