---
title: "Minimal path in terminal?"
date: 2007-08-31
forum: General Help
---

### Post by dxmosiris on 2007-08-31
I know this has probably been discussed before, but I have no idea what to search for pertaining to this issue. 

I would like my terminals to only show the current working directory like in red hat/fedora distros such has user@dir instead of user@dir/dir/dir/dir/dir.

Thanks in advance =]

---

### Post by yabbadabbadont on 2007-08-31
```
/home/daffy $ echo $PS1
$PWD $
/home/daffy $ export PS1='\w $ '
~ $ cd temp
~/temp $ cd /tmp
/tmp $ 
```
Is that what you wanted?

Edit: or more like this:
```
/home/daffy $ export PS1='\u@\w $ '
daffy@~ $ cd /tmp
daffy@/tmp $ 
```

---

### Post by Milk &amp; Toast &amp; Honey on 2007-08-31
This is my setting, put this line in the end of your /home/yourname/.bashrc file.
```

PS1="\u@\h \W > "

```

---

### Post by Milk &amp; Toast &amp; Honey on 2007-08-31
> **yabbadabbadont said:**
> ```
/home/daffy $ echo $PS1
$PWD $
/home/daffy $ export PS1='\w $ '
~ $ cd temp
~/temp $ cd /tmp
/tmp $ 
```
Is that what you wanted?

Edit: or more like this:
```
/home/daffy $ export PS1='\u@\w $ '
daffy@~ $ cd /tmp
daffy@/tmp $ 
```

Ouch... you got me couple second earlier.

---

### Post by dxmosiris on 2007-09-01
Excellent. These choices work like a charm. Now I can further edit my bashrc to how I would like it. Thanks for the quick response, I appreciate it.

---

