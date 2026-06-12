---
title: "Bash Basics: Getting Demand in Path"
date: 2007-02-10
forum: General Help
---

### Post by Burgresso on 2007-02-10
I'm following this tutorial ([http://linuxcommand.org/wss0010.php]("http://linuxcommand.org/wss0010.php")) and I can't get bash commands to execute (in this example, it's the hello world). I've made sure over and over the permissions are correct, and I've even tried putting a . in front of the bin file in my home directory. 

myhome/bin/my_script and myhome/.bin/my_script don't do the trick, but when I put my_script in my home directory, it works with ./my_script.

Any ideas?

thanks
Burgresso

---

### Post by dcstar on 2007-02-10
> **Burgresso said:**
> I'm following this tutorial ([http://linuxcommand.org/wss0010.php]("http://linuxcommand.org/wss0010.php")) and I can't get bash commands to execute (in this example, it's the hello world). I've made sure over and over the permissions are correct, and I've even tried putting a . in front of the bin file in my home directory. 

**myhome/bin/my_script** and **myhome/.bin/my_script** don't do the trick, but when I put my_script in my home directory, it works with ./my_script.

Any ideas?

thanks
Burgresso

The highlighted commands are** relative**, which means that they probably won't run unless you are in your "/" directory when you try to run them, use an absolute reference:
```
/myhome/bin/my_script
``` instead.

---

