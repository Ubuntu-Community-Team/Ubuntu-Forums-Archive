---
title: "abort shutdown"
date: 2013-01-07
forum: General Help
---

### Post by bilboubu on 2013-01-07
Is it possible to abort a shutdown using a shutdown script based on a certain condition?
 
eg rc.local script
 
if conition = true
 
abort shutdown command here
 
fi
 
what would the command be? Or is it just a paticular exit number??

---

### Post by steeldriver on 2013-01-07
you mean like [FONT=Courier New]shutdown -c[/FONT] ?

```
NAME
       shutdown - bring the system down

SYNOPSIS
       shutdown [OPTION]...  TIME [MESSAGE]

DESCRIPTION
       shutdown  arranges  for the system to be brought down in a safe way.  All logged-in users are notified that the system is going down and, within
       the last five minutes of TIME, new logins are prevented.
.
.
.

OPTIONS
       -r     Requests that the system be rebooted after it has been brought down.

       -h     Requests  that the system be either halted or powered off after it has been brought down, with the choice as to which left up to the sysâ
              tem.

       -H     Requests that the system be halted after it has been brought down.

       -P     Requests that the system be powered off after it has been brought down.

[B]       -c     Cancels a running shutdown.  TIME is not specified with this option, the first argument is MESSAGE.
[/B]
       -k     Only send out the warning messages and disable logins, do not actually bring the system down.

```

---

### Post by Grenage on 2013-01-07
You mean like a basic terminal command?  I generally use:

```
shutdown -h -P now
```

I imagine at least one of those flags is not required in Ubuntu, but it won't throw up an error, and I like to be verbose for the practice.

---

### Post by bilboubu on 2013-01-07
if shutdown -c does it that would be great.
 
I'll try it out.
 
In my sleep.d suspend script the script just exits if the condition is met rather than issuing a counter command and the machine does not suspend. I though there may be somethine like this.

---

