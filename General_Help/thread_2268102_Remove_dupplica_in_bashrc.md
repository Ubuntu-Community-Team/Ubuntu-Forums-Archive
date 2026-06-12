---
title: "Remove dupplica in bashrc"
date: 2015-03-06
forum: General Help
---

### Post by CkDGTAT on 2015-03-06
Hi,

Supposed I have 2 functions defined in my ~/.bashrc:

```
function myfunction(){

content1

}

...

function myfunction(){

content2

}

```

I want to remove the first definition, that is 

```

function myfunction(){

content1

}
```

and keep the other one. My ~/.bashrc is 10.000 lines long and need to do it recursively.

---

### Post by ajgreeny on 2015-03-06
> My ~/.bashrc is 10.000 lines long and need to do it recursively. 						Wow, that is a heck of a .bashrc file; do your two functions in there add all those lines to it or have you added lots of extra things to the file.

Mine is 118 lines long, and I have added several lines to it, so yours is a huge edit from the default.

However, what do you mean by your comment about needing to do it recursively?  It is just a single file so I don't understand how you can do anything recursively to it.

---

