---
title: "Why does my Apache and MySQL run even if I don't log-in?"
date: 2018-09-27
forum: General Help
---

### Post by webmiester on 2018-09-27
Hi,

Someone setup my ubuntu server.  After a power failure, I turn it back on and the apache and MySQL starts operating even if I haven't logged in with any users.  Why is this?

I want to run Cron in the same way even if I don't log-in.  Will Cron always start on bootup even if I don't log-in any users?

Thanks so much.

---

### Post by TheFu on 2018-09-28
> **webmiester said:**
> Hi,

Someone setup my ubuntu server.  After a power failure, I turn it back on and the apache and MySQL starts operating even if I haven't logged in with any users.  Why is this?

Because that is how real servers work.  System daemons startup automatically, since remote people want access to those things regardless of whether anyone has actually bothered to login.

You can disable the automatic startup for any process, if you like. How depends on the release.

In the old days, there was a script that let us control what ran and what didn't through a central command.  Before that we'd have settings in the initialization files for each service.  Later we got upstart and it had methods to control this stuff with backwards compatible stuff.  Then **systemd** was put in to replace all the prior init systems.  If you want to control it, there are lots of guides.  I've avoided it for years as it matured.  My personal opinion is that it needs another 5 yrs before it is ready for production use, but the people who decide what goes into a distro decided differently.  They have different needs than me, clearly.

Same opinion for netplan, BTW.  They got the 20% that most people use working and shovelled it into 17.10 and later releases well before it was complete or ready. It is the primary reason I won't touch 18.04 yet.  When I don't have any other choice, I can remove netplan and use the old ifupdown tools, so it isn't THAT bad. Unfortunately, there's no removing systemd from Ubuntu. It is too tightly integrated for that.

Cron does start automatically, unless someone disabled that which would be a huge mistake. cron takes care of things that you don't know. You want/NEED those things handled.

---

### Post by The Cog on 2018-09-28
Like all other services, cron is started automatically when the server boots. I guess this is what you want, so do not need to do anything special - it just happens.

---

### Post by SeijiSensei on 2018-09-28
When you install a server like Apache, mysql, or crond, it automatically registers itself and sets itself up to restart at boot.

That's exactly the behavior you want on a server.

cron and ssh are usually defaults.

---

### Post by bizhat on 2018-09-28
cronjob works even if user is not logged in as long as the program you run can run with out user logged in. 

Apache, MySQL run as service, if you don't want to auto start, run

```

systemctl disable apache2
systemctl disable mysql

```

---

### Post by webmiester on 2018-09-29
> **SeijiSensei said:**
> When you install a server like Apache, mysql, or crond, it automatically registers itself and sets itself up to restart at boot.

That's exactly the behavior you want on a server.

cron and ssh are usually defaults.

Yeah, this is basically my question...  Where are they registered?  I would like to see what programs were registered as automatically self loading.  Just today I found that my team viewer also loads on boot-up even if no one has logged in.  This is a serious security threat in my opinion, so I would like to check on what items registered as self loading even before login.

Also, I want to run some scripts that will load automatically.  I am thinking of using cron for this, but it seems to me that there is another way (as shown by apache and mysql).

Lastly, in cron, I can schedule something to run on specific times of the day right?  How do we command cron to start things on bootup?  The command line I always see is based on time and days (14 0 3 2) and not "on bootup"

---

### Post by TheFu on 2018-09-29
cron has 1 min resolution, assuming the system is on and running.
crontabs do support @reboot as a time specification, so that could be a way to start programs after everything else has started.  

If you need control over the order when things start just after boot, then the systemd start/stop config files are the way since 16.04.   Different tools for different needs.

Whatever the settings, if it is for a system-level thing, the settings are in /etc/ somewhere.  There isn't 1 place that always holds everything because some of the tools used were created in the 1990s, some in the mid-2000s, and others have been migrated to the systemd methods. History impacts current stuff.

---

### Post by The Cog on 2018-09-29
In recent Ubuntu releases, the "service" cnofiguration files that get services started at boot time are in /lib/systemd/system. There are around 300 of them. Others are configured in /etc/systemd/system. See this page: [https://wiki.debian.org/systemd](https://wiki.debian.org/systemd)

Don't be surprised that services start before users get logged in. That is the normal way of services. Your web server and database server are services, just waiting for a user to come along and use them.

Cron is a scheduler for one-off or occasional jobs such as doing backups, and of course it is another service running all the time, launching jobs when the time is right. You should not try to use cron for starting long-running services - systemd is there for that. Windows is much the same - it has many services permanently running, and has a scheduler for running occasional jobs. There is nothing specially different between Windows and Linux (or OSX) in this regard.

In ubuntu, the commands **pstree -a** and **ps auxf** both show a list of running processes and their children.

---

### Post by TheFu on 2018-09-29
> **The Cog said:**
>  
Cron is a scheduler for one-off or occasional jobs such as doing backups, and of course it is another service running all the time, launching jobs when the time is right. You should not try to use cron for starting long-running services - systemd is there for that. Windows is much the same - it has many services permanently running, and has a scheduler for running occasional jobs. There is nothing specially different between Windows and Linux (or OSX) in this regard.


I've always found the Windows Scheduler to be a very heavy process, unlike cron.  Cron is very light, barely uses any system resources.  The Windows Scheduler is so heavy, it rivals Outlook and iTunes in startup speed. No idea why it is so heavy.

---

### Post by webmiester on 2018-09-30
Thank you guys.  I'll look for these files.  Then I'll try to manipulate them as needed and see the results

---

### Post by SeijiSensei on 2018-10-01
```

$ **systemctl list-unit-files | grep enabled**
acpid.path                                                       enabled        
apport-autoreport.path                                           enabled        
cups.path                                                        enabled        
accounts-daemon.service                                          enabled        
anacron.service                                                  enabled        
apache2.service                                                  enabled        
apparmor.service                                                 enabled        
autovt@.service                                                  enabled        
avahi-daemon.service                                             enabled        
bluetooth.service                                                enabled        
[etc.]

```

---

### Post by webmiester on 2018-10-10
> **SeijiSensei said:**
> ```

$ **systemctl list-unit-files | grep enabled**
acpid.path                                                       enabled        
apport-autoreport.path                                           enabled        
cups.path                                                        enabled        
accounts-daemon.service                                          enabled        
anacron.service                                                  enabled        
apache2.service                                                  enabled        
apparmor.service                                                 enabled        
autovt@.service                                                  enabled        
avahi-daemon.service                                             enabled        
bluetooth.service                                                enabled        
[etc.]

```

This is cool.  Thanks!

---

