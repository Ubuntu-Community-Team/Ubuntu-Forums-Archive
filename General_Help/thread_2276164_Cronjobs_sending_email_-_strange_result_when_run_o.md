---
title: "Cronjobs sending email - strange result when run on schedule | on-demand is alright"
date: 2015-04-30
forum: General Help
---

### Post by Frank_Barmentlo on 2015-04-30
Hey all,

I am kinda new to Cron jobs. I thought it was a nice way to automate a few things,
Using Webmin, I created 2 cronjobs to automate tripwire & chkrootkit checks. I wanted to add more but I am running into issues that I don't understand.

The commands I am running are:
@daily chkrootkit | mail -s "ChkRootkit report for `uname -n`" [email]myemail@domain.com[/email] #somecomment
@daily tripwire --check | mail -s "Tripwirereport for `uname -n`" [email]myemail@domain.com[/email]  #some comment

Right now I've set them both to run daily at 00:00 AM, every day(testing purposes).

When I hit "Run now", I receive an email, with the expected report/result/output,

When I wait for it to run as scheduled, I receive an email, without any text in the body.
The subject is alright, but the body is empty.

Can anyone help me out here?

The OS is Ubuntu Server 14.04.2,
Tools used are both CLI/Terminal and Webmin.
Kind regards,
Frank

---

### Post by TheFu on 2015-05-01
cron doesn't get much environment, so things that your login sets up doesn't exist under cron. You have to set everything you expect in the environment, if you want it. For example, the PATH, LD_LIBRARY_PATH are minimal under cron.

