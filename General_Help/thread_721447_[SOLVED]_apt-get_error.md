---
title: "[SOLVED] apt-get error"
date: 2008-03-11
forum: General Help
---

### Post by meazz1 on 2008-03-11
when I try to run 
$sudo  apt-get update 

I am getting a 
"E: Malformed line 58 in source list /etc/apt/sources.list (URI parse)" 

When I open up the /etc/apt/source.lst, there is only 39 lines.

How, can I resolve this?

---

### Post by finferflu on 2008-03-11
Are you sure there are no blank lines? Try:

```
wc -l /etc/apt/sources.list
```
And see how many lines it counts.

---

### Post by meazz1 on 2008-03-11
Yes, are are some blank lines for sure.

I will check that once I get home.

---

### Post by Oldsoldier2003 on 2008-03-11
> **meazz1 said:**
> when I try to run 
$sudo  apt-get update 

I am getting a 
"E: Malformed line 58 in source list /etc/apt/sources.list (URI parse)" 

When I open up the /etc/apt/source.lst, there is only 39 lines.

How, can I resolve this?
some thoughts:
remove any extra whitespace and carriage returns in your sources.list.
post your sources.list so we can see if anything else in it may be causing this error.

remember you need to edit it under sudo or as root in order to save the file.

---

### Post by meazz1 on 2008-03-11
Thanks, I commented out the last line and problem went away.

---

