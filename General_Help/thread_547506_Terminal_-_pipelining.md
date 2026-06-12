---
title: "Terminal - pipelining"
date: 2007-09-10
forum: General Help
---

### Post by jsiii on 2007-09-10
Hello,

I have problem like this: I need to download a file with wget and store it as a file with actual date in the name.

How to write the command?

I have something like this: wget [www.foo.com](www.foo.com) -O tmp/date.html

But I actually want to replace date.html with the output of "date" command. Any suggestion?

Thanks

---

### Post by McNils on 2007-09-10
```
wget www.foo.com -O tmp/`date +%Y%m%d`.html
```

Using backquotes, or wathever they are called, is a simple way of doing it.

---

