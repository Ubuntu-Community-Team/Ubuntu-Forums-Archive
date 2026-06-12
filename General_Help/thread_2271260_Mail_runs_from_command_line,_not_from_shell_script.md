---
title: "Mail runs from command line, not from shell script"
date: 2015-03-28
forum: General Help
---

### Post by Rocket J Squirrel on 2015-03-28
Linux version 3.16.0-31-generic (buildd@lamiak) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) 

I'm using msmtp with msmtp-mta. 

This works from the command line:

```
free -m | mail -s "mem" myemail@myemail.com

```

But if run from inside a shell script, such as i.e.,

```
#!/bin/bash
free -m | mail -s "test from script" myemail@myemail.com

```

I get:

```
$chkmem.sh
mail: cannot send message: Process exited with a non-zero status

```

and no email comes through. 

Looking at the tail of /var/log/msmtp/msmtp.log I see the successful sends and the unsuccessful sends:

Successful send from command line:

```
Mar 16 08:18:00 host=mysmtphost.com tls=off auth=on user=emailaccountname@company.org from=emailaccountname@company.org recipients=myemail@gmail.com mailsize=342 smtpstatus=250 smtpmsg='250 OK id=1YXWmo-0002Bt-9G' exitcode=EX_OK

```

Unsucessful send from within script:

```
Mar 16 08:19:35 host=mysmtphost.com tls=off auth=on user=emailaccountname@company.org from=LINUXUSERNAME@LINUXMACHINENAME recipients=myemail@gmail.com smtpstatus=550 smtpmsg='550-Verification failed for <LINUXUSERNAME>\n550-The mail server could not deliver mail to LINUXUSERNAME@LINUXMACHINENAME.  The account or domain may not exist, they may be blacklisted, or missing the proper dns entries.\n550 Sender verify failed' errormsg='recipient address myemail@gmail.com not accepted by the server' exitcode=EX_DATAERR

```

It appears that when sent from the script both "From:" and "To:" are different than when sent from the command line. The differences are in caps. 

The user executing the script and the owner of the script are the same. They are both "LINUXUSERNAME"

The script is in /home/LINUXUSERNAME/bin and that is where the command line example was run from.

Looking at the log, when the command is run successfully (directly from the commmand line), user=emailaccountname@company.org, and from=emailaccountname@company.org are as they appear in /etc/msmtprc:

```
# Set defaults.
defaults
account default
host mysmtphost.com
port 587
auth login
user emailaccountname@company.org
password PASSWORD
from emailaccountname@company.org
logfile /var/log/msmtp/msmtp.log
aliases /etc/aliases

```

But when run from the script, From: becomes "LINUXUSERNAME@LINUXMACHINENAME" instead of "emailaccountname@company.org" -- and I'm guessing the smtp host is rejecting the email. IOW, it looks like the script is not picking up the "from" from msmtprc.

I hope I have described the problem well enough!

---

### Post by TheFu on 2015-03-28
a) always specify full paths to every program used in scripts.
/usr/bin/mail
/usr/bin/free

b) I think the email address needs an escape before the '@' - emailaccountname\@company.org

c) do not trust any environment to be provided by cron - so if that is your final goal then HOME will not be set and the other environment variables will be minimal, not like a full login. 
I don't know anything about that MTA. Been using postfix for20 yrs.

---

### Post by Rocket J Squirrel on 2015-03-29
Thank you.

I changed the script to provide full path to /usr/bin/mail and to /usr/bin/free and the result is the same:

```
mail: cannot send message: Process exited with a non-zero status
```

Also tried escaping the "@" in the email address, no help. 

