---
title: "The issues on superviorstl ERROR (spawn error) ubuntu system"
date: 2022-01-05
forum: General Help
---

### Post by teretdfl on 2022-01-05
Good morning,I have problem in my ubunbu system,L login in tne linux command line,I cannot restart for the application, The system show "ERROR (spawn error)",And I cannot read the application .log  in the system"Not such file ",  how to find the error location and fixed the problem, and restart the application series ,Can you help???thank you

---

### Post by QIII on 2022-01-05
Which release of Ubuntu are you using?

What is the application "money"?

---

### Post by teretdfl on 2022-01-05
This about the application for this....

---

### Post by QIII on 2022-01-05
What operating system are you using?

---

### Post by teretdfl on 2022-01-05
The [COLOR=#000000] ubuntu  server 20.04 [/COLOR]

---

### Post by QIII on 2022-01-05
Is this on the Windows Subsystem for Linux?

Your image above includes references to .exe and .dll files, both of which are foreign to Linux.

---

### Post by teretdfl on 2022-01-05
help you help ??? how to find the support to fixed problem?????

---

### Post by teretdfl on 2022-01-05
Iam use the SSH remote to system in XSHELL 7.0

---

### Post by QIII on 2022-01-05
Please specify the other OS.  Are you using SSH between two Ubuntu machines?  Ubuntu to Windows?  Windows to Ubuntu?

It is impossible to help until the problem is understood.

---

### Post by teretdfl on 2022-01-05
I am [COLOR=#000000]Windows to Ubuntu in SSH remote,but cannot find the application settings to reset .[/COLOR]

---

### Post by QIII on 2022-01-05
The application settings for "money"?

---

### Post by The Cog on 2022-01-05
You really need to find the log file. I see there is a config folder - see if any of the files in there say where the log will be written. Also there is a pair of log4cplus.config* files that may contain logging configuration. Read those as well.

---

### Post by teretdfl on 2022-01-05
What is the command for read the log file ????????

---

### Post by QIII on 2022-01-05
Hold on a minute and calm down.  We are trying to help.  It is not likely anyone is going to have a step by step solution for you.

The log would be valuable,  but we may not be able to tell you where it is.  It is possible nobody is familiar with that application.  Such logs are often in /var/log. syslog may have some information.

Let's try something really quick.  What happens if you run money from the command line?  Any messages?  Could you post them.

---

### Post by teretdfl on 2022-01-05
See image

---

### Post by QIII on 2022-01-05
```
restart money
```

may not be a well-formed command, and it may not "restart".

Try just

```
money
```

or you may need to add the full path and name, perhaps:

```
/usr/bin/money
```

If it takes elevated privileges, use sudo

---

### Post by teretdfl on 2022-01-05
command not reponed

---

### Post by QIII on 2022-01-05
A couple of times there I see incorrect password.

OK.  Does that app normally start from a script?  What syntax is  used there?

---

### Post by schragge on 2022-01-05
Please show the results of (from inside the **supervisorctl** shell)
```
tail money
```
and
```
tail money stderr
```
According to [docs]("http://supervisord.org/running.html#running-supervisorctl"), it should print the last 1600 bytes of **money**'s stdout and stderr, respectively.

---

### Post by teretdfl on 2022-01-05
Have many message!


[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289737&stc=1[/IMG]

---

### Post by teretdfl on 2022-01-12
Have any idea???

---

