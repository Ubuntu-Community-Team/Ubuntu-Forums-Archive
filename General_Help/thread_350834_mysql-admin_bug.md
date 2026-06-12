---
title: "mysql-admin bug?"
date: 2007-02-01
forum: General Help
---

### Post by antiwindows798 on 2007-02-01
I have a 64 bit computer. mysql-admin works fine, but when I want to go to the users section, mysql-admin freezes. What's up with that?

Any ideas?

---

### Post by antiwindows798 on 2007-02-06
Hello?

---

### Post by antiwindows798 on 2007-02-07
Nobody here uses MySQL????

---

### Post by bullines on 2007-02-07
I have the exact same problem, and haven't found a fix for it.  I know it doesn't help solve the problem, but at least you're not alone :)

---

### Post by antiwindows798 on 2007-02-07
> **bullines said:**
> I have the exact same problem, and haven't found a fix for it.  I know it doesn't help solve the problem, but at least you're not alone :)

No, I'm glad you replied, indeed, at least I know that I'm not alone :), lol.

---

### Post by jural on 2007-02-12
Until this morning this was the workaround:
in a console:
export DEBUG_DONT_SPAWN_FETCHES=1 && mysql-admin

Unfortunately I updated this morn, and now mysql-admin  simply dosen't find the user information. Ubuntu is becoming extremely annoying very fast. Without the work around  mysql-admin crashes on the users screen.

I'll post when I get the solution.

---

### Post by Synapse56 on 2007-02-12
> **antiwindows798 said:**
> I have a 64 bit computer. mysql-admin works fine, but when I want to go to the users section, mysql-admin freezes. What's up with that?

Any ideas?

Hi,

You're not alone - MySQL admin freezes for me on the users section and I'm running 32bit Ubuntu (latest version, can't remember the daft name)

---

### Post by bobfrommarketing on 2007-02-16
Well the export DEBUG_DONT_SPAWN_FETCHES=1 && mysql-admin fix doesn't refresh the user list, but users created in a session are stored and saved in the server, so it's still a decent way to put users into your database.

---

### Post by sylvester_0 on 2007-02-16
I know I'm not contributing anything but...Have you looked at the bug tracker and found the bug? If not have you filed one? Feisty is still in development and it's expected that there will be problems. If you want stable, use Dapper or Edgy.

---

### Post by hl2040 on 2007-02-26
The export isn't strictly necessary, I think. If you say $VAR=1 COMMAND, then the environment variable VAR is only added to the list of environment variables passed to the newly executed program. The export saves it into you running shell's list of environment variables for all subsequent program executions, until removed.

---

### Post by wantime on 2007-02-26
I get the same problem - frozen mysql-admin in the User Administration area.  I don't get the solution of hl2040 but find that bobfrommarketing is onto something.  Interested if anyone else knows more on this subject.

---

### Post by hl2040 on 2007-02-26
what I meant was that the export and the && aren't necessary. The export will always succeed, so && is pointless - && is nice if you don't want the second command to run if the first (before the &&) fails such as 

```
% cd /home/user/Desktop/Trash && rm -rf 
```

You definitely don't want rm -rf to run anywhere; you only want it to run when you have successfully CD'd into your Trash folder.

For the mysql thing; what causes mysql-admin to stop crashing and thus fixes the problem for me is the following command:

```
$DEBUG_DONT_SPAWN_FETCHES=1 mysql-admin
```

This will call mysql-admin, and when it begins executing, it gets a copy of all your shell environment variables. As a one-time effect, because it was prepended to the command, DEBUG_DONT_SPAWN_FETCHES will also be one of those environment variables passed to mysql-admin. Subsequent invocations of mysql-admin would not be passed that environment variable because the shell (bash by default in Ubuntu) behavior is defined that way. To make a variable stick as an "environment variable", use export before the assignment:

```
#export DEBUG_DONT_SPAWN_FETCHES=1 mysql-admin
```

and all subsequent invocations of mysql-admin from the shell instance you ran the 'export' from will know about DEBUG_DONT_SPAWN_FETCHES and the value you chose for it because it was added to the list of environment variables.

---

### Post by wantime on 2007-02-27
OK that makes sense now.  Two things though, one is how did you know to use that variable??? and the other is do you know where I can see a list of all the environment variables on my system (Edgy)?

---

