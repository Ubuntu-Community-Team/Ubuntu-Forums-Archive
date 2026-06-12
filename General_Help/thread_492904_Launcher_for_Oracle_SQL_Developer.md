---
title: "Launcher for Oracle SQL Developer"
date: 2007-07-05
forum: General Help
---

### Post by Grimly Fiendish on 2007-07-05
Hi,

As a complete Linux beginner (and loving Ubuntu so far!) I have what is probably a very easy/stupid question.

I've installed Oracle XE (absolutely no probs) and Oracle SQL Developer (again, easy).

In Terminal I can run SQL Developer by navigating to sqldeveloper_install/sqldeveloper/  and typing "sh sqldeveloper.sh"

I get the following and the app launched fine...

Oracle SQL Developer
 Copyright (c) 2006, 2007, Oracle. All rights reserved.  

Using oracle.home=/sqldeveloper_install/sqldeveloper
Using ide.user.dir=/home/mike/.sqldeveloper


What I want to do is create a Launcher to launch the above...

I've created a Launcher with the following command text 

"/sqldeveloper_install/sqldeveloper/sqldeveloper.sh"

but when I try to run it I get...

Details: Failed to execute child process "/sqldeveloper_install/sqldeveloper/sqldeveloper.sh" (Permission denied)

It's obviously(?) something to do with user permissions but as a hardened Windows (i.e. always admin) user I'm at a complete loss...

Sorry about lengthy post and any help gratefully accepted...

Thanks in advance...

---

### Post by kuja on 2007-07-05
Try setting the option for "run command in terminal" or similar, and use sh before the path as you did before (ie: sh /sqldeveloper_install/sqldeveloper/sqldeveloper.sh)

---

### Post by Grimly Fiendish on 2007-07-05
Hi,

"sh /sqldeveloper_install/sqldeveloper/sqldeveloper.sh" did the trick...

Should have figured it out really...

Many thanks

---

