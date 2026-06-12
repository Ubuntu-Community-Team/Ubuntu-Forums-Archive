---
title: "Linux Process Accounting Solution?"
date: 2013-03-28
forum: General Help
---

### Post by Kirk Schnable on 2013-03-28
Good morning everyone,

I am managing a deployment of about 800 Ubuntu-powered client computers.  All of these have a GUI (most are Xubuntu, those that aren't will be soon).  They are used by non-technical end users, many of whom have no administrative access to the computer.

We manage software on the computers using Puppet.  We are working hard behind the scenes to keep relevant software working smoothly, including some legacy software applications we are running in WINE, etc.

We would like to have a way to find out how often our managed software is being used, so we can prioritize updates, and eventually phase out legacy software that is no longer being used.



We have pondered making a custom launcher for our custom software solutions, and having it use curl to report to a Web API on one of our servers.  The obvious problem with this being the unnecessary overhead, and consideration that most of our clients are mobile and may not always be online.


This led me to ask whether there was a "process analytics" or "process accounting" system for Linux.  Something which could tell us how many times a process started, or even simply "how many hours did they run Google Chrome?" etc.  This could be in the form of a loadable kernel module, as we are planning on incorporating the solution into our new image and we will have an opportunity to add those things now easily.

Obviously a full-blown solution for all processes would be beyond what we need.... but it is not beyond what we are willing to implement.  Whatever we do implement will need to report to a central database server.

Any feedback from the community would be greatly appreciated!

Kirk

---

### Post by Mike_Schmidt on 2013-08-25
I haven't done the appropriate testing to determine whether the "acct" solution will give you the information you need. It is the closest thing I've seen to what you are looking for, though.

See [http://www.shibuvarkala.com/2009/04/howto-enable-process-accounting-in.html](http://www.shibuvarkala.com/2009/04/howto-enable-process-accounting-in.html) first. Then you may want to determine whether you simply upload the log file periodically and interpret it on the server, or whether you want to run the acct command periodically, dumping its output to the server. Perhaps you may even poll periodically and send those logs to the server for interpretation.

Best of luck!

---

