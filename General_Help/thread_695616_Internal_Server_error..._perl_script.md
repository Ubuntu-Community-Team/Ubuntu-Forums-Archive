---
title: "Internal Server error... perl script"
date: 2008-02-13
forum: General Help
---

### Post by tiger.woods on 2008-02-13
I'm trying to setup Turbo Tourney for the upcoming season and am running into a problem executing the script.

[B][I]Internal Server Error

The server encountered an internal error or misconfiguration and was unable to complete your request.

Please contact the server administrator, [email]admin@myweb.com[/email] and inform them of the time the error occurred, and anything you might have done that may have caused the error.

More information about this error may be available in the server error log.[/I][/B]

This is from the log file:

[B][I][Thu Feb 07 21:11:21 2008] [error] [client 192.168.2.1] (8)Exec format error: exec of '/home/ncaa.myweb.com/cgi-bin/pickentry.pl' failed, referer: [http://ncaa.myweb.com/tournamententry.html](http://ncaa.myweb.com/tournamententry.html)
[Thu Feb 07 21:11:21 2008] [error] [client 192.168.2.1] Premature end of script headers: pickentry.pl, referer: [http://ncaa.myweb.com/tournamententry.html](http://ncaa.myweb.com/tournamententry.html)[/I][/B]

I created a scipt in the /cgi-bin directory and was able to execute it from the CL so I think the Perl script is being executed correctly but after that I'm a bit lost.

I'm hoping someone has seen this before and can give me some guidance or has some ideas on how to fix.

Thanks,

---

