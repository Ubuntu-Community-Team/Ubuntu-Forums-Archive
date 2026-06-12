---
title: "Script only works when run in terminal"
date: 2016-03-12
forum: General Help
---

### Post by piphclyd on 2016-03-12
When I run ```
python3 /path/to/script.py
``` in a terminal window, the script runs properly. However, when I run the exact same command through a system call from another application (without a terminal window), it fails to run. 

To be more specific, the other application is a pyqt GUI that runs various other scripts through the python function subprocess.Popen(). For some reason, I have this one specific python script that won't run that way, even though it will run in a terminal window. All my other scripts run find both ways (through subprocess.Popen() and in a terminal window). What could be different about running a python script in terminal versus through a system call?

---

### Post by papibe on 2016-03-12
Hi daylinlt.

Is it interactive? Does it print to the standard output? 

Could you post the content of the script?

A couple of ideas:

I have used python's subprocess.call(), and I make sure all is redirected. For instance:
```

fp = open('/dev/null', 'wb')   # file to redirect output
         
call(cmd, stdin=None, stdout=fp, stderr=fp, shell=False)
```

I also have success running shell and python scripts inside a GNU screen, or a tmux session.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by piphclyd on 2016-03-12
Yes, it is interactive. Is that causing the problem? It calls a shell script that tries to run /usr/bin/expect. It looks like this:
```

#!/usr/bin/expect -f
spawn scp -r "user@user.com:/path/" "/path/to/local/folder"
expect {
  -re ".*es.*o.*" {
    exp_send "yes\r"
    exp_continue
  }
  -re "password" {
    exp_send "password\r"
  }
}
interact
```

---

### Post by papibe on 2016-03-12
I see.

I usually use full paths when not sure if the PATH is available to the script:
```
spawn /usr/bin/scp ...
```
Also, try replacing the 'interact' command with a eof/exit instead (so no shell is used):
```
expect eof
exit
```
Let us know how that goes.
Regards.

---

### Post by piphclyd on 2016-03-12
Replacing interact with expect eof/exit worked. Thanks for your help! I'm trying to make sense of why it only worked in a terminal window before. Does the 'interact' command require a shell to work?

---

