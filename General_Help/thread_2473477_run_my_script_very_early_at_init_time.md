---
title: "run my script very early at init time"
date: 2022-04-05
forum: General Help
---

### Post by Skaperen on 2022-04-05
i want to run my script very early at init time.  it's purpose is to modify PATH in a way intended to affect most, if not all, of the init steps.  what i am hoping to do is find how this new init stuff gets started and swap that executable to get my script started, which will do its thing and then exec the executable that was renamed.  any suggestions?

---

### Post by colin-i on 2022-04-05
1. You can copy to etc:
sudo cp --interactive ./script /etc/init.d/
sudo ln -s /etc/init.d/script /etc/rc5.d/S01script

2. Use "Startup Applications" application?

3. For a terminal launch there is ~/.bashrc file for commands.

---

### Post by Skaperen on 2022-04-06
it needs to be run in place of (but it will run that next) something before even that.  maybe it is better explained this way.  every process left running after system initialization is all done must descend from the (no longer running) process that ran my script.  it may need to replace or modify whatever sets PATH so that every process inherits that PATH value.  do you know where and when PATH first gets set?

---

### Post by colin-i on 2022-04-08
Maybe this file?
```

cat /etc/environment
#PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin"

```

---

### Post by Skaperen on 2022-04-09
when does **/etc/environment** get read in to set the environment?  my script would need to run before then.

if my script is run as **[FONT=courier new]/etc/rc5.d/S01script[/FONT]** then it would not be able to set PATH for other scripts.

---

