---
title: "bash one liner - reverse DNS lookup"
date: 2019-10-07
forum: General Help
---

### Post by getut on 2019-10-07
I need some help with a chained one liner that parses a log file, eliminates known good stuff, and spits out a list of IP addresses to the console, not to a file.

I know there is a cleaner way to get to the point I'm already at, but I'm chaining multiple greps and grep -v  and some sorts and am winding up with a list of IP addresses, one IP per line. How do I continue the chained commands and get the reverse DNS FQDN appended to each IP address?


Here is the tail end of my chained command...

```
grep -E -o '(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\.(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\.(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\.(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)'|sort -u
```

---

### Post by jason.jackal on 2019-10-07
I will try to assist if I can. When you say "good stuff" what is your check? What makes it good? Also, you want it to stdout not to a file correct?

Does it have to be one-liner?

---

### Post by SeijiSensei on 2019-10-07
```

IPLIST=$(whatever you're doing to create the list)

for ip in $IPLIST
do
     host $ip
done

```

You can add this to the end of the current commands with semicolons, but why not just write a script rather than limiting yourself to a one-line command?

---

### Post by getut on 2019-10-07
Basically I just reject lines containing known good ip's, user agents and that kind of stuff

Yes to stdout and prefer it to continue the chained command, not necessarily in a single command, but at least chained to what i already have.

---

### Post by getut on 2019-10-07
It's all on a logging system with non writable drive system (for the users who will be pasting this in and running it).

---

