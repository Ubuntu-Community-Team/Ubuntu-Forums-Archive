---
title: "compiz consumes &gt; 100% of CPU power and causes OS to be unresponsive ?"
date: 2017-03-30
forum: General Help
---

### Post by aeid2 on 2017-03-30
I have been having this problem for a while and I can't deal with , don't know what to do , 
I use workspaces all over the place , but when I do so CPU spikes to more than 100% and OS 
goes unresponsive ... I have to go `alt-shift-f#' and `pkill -9 compiz' to make it unresponsive again
and when I do so I sometimes lose windows or workspace organization ! 

problem happens with '16.04' and '16.10' 

any idea why this is happ

---

### Post by deadflowr on 2017-03-30
> any idea why this is happ
You mean happening?
Maybe.
Strong possibility is that you do not have a proper gpu driver in use, so the system is running the graphics through the cpu via the llvmpipe driver.
Also possible it's a too weak gpu to begin with.

if possible try posting the output from
```
sudo lshw -C display
```

---

### Post by aeid2 on 2017-04-02
this is a screenshot of the output . 

[IMG]http://i.imgur.com/Bq5UxNs.png[/IMG]

---

