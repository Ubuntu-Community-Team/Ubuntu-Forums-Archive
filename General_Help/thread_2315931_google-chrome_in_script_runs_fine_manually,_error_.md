---
title: "google-chrome in script runs fine manually, error from CRON"
date: 2016-03-03
forum: General Help
---

### Post by caughran on 2016-03-03
When Doonesbury started reruns and the Toronto Star dropped it, I created a kalarm command alarm to display it. Now I'm trying to get rid of kalarm, and thought I would transfer this and other things to cron. My batch runs fine manually, chrome exit code 0. When cron (or at) runs it, nothing displays in chrome, and the chrome exit code is 1. I know the batch runs because I sent output to a log, including the exit code.

[FONT=Courier New]/opt/google/chrome/google-chrome [http://www.uclick.com/client/sea/db/](http://www.uclick.com/client/sea/db/)[/FONT]

---

### Post by ajgreeny on 2016-03-03
Show us the full cron command you are using; cron accepts only a limited command syntax compared to bash and you may need to edit the command.

---

### Post by caughran on 2016-03-03
"Show us the full cron command you are using"

[FONT=Courier New]5 07  *   *   *     /home/jim/cronme/comics[/FONT]

I set it up with crontab.

---

### Post by ajgreeny on 2016-03-04
I see you are trying to run a "batch" file, as you have called it, with cron.  In linux these are normally called shell-scripts, not batch files, but never mind about that at this time.

Can you now show us the content of the script that you are trying to run and whether or not it is executable.  Is that final line in your original post the command used in the script?

---

### Post by caughran on 2016-03-04
Here is the shell script, with some debug snats inserted.

```

#!/bin/sh

# daily comics display. runs 7:05
# /opt/google/chrome//opt/google/chrome/google-chrome

	today=$(date)" comics batch"
	echo $today >> /home/jim/cronme/cronme.log
# 	%u day of week (1..7); 1 is Monday
	DayofWeek=$(date +%u)
# echo $DayofWeek >> /home/jim/cronme/cronme.log

	sleep 2
	if 	! [ $DayofWeek = 7 ]  ; then  
		/opt/google/chrome/google-chrome http://www.uclick.com/client/sea/nq/
		ReturnStatus=$?
#		if	[ $ReturnStatus -ne 0 ] ;  then
			echo "chrome nq return status "$ReturnStatus >> /home/jim/cronme/cronme.log
#		fi
		sleep 5
	fi

#	echo "DoonesBury" >> /home/jim/cronme/cronme.log
		/opt/google/chrome/google-chrome http://www.uclick.com/client/sea/db/
		ReturnStatus=$?
#		if	@ReturnStatus <> 0 ;  then
			echo "chrome db return status "$ReturnStatus >> /home/jim/cronme/cronme.log
#		fi

# tom dancing bug on Thursday, Friday
	if  [ "$DayofWeek" = "4" ] ||  [ "$DayofWeek" = "5" ]  ; then
		sleep 5
		/opt/google/chrome/google-chrome http://wpcomics.washingtonpost.com/client/wpc/td/
		echo "chrome td return status "$? >> /home/jim/cronme/cronme.log
	fi
	exit
```

and here is a selection from the log file it generates:

```
Thu Mar 3 07:05:01 EST 2016 comics batch
chrome nq return status 1
chrome db return status 1
chrome td return status 1
Thu Mar 3 15:10:01 EST 2016 comics batch
chrome nq return status 0
chrome db return status 0
chrome td return status 0
Fri Mar 4 07:05:01 EST 2016 comics batch
chrome nq return status 1
chrome db return status 1
chrome td return status 1
```

The 7:05 runs wih return status 1 are the cron-initiated runs; the Thursday 15:10 run was manually initiated.

---

### Post by jim_deadlock on 2016-03-05
Your problem is that Google Chrome relies on a user profile in order to start, which is fine when you're running the script in a user session. However, a cron session has no such profile so you can't run Chrome. You can use 'perl LWP::Simple' instead.

For debugging scripts run under cron you can log the cron output/errors like this:

```
5 07 * * * /home/jim/cronme/comics >> /home/jim/cronme/cronoutput.log 2>&1
```

---

### Post by caughran on 2016-03-07
> **jim_deadlock said:**
> Your problem is that Google Chrome relies on a user profile in order to start, which is fine when you're running the script in a user session. However, a cron session has no such profile so you can't run Chrome. You can use 'perl LWP::Simple' instead.

That makes sense, and is frustrating. 

Yeah, I could learn perl. I've used 20+ computer languages, going back to IBM704 assembly. But I'm tired of creating stuff for computers; I retired for a reason. I'd just like to find something that works without me working too hard at it. (I stretch my mind in other ways these days.)

Is there an easy way to use LWP?

---

### Post by jim_deadlock on 2016-03-07
elinks and lynx are both CLI browsers that should work in your script.

---

### Post by caughran on 2016-03-07
It's not clear to me how a text-only browser is useful in looking at comic strips.

---

