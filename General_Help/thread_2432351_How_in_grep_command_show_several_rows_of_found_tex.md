---
title: "How in grep command show several rows of found text ?"
date: 2019-12-01
forum: General Help
---

### Post by petrogromovo on 2019-12-01
Hello, 

under Kubuntu 18 when I need to search for some code I use command like:
```
grep -Hrn 'modalTaskAssignedToUserHeight()' --include="TaskDetails.vue*" /_diskE_Media/__Archieve/

```
and this command shows all found files in 1 line of code.
My question is if there is a way(parameter) to show found line and next several rows(3-5) of text?

Thanks!

---

### Post by sisco311 on 2019-12-01
```
grep -A 3 ...
```
See:
```
man grep | less +'/^ +Context Line Control'
```

---

### Post by TheFu on 2019-12-01
Some different solutions, not all grep based:
```
lspci -vk |egrep --after-context=8 'Ethernet|Network'
lspci -vk |perl -lne 'print if /Ethernet|Network/ .. /^[\w]*$/'
```

8 is the number of lines displayed after the desired text is found in the egrep command.

The perl version looks for a line that doesn't have any characters, so if the input command going through the pipe outputs more or fewer lines, it will only show the stanza requested.

-A  is the same as -after-context= shown by sisco311.  I use the more general solution with perl almost always.
```

# video information
lspci -vk |perl -lne 'print if /VGA/ .. /^[\w]*$/'

# audio information
lspci -vk |perl -lne 'print if /Audio/ .. /^[\w]*$/'

```

---