[https://stackoverflow.com/questions/2135478/how-to-simulate-the-environment-cron-executes-a-script-with](https://stackoverflow.com/questions/2135478/how-to-simulate-the-environment-cron-executes-a-script-with) explains how to see the environment cron provides.

Hence, there are some best practices for shell scripting.
* Always specify the complete, full, path to all programs you want run.
* Never parse the output from ls, avoid using simple grep and cat - cat is almost never needed.
* For cron entries, create a shell script to put any multi-command commands into 1 file for cron to call.
* noclobber
* [http://www.davidpashley.com/articles/writing-robust-shell-scripts/](http://www.davidpashley.com/articles/writing-robust-shell-scripts/)

Create ~/bin/rootkit-chk ; chmod +x ~/bin/rootkit-chk and put something like this inside:
```
/usr/bin/chkrootkit | /usr/bin/mail -s "ChkRootkit report for `/bin/hostname`" myemail\@domain.com #somecomment
```
inside it.  I guessed at the paths - verify for your system. Also - used hostname. Might be good to set env vars for each command (I usually use all CAPS) and might verify that the commands exist too.

For me, if any bash/sh script gets over 2 pgs long, I'll re-write it in Perl for easier maintenance. Python would be a good choice to, but I don't "python." Both are pre-installed on Ubuntu systems while ruby may not be.

---

### Post by Frank_Barmentlo on 2015-05-01
Thanks for your reply,
I will test this tonight.
1 last question though,
The new cronjob is something like 
@daily tripwire.sh

then the tripwire.sh has the command like you gave above?
"tripwire --check | mail -s "Tripwirereport for `/bin/hostname`" [EMAIL="myemail@domain.com"]myemail@domain.com[/EMAIL]  #some comment"

On your last note: I am a home-user, and hope not to use bash/sh scripts of those lengths.. given examples are the longest I planned to use :P

Kind regards,
Frank

---

### Post by nerdtron on 2015-05-01
@daily tripwire.sh   ---> might as well specify the shell you want this to run, such as: @daily /bin/bash tripwire.sh

Also on your script, as suggested already, better to use full path on for the commands like TheFu said.

---

### Post by TheFu on 2015-05-01
> **Frank_Barmentlo said:**
> 
The new cronjob is something like 
@daily tripwire.sh

then the tripwire.sh has the command like you gave above?
"tripwire --check | mail -s "Tripwirereport for `/bin/hostname`" [EMAIL="myemail@domain.com"]myemail@domain.com[/EMAIL]  #some comment"

You need something like

```
@daily /home/userid-whatever-it-is/bin/tripwire.sh
```
You cannot assume the PATH.  Also, I've never used the @daily crontab - always use a crontab for a specific user - which have different parameters.  I say this so you know I don't know if hte exact line is correct or not ... just that the full path to the script MUST be specified. Also - I think the email address needs the '\@' escaped, but I'm not positive. This is common for certain characters like that.

Also - you need to specify the full path to teh tripwire program. If you don't understand, please ask. We were all new to this at some point. Things will "click" over time and your understanding will grow exponentially as the pieces fit.

Extensions, like .sh, don't mean anything to Linux. They are not required or used by the OS at all. They are handy for humans, but don't trust them completely.

---

### Post by Frank_Barmentlo on 2015-05-01
Hey TheFu,
Thanks for your time helping me out,

About the extensions: I am an IT-guy who grew up with windows, where extensions do matter. It's just for myself that I add extensions, so I know what kind of file I am looking at. Just a bad habbit that's stuck ;-)

Is there any reason the full path has to be used, and is there an easy way to find the full path of binaries?
It probably is /usr/bin or /usr/sbin, but to be sure?

Kind regards,
Frank

---

### Post by Harpz on 2015-05-01
If you just need to know where the executable is you can run whereis or which.

```

whereis firefox
firefox: /usr/bin/firefox /etc/firefox /usr/lib/firefox /usr/share/man/man1/firefox.1.gz

```
```

which firefox
/usr/bin/firefox

```

---

### Post by nerdtron on 2015-05-01
> **Frank_Barmentlo said:**
> 

Is there any reason the full path has to be used,



Because a user running a command will search the default directories on the $PATH variable. This $PATH variable is different from user, root and cron. So it's important  to provide the full path of the commands. 

So, if your tripwire.sh script is saved in your home folder, cron won't even search that folder. Therefore, when cron run the command "@daily tripwire.sh" it won't be able to find the script.

---

### Post by TheFu on 2015-05-01
> **nerdtron said:**
> So, if your tripwire.sh script is saved in your home folder, cron won't even search that folder. Therefore, when cron run the command "@daily tripwire.sh" it won't be able to find the script.

Actually - I'd be surprised if "$HOME" was set correctly under a cron job too. Don't assume anything. **Always** use full paths for programs, input files, output files and redirection in shell scripts. This applies even more so for cron.  Learning it today will save you hours of problems in the future - I speak from experience as a formerly lazy scripter.

Generally, PATH works the same on Linux as it does on Windows. Just Linux will only know about files marked with execute permissions that the current userid can actually run, whereas on Windows PATH knows about cmd, com, exe, dll, and a few other less-popular extensions.

Seems you may have a slight gaps in your Linux knowledge.  At that stage, finding answers by google isn't helpful. It is like jumping into the ocean when you've just learned how to doggie paddle in the shallow end.
[http://blog.jdpfu.com/2014/12/28/learning-linux](http://blog.jdpfu.com/2014/12/28/learning-linux) provides my best answer to fill in those blanks in an ordered way.  There's a great, free, no-hassle, PDF book link there to learn Linux and the command line. It isn't just *what to type*, rather, it is *why* to do something a certain way.  3 hrs of reading will prevent hours, days, weeks of frustration.

---

### Post by CharlesA on 2015-05-01
+1 to TheFu. I always try to use full paths in my shell scripts whether they will be run via cron or not.

Have a read on the link in TheFu's last post as well. That should help.

As an aside... I rarely  use @daily or @weekly when setting up cronjobs. I use the normal syntax.
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

---

### Post by SeijiSensei on 2015-05-01
> **CharlesA said:**
> As an aside... I rarely  use @daily or @weekly when setting up cronjobs. I use the normal syntax.
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)
I usually just create symlinks from scripts I want to run periodically to the corresponding /etc/cron.* directories like /etc/cron.daily.  That avoids editing crontabs directly.

---

### Post by CharlesA on 2015-05-02
> **SeijiSensei said:**
> I usually just create symlinks from scripts I want to run periodically to the corresponding /etc/cron.* directories like /etc/cron.daily.  That avoids editing crontabs directly.

Does that set them to run at a specific time or whenever cron.daily/weekly/monthly runs? Stupid question, I know. :p

---

### Post by SeijiSensei on 2015-05-02
> **CharlesA said:**
> Does that set them to run at a specific time or whenever cron.daily/weekly/monthly runs? Stupid question, I know. :p

They run at the times set in /etc/crontab.  The default looks like this:
```

# m h dom mon dow user  command
17 *    * * *   root    cd / && run-parts --report /etc/cron.hourly
25 4    * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 4    * * 7   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 4    1 * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )

```
Any changes here will affect all the scripts run out of the corresponding directory, of course.  On my servers with UTC clocks, I push up the times by 4-5 hours so the scripts run overnight here in GMT-5.

---

### Post by CharlesA on 2015-05-02
Thanks! That's pretty neat.

---

### Post by Frank_Barmentlo on 2015-05-06
okay, it took a bit longer then expected,
I created /scripts/chkrootkit and added:
/usr/bin/chkrootkit | /usr/bin/mail -s "ChkRootkit report for `uname -n`me@mydomain.com

The cronjob is set as:
35 * * * * /scripts/chkrootkit.sh   #Rootkit check & Mail results
and it's 23:33 right now.. so 2 more minutes before it should run. I tested manual trigger, and that worked as before.

edit: just read the second page.. I came to resolve an issue, not to learn :P I will read trough the stuff later
Thanks for the help, all!

ChkRootkit script works.. tripwire needs a better look as there's something wrong in the config of tripwire itself, not the cronjob.

Well, thanks again!
Kind regards,
Frank

---

