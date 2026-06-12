---
title: "Evolution Memory Usage Problem"
date: 2005-04-28
forum: General Help
---

### Post by davidwfm on 2005-04-28
Hello to everyone in the forum, 

Up until the 5.04 release, i have always been a strict MS windows user (so consider me a very green newbie :-) ), and am Loving every minute of Ubuntu!

My current problem is that Evolution is using a huge amount of my memory. it uses about 115 MB for the Evolution process alone, and more for Exchange server, alarm notify and data server processes that are always working even if i close evolution. 
Note: i got this info from the System monitor and cannot cut-and-paste the info. 


Can anyone tell me what i can do to reduce Evolution's memory usage. Currently, it uses about 4 times what MS outlook used  - and that was ridiculous . 

Any help would be appreciated. 


David

---

### Post by doclivingston on 2005-04-28
When you're reading how much memory various processes are using, you have to make sure you're reading the correct value. The two most important ones are VM size, and RSS memory. The VM size (the bigger of the two) include all the shared libraries that an application uses, whereas RSS doesn't.

For Evolution the VM size will include the size of all the Gnome libraries that it uses. The memory for the shared libraries will be only used once, but they are reported as part of the VM size of all the application that use them.

---

### Post by davidwfm on 2005-04-28
Thanks for the tip. So essentially, you're saying that ~114MB of memory sounds reasonable?


David

---

### Post by doclivingston on 2005-04-29
The current uage of my Evolution-related process are

```
Name            VM      RSS
Evolution   241     67
E-D-S       138     4
E-A-N       64      4
```

If the VM size of Evolution is around 114M it shouldn't be too much of a problem.

One thing Evolution does is cache the messages that you have opened; if you quit and reload, it will purge the cache and free up some memory (If you're worried about how much it is using). After quitting and re-loading Evolution both it's VM and RSS size was about half of what it was before.

---

### Post by davidwfm on 2005-04-30
Thanks doclivingston

---

