---
title: "shell logging"
date: 2013-08-16
forum: General Help
---

### Post by chakri78 on 2013-08-16
Could you please suggest a tool or a procedure for shell logging. I would like to capture all the shell activity for all the users including root for all the shells ( bash, sh, ksh ....)

Thanks,

---

### Post by Lars Noodén on 2013-08-16
I would look at using [script](http://manpages.ubuntu.com/manpages/raring/en/man1/script.1.html) in some capacity.  What problem are you trying to solve?

---

### Post by tgalati4 on 2013-08-16
You could write a cronjob to capture .bash_history for each user.  You would need to set an environment variable to get time stamps in the history file.  Root actions are stored in /var/log/auth.log.

If you can elaborate on your specific use case, then there are probably better methods.  What are you trying to do?

---

### Post by chakri78 on 2013-08-16
I would like to have all the commands executed by the users in bash shell in a single file for monitoring purpose. 

Thanks,

---

### Post by Lars Noodén on 2013-08-16
If you use the bash history, you should look at setting the 'shopt -s histappend' and 'cmdhist' options so that multiple sessions can be recorded concurrently and in a coherent manner.  

However, even with script, mentioned above, you are still going to be depending on the cooperation from the shell users.  The users will still be able to erase or edit the history file or the script log.  If you need something more hostile, then maybe the package auditd might have something, but I haven't used it.

---

### Post by chakri78 on 2013-08-21
Thanks for the suggestions.

---

