---
title: "Symbolic link with name replacement"
date: 2016-04-19
forum: General Help
---

### Post by legendbb on 2016-04-19
Don't understand the thing I am seeing.

Having an executable install /opt/app/executable
Tried creating a symbolic link in /usr/bin/name_other_than_executable by doing:
```
sudo ln -s /opt/app/executable /usr/bin/name_other_than_executable
```


My executable only runs if the symbolic link is created strictly as "executable", any name_other_than_executable will generate:
```
Error: cannot find /opt/app/name_other_than_executable
```

Is this system thing or executable thing?

Thanks for comments.

---

### Post by sisco311 on 2016-04-19
It's the job of the application to handle this correctly. Which application are we talking about?

---

### Post by legendbb on 2016-04-19
Thanks for attention. It's Mentor Graphics modelsim

---

### Post by sisco311 on 2016-04-20
I consider this a bug, so I think you should report it to  Mentor Graphics.

As a workaround you could use an alias or write a little script (which you can name whatever you want) and put it in /usr/local/bin:
```
#!/bin/sh

cd /opt/app || exit 1
./executable

```

---

### Post by mc4man on 2016-04-20
What are you gaining by not using the same name?

---

### Post by sisco311 on 2016-04-21
> **mc4man said:**
> What are you gaining by not using the same name?

Freedom  :) , or most likely, an app name which is shorter and/or easier to memorize.

And if/when  Mentor Graphics fixes this bug we will all gain the chance to buy and use a software which works in Linux as expected.

---

