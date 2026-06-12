---
title: "Telnet and backspace"
date: 2007-01-18
forum: General Help
---

### Post by olejorgen on 2007-01-18
When I telnet into my crappy speedtouch router I can't delete characters. I can fix this by using the control character and do "mode line", but it's highly annoying to do this each time. When I type my username/password backspace does not work either.

I have put this in my .telnetrc file but it does not help. (probably because I have to be logged in before I do "mode line"

```

DEFAULT
        set localchars
        set escape ^O
        mode line

```

Is there a solution?

---

### Post by lukew on 2007-01-18
You need to map the backspace key to the erase

[HTML]http://tldp.org/HOWTO/Keyboard-and-Console-HOWTO-5.html[/HTML]

---

### Post by olejorgen on 2007-01-20
Thanks, but that's seem a litte heavy for me. What exacly do I need to do?

Should I put 
```

stty erase <telnet code for erase>

```
in my .telnetrc file?

---

### Post by ynnhoj on 2007-01-20
i remember when i was in college, one of the servers i used to access via telnet always buggered up my backspace key, so i had to use control+h.  i noticed *set escape ^O* in your .telnetrc, so maybe the addition of *set erase ^H* would do the trick..?  just a guess, though.

---

### Post by olejorgen on 2007-01-21
Yeah, that might work, but I'd rather use my backspace key. It works on windows so I should be possible to get it to work here too :-/

---

### Post by olejorgen on 2007-06-27
If someone is having the same problem, you could use **rlwrap**. (alias telnet='rlwrarp telnet')

It gives you readline functionality in any program. Not perfect, but it works mostly. (eg. I could not get the password detection to work)

---

### Post by barney_1 on 2007-09-30
Anyone have an answer for this?  I just need my telnet to send "CTRL-H" when I press the backspace key.  Can that be done with .telnetrc and how?

Thanks!

---

### Post by QuantumCow on 2008-01-08
This site has info that worked for me.

[http://www.ibb.net/~anne/keyboard/keyboard.html#other]("http://www.ibb.net/~anne/keyboard/keyboard.html#other")

Here is a breakdown.  

Note: 
-I cleaned up some of the script, so that grep doesn't wait for input if nothing is passed.  
-I renamed my list of hosts with bad backspaces a little different than the example on the webpage.
-This only works if the host name is passed as part of the command line.

1.Create a script called kbdfix, in /usr/bin, with the following code

#!/usr/bin/expect

eval spawn -noecho $argv

interact {
 \177        {send "\010"}
 "\033\[3~"  {send "\177"}
}

2.Rename the telnet binary in /usr/bin to telnet.orig

3.Create a list of hosts in  /usr/bin that need the backspace fixed and name it bad-bs-hosts

3.Create a script called telnet with the following code

#!/bin/sh

if [ "$#" -ge 1 ]; then
        if grep -wq "$@" /etc/bad-bs-hosts ; then
                exec kbdfix telnet.orig "$@"
        else 
                exec telnet.orig "$@"
        fi
else
        exec telnet.orig
fi

4. Don't forget to chmod everything to be executable

---

