---
title: "exiting scripts"
date: 2015-03-23
forum: General Help
---

### Post by abul on 2015-03-23
I was using terminal to find the ip addresses on the server and when I run the script it doesn't end. I was wondering how I can end the script without using my keyboard?

---

### Post by Lars Noodén on 2015-03-23
Welcome.

Which script?

[****code]
#!/bin/sh
...
[/code]

---

### Post by ajgreeny on 2015-03-23
If you are using a GUI terminal I presume you could just close the terminal window with the mouse, but stopping the script's actions may still be dependent on what exactly the script is doing, so show us what is in the script, as asked for by Lars Noodén.

---

### Post by kerry_s on 2015-03-23
> **abul said:**
> I was using terminal to find the ip addresses on the server and when I run the script it doesn't end. I was wondering how I can end the script without using my keyboard?

ctrl+c usually stops

if i get 1 that's stuck i'll usually just open a new tab & close the stuck 1

---

### Post by ajgreeny on 2015-03-23
> **kerry_s said:**
> ctrl+c usually stops

if i get 1 that's stuck i'll usually just open a new tab & close the stuck 1

Did you miss his request which was "how I can end the script without using my keyboard?"
Ctrl+C was using a keyboard last time I used it.

To be fair, I was just about to give the same answer until I noticed the original query, so then had to think about it a little harder.

---

### Post by kerry_s on 2015-03-23
> **ajgreeny said:**
> Did you miss his request which was "how I can end the script without using my keyboard?"
Ctrl+C was using a keyboard last time I used it.

To be fair, I was just about to give the same answer until I noticed the original query, so then had to think about it a little harder.

yeah i skimmed it, missed the keyboard part, i had just woke up.

---

### Post by abul on 2015-03-24
i'm trying to find the IP address of the macs that are on the server and the command that I am using is dns-sd -G ipv4 (hostname).
For example one of the commands that i use is dns-sd -G ipv4 rm301
The output that I get is:
Timestamp     A/R Flags if Hostname                  Address                                      TTL
 9:29:57.308  Add     2  0 rm301.78M696.nycboe.org.  0000:0000:0000:0000:0000:0000:0000:0000%<0>  60   No Such Record
 9:29:57.311  Add     2  0 rm301.78M696.nycboe.org.  10.58.16.217                                 4502


Is there a command that I can use to get out this without pressing ^C on my keyboard?
I've used the "break" and "sleep" command to automatically end this script without any success, is there anything that I'm doing wrong?

---

### Post by Lars Noodén on 2015-03-24
Very sneaky. :P That program is on OS X rather than Linux.  I don't see any options there for shortening its response time.  What data are you trying to get on the Macintosh about the other machines?

If you're trying to find the ipv4 address of the Macintosh itself, there is 'ifconfig'

---

### Post by steeldriver on 2015-03-24
Maybe you could
[LIST=1]
[*]put the process immediately in the background with & 
[*]catch and save the PID using $! 
[*]sleep for however long 
[*]pkill it using the saved PID 
[/LIST]

---

### Post by abul on 2015-03-24
I got it! I was able to get out of running the command **on my mac** by let my script run for a certain period of time with the sleep command and then killed the PID. Thanks guys for all your help, especially steeldriver, this is the hardest script that I ever wrote!
```

     
                rm="rm410"
  
               (dns-sd -G ipv4 $rm) &             #|awk 'NR==2 {print $6}' &
              
                WATCH=$!

                sleep .05

                kill -9 $WATCH

```

):P

---

