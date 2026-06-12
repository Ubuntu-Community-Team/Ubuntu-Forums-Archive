---
title: "How can I incorporate TELNET commands into a script?"
date: 2008-01-27
forum: General Help
---

### Post by FRuMMaGe on 2008-01-27
I have a router with a cli that I control through telnet. I would like to incorporate a few of the simple commands into a script which will connect to my router and perform the commands automatically.

What is the best way to do this?

---

### Post by mssever on 2008-01-27
> **FRuMMaGe said:**
> I have a router with a cli that I control through telnet. I would like to incorporate a few of the simple commands into a script which will connect to my router and perform the commands automatically.

What is the best way to do this?
You could do someting like this (I'm using Ruby in this example, but you could use other languages, as well):

```
begin
  telnet = IO.popen("telnet somehost someport 2> /dev/null")
  telnet.each do |prompt|
    # process each prompt and write commands to telnet
  end
ensure
  telnet.close unless telnet.closed?
end
 
```

---

### Post by FRuMMaGe on 2008-01-27
> **mssever said:**
> You could do someting like this (I'm using Ruby in this example, but you could use other languages, as well):

```
begin
  telnet = IO.popen("telnet somehost someport 2> /dev/null")
  telnet.each do |prompt|
    # process each prompt and write commands to telnet
  end
ensure
  telnet.close unless telnet.closed?
end
 
```

This is helpful, but I'm not quite sure how to implement it.

How could I do the following with a bash script?

```
telnet
<in telnet shell now>
open
10.0.0.138
<then I enter my user and pass>
wireless aclentry hwaddr=00:16:01:09:ce:2c action=deny name=manual

```

---

### Post by mssever on 2008-01-27
> **FRuMMaGe said:**
> This is helpful, but I'm not quite sure how to implement it.

How could I do the following with a bash script?

```
telnet
<in telnet shell now>
open
10.0.0.138
<then I enter my user and pass>
wireless aclentry hwaddr=00:16:01:09:ce:2c action=deny name=manual

```
I don't think that my approach above is possible in bash. Maybe this will work, though I'm skeptical: ```
echo -e "open\n10.0.0.138\nuser\npass" | telnet host port
```

It looks like you might be trying to pass the hostname interactively. Specify that on the command line. E.g., ```
telnet google.com 80
``` to talk directly to Google's web server.

---

### Post by FRuMMaGe on 2008-01-27
So I would have to enter the actual commands within telnet manually?

---

### Post by mssever on 2008-01-27
> **FRuMMaGe said:**
> So I would have to enter the actual commands within telnet manually?

From bash, it appears that way. From a more powerful language, you should be able to automate it.

You might have some luck using curl instead of telnet.

---

### Post by fimblo on 2008-01-28
For simple stuff, with not conditionals (if *output* is this, then input *that*) I'd do the following:

connect to 192.168.0.1 with username foo and password bar, then run command "funkyblarg".:

[FONT="Courier New"](echo bar; sleep 0.5; echo funkyblarg ; sleep 0.5; echo exit) | telnet 192.168.0.1 -l foo
[/FONT]

the sleep is necessary so the routers telnetd service has time to query for your password, command, etc. 

hope this helps.

---

