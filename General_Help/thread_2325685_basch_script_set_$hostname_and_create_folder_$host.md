---
title: "basch script set $hostname and create folder $hostname after remote login with ssh"
date: 2016-05-24
forum: General Help
---

### Post by tellme-a on 2016-05-24
Hi,can't manage to script setting environment $hostname from logged in computer then ssh without Password Using ssh-keygen to remote computer
after that i want to create a dir with $hostname variabele

this is my script so far:

#!/bin/sh

BACKUPDIR=/backup/$(hostname)
ssh admin@remotesystem
mkdir -p $BACKUPDIR
exit

I get no error message but directory is not created.
When i do it step by step manual and i do ssh admin@remotesystem i log in to the remote system.
If i then echo $BACKUPDIR i have no result, the variabele is lost after remote login.
Is there an option to create automatic my original $hostname dir after login to remote system ?

Thanks for all input
Tellme

---

### Post by bab1 on 2016-05-24
> **tellme-a said:**
> Hi,can't manage to script setting environment $hostname from logged in computer then ssh without Password Using ssh-keygen to remote computer
after that i want to create a dir with $hostname variabele

this is my script so far:

#!/bin/sh

BACKUPDIR=/backup/$(hostname)
ssh admin@remotesystem
mkdir -p $BACKUPDIR
exit

I get no error message but directory is not created.
When i do it step by step manual and i do ssh admin@remotesystem i log in to the remote system.
If i then echo $BACKUPDIR i have no result, the variabele is lost after remote login.
Is there an option to create automatic my original $hostname dir after login to remote system ?

Thanks for all input
Tellme
I assume you mean BASH script.  The shebang line should be```
#!/bin/bash
```...what you have is really DASH and might not have the results you ultimately want.  But that is not really your problem.

When ever you log into an environment (desktop, terminal or ssh) you are in a separate shell.  The environment variables do not carry over.   You can see this when you compare your terminal shell prompt with the ssh shell prompt.  You should see something like this```
user@[COLOR="#0000CD"]localhost[/COLOR]
user@[COLOR="#ff0000"]remotehost[/COLOR]
```
You need to set the variables and run the script both from the remote host.

---

### Post by nerdtron on 2016-05-25
Aside from the /bin/bash stated by bab1 above, bash scripts are executed line per line on the local machine, not on the remote machine.
Therefore, your mkdir command which is on a new line will not be executed on the remote machine.

If you want to execute commands to the remote machine via ssh, you'll need to "feed" your commands to the ssh line. Like this:
```

#!/bin/bash

BACKUPDIR=/backup/$(hostname)
ssh admin@remotesystem "mkdir -p $BACKUPDIR"
exit

```

---

### Post by tellme-a on 2016-05-25
Thx [**[COLOR=#000000]bab1[/COLOR]**]("http://ubuntuforums.org/member.php?u=582150")and [**[COLOR=#C61919][B]nerdtron**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=895543") !!! Thanks also for explanation, it was the **#!/bin/bash** now its working like a charm !!
Thanks for your input, i learned something and now i am happy :popcorn:

---

