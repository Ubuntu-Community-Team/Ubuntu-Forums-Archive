---
title: "How to track and log error from a running app?"
date: 2020-05-23
forum: General Help
---

### Post by chrisnk on 2020-05-23
Hi!
Im interested in a solution how to save a log file with error report from an app what Im running on Ubuntu/Lubuntu.

Lets say I use Nano and for any reason Nano run into a trouble and crash or give an error msg on the screen.

Is there a way to save this msg for later investigation or so?

I have running an app on my pc for syncing files on my net. And sometime an error pop up cos of some folder was deleted etc. and the app ignores this err but I would like to have a log about this. The app has no in-built option to log such of problem.

Thank you.

---

### Post by ajgreeny on 2020-05-23
So where do you see this error?  

If an error message pops up on your screen it must come either from the application running into the problem or some other background utility that is used by the application.
What is this application?

---

### Post by Impavidus on 2020-05-23
If an application writes error messages to stderr, you could try redirecting stderr to a file:```
command 2>error.log
```

---

### Post by lvm on 2020-05-23
Usually program writes errors, warning and other messages to console, in order to see them you should start it either from a terminal or from a script redirecting stderr to a log file '<program> >> <logfile> 2>&1'.

---

### Post by TheFu on 2020-05-23
If the programmer wanted, they can write errors to syslog or any other log file they choose.  This is pretty common, unless they came from a different OS and didn't learn to program the Unix way.  There are tools/libraries to make outputing to the syslog easy.  Where I worked programming, our systems were fairly large, so we had dedicated logs that were written to a specific log directory just for our apps, and n-tier servers.  We setup debug levels in the config files so the clients could control what was logged.  Level 5 would log enough that the files would tell a developer exactly which functions/methods were hit, in order, effectively providing a stack trace for the code path taken.  Level 1 would only log errors.  Our logging was so good that we could have the client turn up the level to 5, cause an issue, email us the logs, and we'd be able to determine what the problem was usually in just a few minutes.  Other places I've worked did the same thing.  It always amazes me when a non-trivial program doesn't have this capability.  

Developers are famous for saying they can't reproduce some issue. Good logging removes that problem. You don't need to reproduce it when you know exactly what code it throwing every error, assuming the code checks every return value. They should, BTW.

---

