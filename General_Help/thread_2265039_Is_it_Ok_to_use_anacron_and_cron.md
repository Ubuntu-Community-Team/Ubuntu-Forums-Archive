---
title: "Is it Ok to use anacron and cron"
date: 2015-02-12
forum: General Help
---

### Post by alex330 on 2015-02-12
Hey,

Question: is it OK to have installed anacron and cron on the same machine?

After reading the doc, I'm still not quite sure to understand anacron.

Especially when I'm looking at the following files:

[LIST]
[*]**crontab** file: 
[/LIST]
> SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user    command
17 *    * * *    root    cd / && run-parts --report /etc/cron.hourly
25 6    * * *    root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6    * * 7    root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6    1 * *    root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
#

[LIST]
[*]**anacrontab** file: 
[/LIST]
> # These replace cron's entries
1    5    cron.daily     nice run-parts --report /etc/cron.daily
7    10    cron.weekly     nice run-parts --report /etc/cron.weekly
@monthly    15    cron.monthly nice run-parts --report /etc/cron.monthly


Based on **crontab** file, I can see that the files in **/etc/cron.daily/** will be executed everyday at 6:26am.
Based on **anacrontab**, will the same files (in **/etc/cron.daily**) be also executed at 1am?

Does Anacron, at 1am, can see that the last time the files in /etc/cron.daily were executed less than 24hours ago, so it will not run them?

---

### Post by TheFu on 2015-02-12
Yes, they can both be installed.

And there are crontabs managed by individual users under /var/spool/cron/

---

### Post by raptir on 2015-02-12
In anacrontab, the first field is the *period*, not the time it runs. The second value is the delay. So the line...

```
1 5 cron.daily nice run-parts --report /etc/cron.daily
```

Means *every one day, five minutes after boot, refer to this task as "cron.daily", and execute "nice run-parts --report /etc/cron.daily"*.

Now, as to whether they overlap, take a look at the line in the crontab.

```
25 6 * * * root **test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )**
```

The bolded part is the key. This line in the crontab means that at 6:25am of every day, *check if /usr/sbin/anacron is executable, and if **not**, perform cd / && run-parts --report /etc/cron.daily*. So if you have anacron installed, cron will only execute the hourly jobs.

---

### Post by kjohri on 2015-02-17
Yes, cron and anacron work well together. Please look at the following links,

[http://www.softprayog.in/tutorials/cron]("http://www.softprayog.in/tutorials/cron")
[http://www.softprayog.in/tutorials/anacron]("http://www.softprayog.in/tutorials/anacron")

---

### Post by alex330 on 2015-02-22
Thank you for your replies.

Is this correct:

Let's say I start my computer at 5:00am.

On a computer with anacron:
At 5:05am -> files in /etc/cron.daily are executed
At 6:25am -> test if anacron is executable, it's TRUE, so do nothing

On a computer without anacron:
At 5:05am -> nothing special
At 6:25am -> test if anacron is executable, it's FALSE, so run the scripts in /etc/cron.daily/

---

### Post by kjohri on 2015-02-23
It depends on the contents of /etc/crontab. Mostly, /etc/crobtab has the entries,

25 6	* * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6	* * 7	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6	1 * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )

So if, anacron is not installed, the scripts in /etc/cron.daily are executed.

---

