---
title: "Question about Startup Applications and Bash script orders"
date: 2018-09-05
forum: General Help
---

### Post by webmiester on 2018-09-05
Hi everyone,

I would like to ask about how bash scripts and startup applications work:

1) If my bash script called on a particular program, how will it respond to the lines below that program:  For intance:

#! /bin/bash
chromium
xmodmap -e "clear Control"

>  Will bash load xmodmap right after it runs chromium or will it have to wait until chromium closes until it starts Xmodmap?

2) How does the startup applications choose the order it will load the items?

A.I noticed that in the GUI, the startup applications is in alphabetical order, so does it load the items in alphabetical order too?

B. If I put lets say a bash script in the startup applications that has "sleep 40" in it, will startup applications wait until this bashscript finishes before it runs the next  item in its list?  Or wil it run the next item on its list immediately, not waiting for this bash script to finish?

Thanks

---

### Post by &amp;KyT$0P# on 2018-09-05
> **webmiester said:**
> If my bash script called on a particular program, how will it respond to the lines below that program:  For intance:

#! /bin/bash
chromium
xmodmap -e "clear Control"

>  Will bash load xmodmap right after it runs chromium or will it have to wait until chromium closes until it starts Xmodmap?
It would wait until chromium closes.  If you don't want that, add a & on the end of the chromium command, so it would look like this -
```
#!/bin/bash
chromium &
xmodmap -e "clear Control"
```

---

### Post by DuckHook on 2018-09-05
> **webmiester said:**
> Will bash load xmodmap right after it runs chromium or will it have to wait until chromium closes until it starts Xmodmap?
[s]Scripts do not work as if they are invisible consoles. If you launch an app in a console, the app occupies the foreground until you send to background. In scripts, apps are launched into their own processes and the script immediately goes to the next instruction. The only time it does not do so is if you launch both commands on the same line with the && pipe.[/s]

Edit: corrected by halogen2 (see above).

Brain cramp.
> …A.I noticed that in the GUI, the startup applications is in alphabetical order, so does it load the items in alphabetical order too?
Yes. If you want to control the load order, name your startup apps/scripts with the following convention: 0-app A,  1-app B, etc.
> B. If I put lets say a bash script in the startup applications that has "sleep 40" in it, will startup applications wait until this bashscript finishes before it runs the next  item in its list?  Or wil it run the next item on its list immediately, not waiting for this bash script to finish?
Startup Applications will not wait. The *sleep* command effects only what is in your script. It cannot (and should not) effect anything outside your script. *sleep* is usually used to delay launch of program 'A' until program 'B' launches, upon which program 'A' depends. Obviously, this functionality would be short-circuited if the system waits for 'A' to finish sleeping before launching 'B'.

---

### Post by webmiester on 2018-09-05
> **halogen2 said:**
> It would wait until chromium closes.  If you don't want that, add a & on the end of the chromium command, so it would look like this -
```
#!/bin/bash
chromium &
xmodmap -e "clear Control"
```

Will this "&" thing still work even if I have lots of arguments with chromium

e.g.

chromium --kiosk http:google.com --kiosk-printing --profile-directory=Default &
xmodmap -e "clear Control"

---

### Post by &amp;KyT$0P# on 2018-09-05
> **webmiester said:**
> Will this "&" thing still work even if I have lots of arguments with chromium
Yes  (It's a feature of bash, not a Chromium feature.)

---

### Post by webmiester on 2018-09-06
Thanks so much.  How do I  mark a thread as solved?

---

### Post by raleigh3 on 2018-09-06
Just click on Thread Tools on the right side.

---

