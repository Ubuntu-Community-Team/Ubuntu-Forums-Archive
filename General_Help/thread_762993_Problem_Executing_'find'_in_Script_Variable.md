---
title: "Problem Executing 'find' in Script Variable"
date: 2008-04-22
forum: General Help
---

### Post by jbulcher on 2008-04-22
Hi,

I'm having a bit of trouble with a shell script. I need to execute a find command from a variable, but for some reason it is taking quotes literally:

```
#!/bin/sh
cmd="find ./ -type f ! -name ".sh"
$cmd
```

will exclude '".sh"' but not '.sh'. What can I do about this? This really has me stumped.

---

### Post by gsmanners on 2008-04-22
You need to put the command in backward single quotes, like this:

cmd=`find`

---

### Post by jbulcher on 2008-04-22
I'm not trying to capture the output of the command though - I'm just trying to store the command in a variable and execute it later. Unless I'm mistaken, the way you put it would run during the declaration of the variable, correct?

Thanks for your reply!

---

