---
title: "Getting a program to work"
date: 2007-02-05
forum: General Help
---

### Post by bdmp on 2007-02-05
I am trying to get a program working, but I am getting this error  

burepe@pikapika:/opt/dmak$ ./dmak
Error opening terminal: xterm.

The directions say to do this but I am not sure how to do it exactly. Can someone explain how to do this?

Debian Linux seems to be a special case.
Add:  export TERM=ansi to .bashrc (or however you set up your environment)

Any help would be appreciated.

Thanks.

---

### Post by majoridiot on 2007-02-05
if you are running dapper, then open a terminal and:

```
gedit ~/.bashrc
```

and then add the **export TERM=ansi** line to the end of the file, save it and try to run
your application again.

---

