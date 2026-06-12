---
title: "[SOLVED] a sed question"
date: 2007-11-18
forum: General Help
---

### Post by jordanmthomas on 2007-11-18
Hello, I have a quick question about sed and using newlines.

Say I have a file with one line in it like so:
```
va.artofwarcentral.com
```
I want to split each of the parts separated by periods into new lines.

I used sed to do this:
```
sed 's/\./\n/g' filename
```
and it works without incident.  The output is this:
```

va
artofwarcentral
com

```

However, when I try this on OS X I get this unexpected output:
```

va[COLOR="#ff0000"]n[/COLOR]artofwarcentral[COLOR="Red"]n[/COLOR]com
```

Am I mistaken in thinking that the newline character in OS X is \n ?  I have tried \r and \n\r, all to no avail.  If I use anything other than a newline, like a string of characters, it is substituted correctly.

So, I guess my question is this:  am I doing something wrong or is this something that OS X is doing retardedly?  Any help is appreciated.

---

### Post by jordanmthomas on 2007-11-18
Well, I have solved my own problem by just making a workaround.  Instead of using newlines, I just use spaces and then awk to get the parts I want out.

---

