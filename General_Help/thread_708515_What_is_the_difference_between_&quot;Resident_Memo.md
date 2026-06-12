---
title: "What is the difference between &quot;Resident Memory&quot; and &quot;Memory&quot; columns"
date: 2008-02-26
forum: General Help
---

### Post by chandru.in on 2008-02-26
Hi,

In Gnome's system monitor, there are two columns namely "Resident Memory" and "Memory".

I'm able to understand "Resident Memory" as it displays the same info as the "rss" field of "ps" command.

The value displayed in "Memory" column is almost always less than that in the "Resident Memory" column.  What exactly does this column show?  Also, what is the command-line equivalent to get the info in this column of system monitor?

---

### Post by plucky on 2008-02-26
> The value displayed in "Memory" column is almost always less than that in the "Resident Memory" column


Open system monitor and navigate to Help file contents and select preferences.This gives an explanation of each column.

> what is the command-line equivalent to get the info in this column of system monitor?
```
top
```

I think is what you want.

Good luck

---

### Post by chandru.in on 2008-02-27
Yes I looked into those help topics before posting.

I did get a vague idea.  I wanted to know how exactly it works.

Also, "top" and "ps" commands give percentage of memory used, Resident memory, etc.  I have not been able to find any field which corresponds to the value displayed in the "Memory" column of Gnome system monitor.

If I'm missing something, please tell me which field of top/ps I'm supposed to look at.

---