I really think the problem is that the environmental variables found in [COLOR=#000000]/etc/msmtprc are not getting passed on when mail is called from the script, whereas they do get picked up and passed on when the command is entered directly on the command line. This based on what I found in [/COLOR][COLOR=#000000] /var/log/msmtp/msmtp.log as described in my original post. 

[/COLOR]I'll worry about getting this working when called from cron once I get it working as a shell script.

---

### Post by TheFu on 2015-03-29
MTA interfaces through TCP - no environment variables are passed. In postfix, there is a relayhost setting in the main.conf. Does msmtp have something similar? It appears it isn't trying to send anything external at all.

When you run the script, are you logged in as the same userid as when typing the commands? If so, the shell (bash) environments should be inherited by the script.  Add "echo $HOME" to the end of the script to see that.

I'll do a little research on msmtp to see what might help. Give me a sec.

[http://msmtp.sourceforge.net/doc/msmtp.html#Environment-1](http://msmtp.sourceforge.net/doc/msmtp.html#Environment-1) - it appears you need to set the "SMTPSERVER" environment variable or get the host and account settings defined like their example config file [http://msmtp.sourceforge.net/doc/msmtprc.txt](http://msmtp.sourceforge.net/doc/msmtprc.txt) It is different from yours. Their "default" setting refers to other sections in the file. Their "user" setting refers to the userid on the remote system, not an email address. Of course, some SMTP servers use the email address as the userid - mine does - so that could be completely fine for your situation.

---

### Post by Rocket J Squirrel on 2015-03-29
Thank you.

I'm kind of fixated on the logged difference between a successful mail send (directly from the command line) and an unsucessful one (from the script).

Referring to the results found in /var/log/msmtp/msmtp.log, here is a key difference:

Successful send from command line shows this:

```
user=emailaccountname@company.org from=emailaccountname@company.org
```

Unsucessful send from within script shows this:

```
user=emailaccountname@company.org from=LINUXUSERNAME@LINUXMACHINENAME
```

In the case of the successful send, "from" gets picked up from /etc/msmtprc

In the case of the unsucceful send, "from" doesn't get picked up from /etc/msmtprc, resulting in:

```
smtpstatus=550 smtpmsg='550-Verification failed for <LINUXUSERNAME>\n550-The mail server could not deliver mail to LINUXUSERNAME@LINUXMACHINENAME.  The account or domain may not exist, they may be blacklisted, or missing the proper dns entries.\n550 Sender verify failed' errormsg='recipient address myemail@gmail.com not accepted by the server' exitcode=EX_DATAERR
```

The mail send was rejected by the smtp host because "LINUXUSERNAME@LINUXMACHINENAME" is not an account with it, whereas "emailaccountname@company.org" is an account. 

A side issue it that the documentation that you have helpfully provided links to (thank you!) is for msmtp 1.6.1, and I am running msmtp 1.4.31 -- I just ran apt-get update and apt-get dist-upgrade and 1.4.31 seems to be the latest in the repository.

---

### Post by TheFu on 2015-03-29
I'm guessing blindly here.  I would think it would work, but it is best to follow their example config file.

In theory, the current documentation for the version installed on your box is in the local manpage. **man msmtprc** would be my guess. Perhaps just msmtp?

Did you try setting the SMTPSERVER variable?

---

### Post by Rocket J Squirrel on 2015-03-29
Thank you.

I took a look in ~.bashrc and found a rather weird looking line:

```
alias mail='mail -aFrom:"emailaccountname@company.org"
```

which didn't look right. Googling about suggested that the "a" before "From" shouldn't be there. I removed it and tried the script again, no joy.

So I edited ~.bashrc again and added 

```
SMTPSERVER=mysmtphost.com
```

and tried the script again, still same error. 

```
man msmtp
```

Provides lots of interesting options, like setting the username with -user=username, but again, it works from the command line, but not from the script:

Command line works:

```
free -m | mail -user=emailaccountname@company.org -s "mem" myemail@myemail.com

```
Script does not:


```
#!/bin/bash
free -m | mail -user=emailaccountname@company.org -s "test from script" myemail@myemail.com

```
Gives the same error:


```
$chkmem.sh
mail: cannot send message: Process exited with a non-zero status

```

And the tail of /var/log/msmtp/msmtp.log shows that "from" when done from the command line is correct, but from the script is still not correct:

Successful send from command line:


```
user=emailaccountname@company.org from=emailaccountname@company.org

```
Unsucessful send from within script:


```
user=emailaccountname@company.org from=LINUXUSERNAME@LINUXMACHINENAME

```

I need a bigger hammer.

---

### Post by TheFu on 2015-03-30
Try [B]
export SMTPSERVER=mysmtphost.com[/B]
There is a difference.

---

### Post by Rocket J Squirrel on 2015-03-30
Thank you. I changed the line in ~.bashrc to

export SMTPSERVER=mysmtphost.com

and the same fail, with [COLOR=#000000]/var/log/msmtp/msmtp.log reporting that the smtp host rejected the message because "from" is still not correct. 

It should be [/COLOR]"emailaccountname@company.org" -- the value it gets when the command is run from the command line, but it's still becoming "LINUXUSERNAME@LINUXMACHINENAME" when run from the script. 

The smtp host recognizes "emailaccountname@company.org", but not "LINUXUSERNAME@LINUXMACHINENAME" and that's why the script-sending of the mail is failing. 

"emailaccountname@company.org" is found in /etc/msmtprc:

```
# Set defaults.
defaults
account default
host mysmtphost.com
port 587
auth login
user emailaccountname@company.org
password PASSWORD
from emailaccountname@company.org
logfile /var/log/msmtp/msmtp.log
aliases /etc/aliases


```

I can't see why everything BUT "user" is getting picked up when the command is run from within the script -- it gets the host and port right because the error found in /var/log/msmtp/msmtp.log says that the host rejects the mail because "LINUXUSERNAME@LINUXMACHINENAME" doesn't have an account on it. So clearly the mail is being created and sent -- it just doesn't have the right user name. But when the command is run from the command line, it goes through because "user" gets picked up.

---

### Post by TheFu on 2015-03-30
I don't have any more ideas. Sorry.
Just 
a) use their example config file
b) put it into ~/.msmtprc - not /etc/msmtprc

That's all I got.

---

### Post by SeijiSensei on 2015-03-30
I don't use this program, so this comment may be entirely erroneous, but mailers like sendmail do not allow ordinary users to specify the "envelope sender" without special authorization.  Root has this ability, but other users must be listed in a "trusted-users" file.

The envelope sender is the name used in the SMTP dialogue with the receiving server.  It need not, and often does not, match the "From:" line in the message body.  If you run the same command as root with sudo rather than as an ordinary user, does it use the correct envelope sender?

---

### Post by dcstar on 2015-04-05
The issue is possibly that when you run the /bin/bash shell you are implementing a different environment to the current shell that you are already in.

This should tell you what shell you are running in the command screen:
```
set | grep SHELL=
```

---

### Post by TheFu on 2015-04-05
> **dcstar said:**
> The issue is possibly that when you run the /bin/bash shell you are implementing a different environment to the current shell that you are already in.

This should tell you what shell you are running in the command screen:
```
set | grep SHELL=
```

True - ```

FOO=something
export FOO=something-else
```

The 1st one doesn't get passed to subshells.
The 2nd one does.

---

