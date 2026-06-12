---
title: "Need help using cron with freefilesync"
date: 2013-02-06
forum: General Help
---

### Post by denywinarto on 2013-02-06
Hi, im trying to schedule sync job with cron, but apparently its not possible running it normal way, after searching around i found this solution 

sourceforge.net/p/freefilesync/discussion/847543/thread/85e38663/

Problem is, i dont understand the last part of the solution 

You must run "xhost +local:" from the session you want to run the display on. Xubuntu has the auto start program which is what I used for that.

Could someone help me understand this?
Im still new at ubuntu..
What exactly do i have to do?
Thanks

---

### Post by jonobr on 2013-02-06
Hi

Whenever your unsure of commands such as xhosts,

try the man pages

in a terminal window type man man

These are the man (help) pages for man

You can see what xhosts command does using 
man xhosts
Or you could search the web  [Here for example]("http://cf.ccmr.cornell.edu/cgi-bin/w3mman2html.cgi?xhost%281%29")

>        The  xhost program is used to add and delete host names or
       user names to the list allowed to make connections to  the
       X  server.  In the case of hosts, this provides a rudimen-
       tary form of privacy control and  security.   It  is  only
       sufficient  for  a  workstation (single user) environment,
       although it does limit  the  worst  abuses.   Environments
       which require more sophisticated measures should implement
       the user-based mechanism or use the hooks in the  protocol
       for passing other authentication data to the server.


Best of luck

---

