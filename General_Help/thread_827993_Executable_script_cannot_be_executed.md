---
title: "Executable script cannot be executed"
date: 2008-06-13
forum: General Help
---

### Post by volmark on 2008-06-13
I’ve created simple script file for restarting an interface and made it executable (-rwxrwxr--). The script contains only one line: sudo /etc/init.d/networking restart.
When I’m trying to execute the script the following line coming up: -bash: netrestart: command not found
What’s wrong???

---

### Post by Gerlads Mod on 2008-06-13
Your script should look something like:
```

#!/bin/bash
cd /etc/init.d
sudo networking restart
exit 0

```

---

### Post by ilrudie on 2008-06-13
> **volmark said:**
> I&#8217;ve created simple script file for restarting an interface and made it executable (-rwxrwxr--). The script contains only one line: sudo /etc/init.d/networking restart.
When I&#8217;m trying to execute the script the following line coming up: -bash: netrestart: command not found
What&#8217;s wrong???


You need to specify a path.  In your case it will be ./netrestart if you are in the folder that contains your script.  Otherwise it looks in the folders in your PATH environment variable for your script, doesn't find the script and then says it can't find it.

Also you could add the folder your script is in to your path variable.

---

### Post by Gerlads Mod on 2008-06-13
Yes he's right.
It should look like this:
```

#!/bin/bash
cd /etc/init.d
sudo ./networking restart
exit 0

```

---

### Post by joshsmith on 2008-06-13
your script is fine
the problem is in your running it

if you want to run a program in the current directory you use ./
so you want
./netrestart
if you are in the same directory as your script.
or
/home/yourname/rest_of_path/netrestart

---

