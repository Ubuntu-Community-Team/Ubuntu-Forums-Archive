---
title: "Dates in xubuntu xfce desktop in spanish."
date: 2014-04-15
forum: General Help
---

### Post by jaym292 on 2014-04-15
All dates for everything such as last modified dates, the calendar and such are in Spanish. How do I make it english?

---

### Post by davea42 on 2014-04-16
Type the command 
```
locale
```
and if it does not say

LC_TIME="en_US.UTF-8" 
(it might not, I don't know where you are) then try a query
in your browser on setting the locale in Ubuntu. 
One
candidate browser query is
```
ubuntu locale date format
```
but other similar will be as good.

Another command to try in a terminal window is 
```
printenv
```
and look for surprising language settings in the output.

---

