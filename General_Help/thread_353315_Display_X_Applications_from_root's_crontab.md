---
title: "Display X Applications from root's crontab"
date: 2007-02-04
forum: General Help
---

### Post by sumadartsan on 2007-02-04
I have a script I need to run as root that I added to root's crontab.  I would like an xterm window to pop up and tell me what's going on.  So I added this command: ```
export DISPLAY=:0.0 && xterm -hold -e 'myscript.sh'
``` to crontab.  That command does not run and I get the following error message recorded in my logs: 

"Warning: This program is an suid-root program or is being run by the root user. The full text of the error or warning message cannot be safely formatted in this environment. You may get a more descriptive message by running the program as a non-root user or by removing the suid bit on the executable. xterm Xt error: Can't open display: %s"

 I've searched through the forums about how to get GUI applications to work in crontab and have found several on how for the regular user's crontab. However, I haven't been able to find any on how to get them to work through the root's crontab.  How would I go about doing this?

---

### Post by schilcha on 2007-02-04
Sorry, cannot answer your question, since I really cant put any meaning into the warning-message you posted. 

To state the obvious: did you make sure to allow incoming X-connection with xhost? Also, this is by default disabled in ubuntu -- you need to reconfigure the x-server to accept tcp-connection. And even if, I'm not 100% sure, if that'd work (though it might be worth a try). 

But, what I can suggest is to add the script to your own crontab like this:
```

xterm -hole -e 'sudo myscript.sh'

```
In this case, you can use the threads on how to launch x-apps from a regular user's crontab. The only thing you need to take care of is that myscript.sh can be run via sudo without entering a password. This can be done by adding a line like the following to your sudoers-file:
```

schilcha  smithers = NOPASSWD: /sbin/poweroff

```
substitute "schilcha" with your username, "smithers" with your hostname and "/sbin/poweroff" with the path-and-file-name of myscript.sh.

!!!Make sure to user the command "visudo" to edit the sudoers-file!!!

Hope this helps.

---

