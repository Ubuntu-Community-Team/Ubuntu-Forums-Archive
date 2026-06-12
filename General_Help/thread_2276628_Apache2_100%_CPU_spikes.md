---
title: "Apache2 100% CPU spikes"
date: 2015-05-04
forum: General Help
---

### Post by rob134 on 2015-05-04
[TABLE="width: 100%"]
[TR]
[TD]Hi,

I have 6 wordpress websites running on my Ubuntu Linode. Now frequently Longview sees Apache2 spiking 100% CPU which causes slow website performance, memory also spikes with it to max 1gb. Every day consistently from around 9:00 to 9:15 and 11:45 to 12:15 my websites are very slow or timeout when trying to connect.

I know there's many treads on this but haven't found a solution just yet.

I have:

[LIST=1]
[*]Checked the log files per domain   ```
ErrorLog  /home/somefolder/public/domain.com/log/error.log
``` and ```
CustomLog /home/somefolder/public/domain.com/log/access.log combined
```
[*]During the 100% CPU I entered "deny from all" in .htaccess per domain without any visual result trying to filter it down to which domain causes it. 
[/LIST]

It's been going on for a week now. Am I looking in the wrong places?

Many thanks,

Regards
Rob
[/TD]
[/TR]
[/TABLE]
[IMG]http://www.seomandarin.com/wp-content/uploads/Linode-Longview-longview91894-1.jpg[/IMG]

---

### Post by dragonfly41 on 2015-05-04
I have no experience of Linode .. but you might get some insights into the root cause of the spikes by

(a) adding some options to logging directives
[http://httpd.apache.org/docs/current/mod/mod_log_config.html#formats](http://httpd.apache.org/docs/current/mod/mod_log_config.html#formats)

(b) installing webmin on your Ubuntu installation to give you a web dashboard to monitor your servers and processes.

Also I'm currently tweaking my own modest apache2 localhost development server and I'm adding mod_status module to try to monitor apache2 status.
Not sure if that would help.

---

### Post by SeijiSensei on 2015-05-04
Since the spikes are periodic, I'd start by looking at requests in /var/log/apache2/access.log.  Do requests spike in these same periods?  Perhaps it's a spidering application from a search engine?

Since it's WordPress, another possibility might be the back-end SQL server.  

You might consider upgrading to 2GB to see if that helps.  I'd make a snapshot backup of the server first if you're not paying for the backup service (if not, I strongly recommend it), then follow the procedure to upgrade to 2 GB.  If that doesn't help, you can revert back to the cheaper plan.

---

### Post by rob134 on 2015-05-05
> **dragonfly41 said:**
> I have no experience of Linode .. but you might get some insights into the root cause of the spikes by

(a) adding some options to logging directives
[http://httpd.apache.org/docs/current/mod/mod_log_config.html#formats](http://httpd.apache.org/docs/current/mod/mod_log_config.html#formats)

(b) installing webmin on your Ubuntu installation to give you a web dashboard to monitor your servers and processes.

Also I'm currently tweaking my own modest apache2 localhost development server and I'm adding mod_status module to try to monitor apache2 status.
Not sure if that would help.

Thanks,

a. The logging doesn't show any option for CPU usage it seems.
b. webmin needs a newer Ubuntu version of 14+ reading the linode documentation.

I have added the mod_status and I ran the monitoring thing but it said I don't have the permissions, even though I ran it as root... 

Cheers

---

### Post by rob134 on 2015-05-05
> **SeijiSensei said:**
> Since the spikes are periodic, I'd start by looking at requests in /var/log/apache2/access.log. Do requests spike in these same periods? Perhaps it's a spidering application from a search engine?

Since it's WordPress, another possibility might be the back-end SQL server. 

You might consider upgrading to 2GB to see if that helps. I'd make a snapshot backup of the server first if you're not paying for the backup service (if not, I strongly recommend it), then follow the procedure to upgrade to 2 GB. If that doesn't help, you can revert back to the cheaper plan.

I've got Wordfence running which monitors the amount of requests to the domains. There's no relation between high cpu/memory and spider/user requests.

What do you mean with back-end SQL server? something that the server itself causes?

I might consider an upgrade to 2GB if I can't find a solution for this. Thanks

---

### Post by SeijiSensei on 2015-05-05
WordPress uses MySQL by default to store all the blog content.

Try disabling WordFence.  I'm wondering if it is eating the CPU if it has to handle traffic bursts.  

I've run Apache for years and never seen this behavior so I'm pretty much out of suggestions.

---

### Post by rob134 on 2015-05-05
> **SeijiSensei said:**
> WordPress uses MySQL by default to store all the blog content.
I asked because I thought there would be some hidden back end that doesn't show up in logs and such :) Guess not!

> **SeijiSensei said:**
> Try disabling WordFence.  I'm wondering if it is eating the CPU if it has to handle traffic bursts. .
Good point, but doesn't seem to be the case. Log files don't show anything out of the ordinary on those time windows. I've tried with and without wordfence and with and without w3 cache plugin.

> **SeijiSensei said:**
> I've run Apache for years and never seen this behavior so I'm pretty much out of suggestions..
Thanks for your help though :) I'm hoping it will go away by itself some day - probably will only get worse over time...

---

### Post by dragonfly41 on 2015-05-05
I'm guessing here .. but since you are deploying WordPress sites could this peak be due to cronjobs?

[https://www.ecenica.com/support/answer/fix-high-cpu-load-wordpress/](https://www.ecenica.com/support/answer/fix-high-cpu-load-wordpress/)

---

